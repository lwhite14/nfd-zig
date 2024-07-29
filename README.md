# nfd-zig

`nfd-zig` is a Zig binding to the library [nativefiledialog](https://github.com/mlabbe/nativefiledialog) which provides a convenient cross-platform interface to opening file dialogs on Linux, macOS and Windows.

This library has been tested on Windows 10/11, macOS 11.1 and Linux.

## Usage

You can run a demo with `zig build run`. The demo's source is in `src/demo.zig`.

If you want to add the library to your own project...

- Add the `nfd` package to your `build.zig.zon` file
  ```zig
  .dependencies = .{
      .nfd = .{
          .url = "https://github.com/fabioarnold/nfd-zig/archive/d85279e0acac16daf12ad26fce45aba7d13276b1.tar.gz",
          .hash = "12201c12379ee12e5b921f015a041dcd65428717d0d4b97bfbf40153897f3f8d4dc1",
          // If you want to use the most current version of the master branch, use the url below.
          // Delete the '.hash = "...",'. Run 'zig build'. It will fail, providing you with the uptodate hash.
          // .url = "https://github.com/fabioarnold/nfd-zig/archive/master.tar.gz",
      },
  },
  ```
- Add the `nfd` package to your executable in your `build.zig`
  ```zig
  const nfd_dep = b.dependency("nfd", .{ .target = target, .optimize = optimize });
  exe.root_module.addImport("nfd", nfd_dep.module("nfd"));
  ```
- Import the library
  ```zig
  const nfd = @import("nfd");
  ```

## Screenshot

![Open dialog on Windows 10](https://raw.githubusercontent.com/mlabbe/nativefiledialog/67345b80ebb429ecc2aeda94c478b3bcc5f7888e/screens/open_win.png)
