# Sweet Home 3D Snap

This repository packages [Sweet Home 3D](https://www.sweethome3d.com/)
as a Snap. It is a packaging project, separate from the upstream
Sweet Home 3D source code: the Snap uses an official upstream standard
distribution and adds the launcher and desktop integration. It does not
develop or maintain the interior design application itself.

## For users

The Snap runs the application on the OpenJDK JRE staged into the Snap; the
Java runtime bundled in the upstream tarball is removed at build time.

For installation and general Sweet Home 3D usage, see the
[upstream project site](https://www.sweethome3d.com/).

## Reporting issues

Please report an issue to the project responsible for it:

- **Snap packaging or installation** (for example, the Snap does not launch,
  or has a packaging/desktop integration problem):
  [open an issue in this repository](https://github.com/jibel/sweethome3d-snap/issues).
- **Sweet Home 3D application behavior** (for example, plan drawing, 3D view,
  or application feature bugs):
  [report it to upstream](http://www.sweethome3d.com/support.jsp).
  The [upstream website](https://www.sweethome3d.com/) has additional
  project information and support links.

When reporting a Snap issue, include your Ubuntu version, Snap version, and
the steps or command that reproduce the problem. For an upstream issue, include
the Sweet Home 3D version.

## Build the Snap

Requirements: Snapcraft 9 and a working `snapcraft` installation. The build
uses Snapcraft's managed build environment for the `core26` base.

1. Download a Sweet Home 3D **tarball** from the
   [upstream downloads](https://sourceforge.net/projects/sweethome3d/files/SweetHome3D/).
2. Place the original, versioned archive in `download/`, for example
   `SweetHome3D-7.5-linux-x64.tgz`. Archive files there are ignored by Git.
3. From the repository root, run:

   ```sh
   snapcraft pack
   ```

The generated `.snap` can be installed locally for a trial with
`sudo snap install --dangerous ./<generated-snap-file>.snap`.

If multiple tarballs are present, the build selects the highest version. It
sets the Snap version from the selected archive name.

## Known Issues

Printing from a java app is not working and printing is disabled.
