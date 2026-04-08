# XMP on Zig

This repository wraps the upstream Extended Module Player library source code with Zig's build system.

Zig 0.15.2 is required.

## Installing as a `build.zig.zon` package

Run in your Zig project:
```sh
zig fetch --save-exact=xmp git+https://github.com/lateleite/xmp-on-zig.git
```

Then in your `build.zig` file:
```zig
pub fn build(b: *std.Build) !void {
    // ...

    // Add a reference to the package you've just fetched...
    const dep_xmp = b.dependency("xmp", .{
        .target = target,
        .optimize = optimize,
    });
    const lib_xmp = dep_xmp.artifact("xmp");

    // ...then link the library to your module
    your_module.linkLibrary(lib_xmp);

    // ...
}
```

After that, you may use XMP's header files in your module.

## License

All (build) code here is released to public domain or under the BSD Zero Clause license, choose whichever you prefer.

You may find XMP's license at [https://github.com/libxmp/libxmp/blob/301a9c0ae9dcdde7dd5ec336ad497e228fb52568/README](https://github.com/libxmp/libxmp/blob/301a9c0ae9dcdde7dd5ec336ad497e228fb52568/README).
