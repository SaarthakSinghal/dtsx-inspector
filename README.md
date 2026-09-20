# DTSX Inspector

A local, browser-based inspector for Microsoft SSIS `.dtsx` packages. It extracts package configuration, task bindings, Script Task source, and Execute SQL statements without uploading package data.

## Capabilities

- Inspect package parameters and scoped variables.
- Edit package parameter values and save or download an updated DTSX file.
- Review Script Task read/write variable bindings.
- View and copy `ScriptMain.cs`, `.vb`, or `.fs` source stored in `ProjectItem` nodes.
- View and copy Execute SQL Task queries and configuration.
- Search parameters, variables, bindings, task configuration, and code.
- Export inspection results as JSON.

## Use

1. Open `index.html` in a current Chrome or Edge browser.
2. Select **Load file**, drop a `.dtsx` or `.xml` file, or paste package XML.
3. Select **Parse** when pasting XML. Loaded files are parsed automatically.
4. Expand a section or use **Expand all**.
5. For tasks, switch between **Config** and **Code**.

## Edit package parameters

1. After parsing, select **Edit parameters** beside **Copy visible**.
2. Update the required values.
3. Select **Done editing** to return to the read-only view.
4. Select **Save DTSX** when direct file access is available, or **Download DTSX** to create an edited copy.

Save pending Script Task work in Visual Studio before replacing or externally modifying the package file. Visual Studio may ask you to reload the changed DTSX.

## Script source mapping

The inspector prioritizes `ScriptMain.cs`, `ScriptMain.vb`, and `ScriptMain.fs` within each `ScriptProject`. Source is mapped to its enclosing Script Task. Alphabetical mapping is used only when structural ownership is unavailable.

If a package contains only a compiled `BinaryItem`, plain source code is not available in the DTSX XML and cannot be displayed.

## Security

- Processing stays in the browser.
- No uploads, analytics, cookies, or browser storage.
- No external scripts, fonts, or network requests.
- DTD and entity declarations are rejected.
- Input size, XML depth, and element count are limited.
