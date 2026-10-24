# Sweet Home 3D Snap

This repository packages [Sweet Home 3D](https://www.sweethome3d.com/)
as a Snap. It is a packaging project, separate from the upstream
Sweet Home 3D source code: the Snap uses an official upstream standard
distribution and adds the launcher and desktop integration. It does not
develop or maintain the interior design application itself.

## For users

The Snap runs the application on a jlink-trimmed OpenJDK 25 runtime built
into the Snap; the Java runtime bundled in the upstream tarball is removed
at build time.

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

## Optional content snap: extra furniture and texture libraries

The `content-snap/` directory builds `sweethome3d-content`, a companion snap
that ships three official furniture libraries (3DModels-Contributions,
3DModels-BlendSwap-CC-0, 3DModels-BlendSwap-CC-BY, all version 1.9.3) and two
official texture libraries (Textures-Contributions, Textures-eTeksScopia,
version 1.3.1). Build and install it from that directory:

```sh
cd content-snap
snapcraft pack
sudo snap install --dangerous ./sweethome3d-content_<version>_amd64.snap
```

The library files are committed to this repository, so no download is needed.
When both snaps are installed the libraries appear automatically in Sweet
Home 3D's furniture and texture catalogs; without the content snap the
application behaves exactly as before.

## Licensing and attribution

The libraries carry mixed licenses and each library's full license text is
included in `content-snap/licenses/`:

- 3DModels-Contributions: Free Art License 1.3
- 3DModels-BlendSwap-CC-0: CC0 / Public Domain
- 3DModels-BlendSwap-CC-BY: Creative Commons Attribution 3.0
- Textures-Contributions: Creative Commons Attribution 4.0 International
- Textures-eTeksScopia: Creative Commons Attribution 4.0 International

Per-model attribution is also embedded inside each SH3F/SH3T file and is
shown by Sweet Home 3D in the catalogs. To satisfy the CC-BY attribution
requirement, keep the license files intact when redistributing; the
`sweethome3d-content.info` command prints the license summary. The Free Art
License has no SPDX identifier, so the content snap's `license` field lists
only the SPDX-identifiable licenses (GPL-2.0, CC-BY-3.0, CC-BY-4.0); the
FAL text is provided verbatim in `licenses/`.

## Known Issues

Printing from a java app is not working and printing is disabled.
