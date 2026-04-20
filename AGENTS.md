# Systemless Build.Prop Module - AI Agent Guidelines

## Project Overview
This is a Magisk module that enables systemless editing of Android `build.prop` files. The module copies `/system/build.prop` (and optionally `/system/vendor/build.prop`) to the module's overlay directory, allowing modifications without altering actual system files.

## Architecture
- **Module Structure**: Standard Magisk module with `META-INF/` for installation scripts and `system/` for overlay files
- **Core Logic**: `customize.sh` handles installation by copying system build.prop files and setting permissions
- **Version Management**: `module.prop` contains metadata, `update.json` enables Magisk Manager updates

## Key Files & Patterns
- **`customize.sh`**: Installation script using shell commands; uses fallback methods (cp/cat/dd) for file operations; removes unwanted files from `$MODPATH`
- **`module.prop`**: Simple key=value format for module metadata (id, name, version, author, description, updateJson)
- **`update.json`**: JSON with version info, download URL, and changelog link for Magisk updates
- **`system/` directory**: Overlay structure mirroring Android system paths for build.prop files

## Development Workflows
- **Building**: Create ZIP archive of module files for distribution/installation
- **Version Updates**: Increment `versionCode` in `module.prop` and `update.json`; update `zipUrl` and `changelog` in `update.json`
- **Testing**: Install via Magisk Manager on device; verify build.prop copies exist in module path with 777 permissions
- **Debugging**: Check Magisk logs for installation errors; validate file operations in `customize.sh`

## Conventions
- Use `ui_print` for user feedback in `customize.sh`
- Handle file operation failures gracefully with multiple methods (cp || cat || dd)
- Set 777 permissions on build.prop files for universal editability
- Include vendor build.prop support only if `/system/vendor/build.prop` exists
- Clean up unwanted files (README.md, LICENSE, etc.) during installation

## Integration Points
- **Magisk Framework**: Relies on `$MODPATH` variable and Magisk's overlay system
- **Android System**: Reads from `/system/build.prop` and `/system/vendor/build.prop`
- **External Tools**: Compatible with any build.prop editor that can modify files in module overlay

## Common Tasks
- **Add New Features**: Modify `customize.sh` logic, update version in `module.prop` and `update.json`
- **Fix Bugs**: Test file operations thoroughly; ensure fallback methods work on various Android versions
- **Update Releases**: Create GitHub release with ZIP, update `update.json` URLs and version numbers</content>
<parameter name="filePath">C:\Users\USER\Documents\GitHub\Systemless-build.prop\AGENTS.md
