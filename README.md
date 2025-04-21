# IDA PRO MCP

- This repo is the fork of https://github.com/mrexodia/ida-pro-mcp with modify for allow remote ida-plugin and sse MCP server

# Usage

- Copy the `mcp-plugin.py` to `plugins` folder of IDA PRO

- Manual start plugin in IDA

- Connect use Cline MCP server or Claude (Ex Cline: [cline_mcp_settings.json](cline_mcp_settings.json))

- If you host the MCP server in the same host with Cline/Claude, you should use `stdio` mode, replace `url` and `transportType` with

```json
"args": [
    "python",
    "server.py",
    "--ida-host",
    "127.0.0.1",
    "--ida-port",
    "13337"
]
```

- If you host MCP server in another machine, you should use `sse` mode, run the server and point the url to `http://<server-ip>/sse`

```bash
python server.py --transport sse --host 127.0.0.1 --port 9999
# python server.py --transport sse --host 127.0.0.1 --port 9999 --ida-host 192.168.48.138 --ida-port 13337
```

# Currently supported function

- `check_connection`: Check if the IDA plugin is running.
- `get_metadata()`: Get metadata about the current IDB.
- `get_function_by_name(name)`: Get a function by its name.
- `get_function_by_address(address)`: Get a function by its address.
- `get_current_address()`: Get the address currently selected by the user.
- `get_current_function()`: Get the function currently selected by the user.
- `convert_number(text, size)`: Convert a number (decimal, hexadecimal) to different representations.
- `list_functions(offset, count)`: List all functions in the database (paginated).
- `list_globals(filter, offset, count)`: List all globals in the database (paginated).
- `list_strings(filter, offset, count)`: List all strings in the database (paginated).
- `decompile_function(address)`: Decompile a function at the given address.
- `disassemble_function(start_address)`: Get assembly code (address: instruction; comment) for a function.
- `get_xrefs_to(address)`: Get all cross references to the given address.
- `get_entry_points()`: Get all entry points in the database.
- `set_comment(address, comment)`: Set a comment for a given address in the function disassembly and pseudocode.
- `rename_local_variable(function_address, old_name, new_name)`: Rename a local variable in a function.
- `rename_global_variable(old_name, new_name)`: Rename a global variable.
- `set_global_variable_type(variable_name, new_type)`: Set a global variable's type.
- `rename_function(function_address, new_name)`: Rename a function.
- `set_function_prototype(function_address, prototype)`: Set a function's prototype.
- `declare_c_type(c_declaration)`: Create or update a local type from a C declaration.
- `set_local_variable_type(function_address, variable_name, new_type)`: Set a local variable's type.
- `dbg_get_registers()`: Get all registers and their values. This function is only available when debugging.
- `dbg_get_call_stack()`: Get the current call stack.
- `dbg_list_breakpoints()`: List all breakpoints in the program.
- `dbg_start_process()`: Start the debugger.
- `dbg_exit_process()`: Exit the debugger.
- `dbg_continue_process()`: Continue the debugger.
- `dbg_run_to(address)`: Run the debugger to the specified address.
- `dbg_set_breakpoint(address)`: Set a breakpoint at the specified address.
- `dbg_delete_breakpoint(address)`: del a breakpoint at the specified address.
- `dbg_enable_breakpoint(address, enable)`: Enable or disable a breakpoint at the specified address.
