# MCP Tool Map

The **freecad-mcp** server (uvx package `freecad-mcp`) exposes **17 tools**. Names below are the tool
surface; verify against the local build with the MCP `list_tools` call before relying on a name.

| Tool | Purpose |
| --- | --- |
| `create_document` | Create a new FreeCAD document |
| `list_documents` | List open documents |
| `reload_document` | Close and reopen a saved document to pick up external changes |
| `create_object` | Create an object in a document |
| `edit_object` | Edit an object's properties |
| `delete_object` | Delete an object |
| `get_objects` | Get all objects in a document |
| `get_object` | Get one object |
| `get_view` | Screenshot of the active view |
| `execute_code` | Run Python on FreeCAD's GUI thread |
| `execute_code_async` | Start a background job, returns a job ID |
| `get_async_status` | Background job state and failure tracebacks |
| `execute_code_headless` | Run a script in a separate `freecadcmd` process |
| `get_rpc_status` | RPC + GUI-dispatch health, addon version |
| `insert_part_from_library` | Insert a part from the FreeCAD parts library |
| `get_parts_list` | List parts in the FreeCAD parts library |
| `run_fem_analysis` | Run CalculiX on an existing analysis |

## Argument names that matter

### `create_object` uses `obj_properties`, NOT `properties`

```json
{
  "doc_name": "ProjectName",
  "obj_type": "Part::Box",
  "obj_name": "Base Frame",
  "obj_properties": {"Length": 1219.0, "Width": 89.0, "Height": 38.0},
  "include_screenshot": false
}
```

⚠️ **The silent-failure trap:** passing `properties` instead of `obj_properties` is **accepted and
ignored**. The object is created with FreeCAD's defaults, the call reports success, and the geometry is
wrong. A default `Part::Box` is **10x10x10 mm, volume 1000 mm³**.

**Always verify any create/edit by reading a computed value back** — volume, a bounding box, or a
dimension — rather than trusting the success message. A useful check: for a rectangular part,
`Length x Width x Height` in mm should equal `Shape.Volume`.

### `create_object` other arguments

| Argument | Meaning |
| --- | --- |
| `doc_name` | Target document |
| `obj_type` | FreeCAD type string, e.g. `Part::Box`, `Part::Cylinder`, `Part::Fuse` |
| `obj_name` | Requested name — FreeCAD may de-duplicate it (`Box` -> `Box001`) |
| `analysis_name` | Only for `Fem::FemMeshGmsh`; names the `Fem::AnalysisPython` container |
| `obj_properties` | Property map — **see trap above** |
| `include_screenshot` | Set `false` to skip the return screenshot |
| `view_name` | View for the returned screenshot |

### `execute_code` for anything the structured tools cannot do

`execute_code` runs arbitrary Python on FreeCAD's GUI thread and is the escape hatch for real modelling
work — boolean operations, fillets, arrays, exports, and reading values back. Always print a value you can
assert on:

```python
import FreeCAD as App
o = App.getDocument("ProjectName").getObject("Base Frame")
print("VOL=" + str(round(o.Shape.Volume, 2)))
print("LWH=" + str([round(o.Length,1), round(o.Width,1), round(o.Height,1)]))
```

Notes:
- `Shape.BoundBox` is **not iterable**. Read `.XMin/.YMin/.ZMin/.XMax/.YMax/.ZMax` individually.
- The GUI thread runs this, so a long computation blocks the UI. Use `execute_code_async` for anything slow
  and poll with `get_async_status`.
- Exports: `Mesh.export([obj], "out.stl")` for STL, `Part.export([obj], "out.step")` for STEP.

## Runtime preconditions

- **FreeCAD must be running with the addon's RPC server started** for every tool except
  `execute_code_headless`. Check with `get_rpc_status` before a modelling run; a healthy answer reports
  `rpc_server: running` and `gui_dispatch: healthy`.
- Default RPC endpoint is `localhost:9875`, loopback-only.
- `execute_code_headless` shells out to a separate `freecadcmd` process and works **without** the GUI.
  It is the right tool for batch work — but a document it saves must be opened in the GUI, or
  `reload_document` called if that document is already open.

## Known bridge pitfalls

1. **Silent `obj_properties` failure** — described above. Verify values after every write.
2. **Windows `--freecadcmd` path** — the server splits this value with shell-style quoting, so an
   unquoted Windows path loses its backslashes and the headless tool fails with
   `[WinError 2] The system cannot find the file specified`. **Pre-quote the path** so it survives:
   `'"C:\Program Files\FreeCAD 1.1\bin\freecadcmd.exe"'`.
3. **Imperial/millimetre drift** — FreeCAD is millimetres; the design spec is inches. Convert everywhere
   and record the conversion table.
