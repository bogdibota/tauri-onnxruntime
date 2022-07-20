## How this repo was created

1. `yarn create tauri-app`
2. add `onnxruntime = "0.0.14"` as dependency
3. use `onnxruntime` in `main.rs`

*Note: doing the same in a new rust project (w/o tauri) works as intended.*

## How to reproduce the issue

1. clone the repo
2. start the app: `yarn && yarn tauri dev` or `cargo tauri dev`


**Expected**: app builds & starts

**Actual**: app fails to build / start

*Note: error messages are from the second run/build*

### `dev` error message
```
dvk@pop-os:~/tmp/tauri-onnxruntime$ cargo tauri dev
        Info Watching /home/dvk/tmp/tauri-onnxruntime/src-tauri for changes...
   Compiling app v0.1.0 (/home/dvk/tmp/tauri-onnxruntime/src-tauri)
    Finished dev [unoptimized + debuginfo] target(s) in 22.06s
/home/dvk/tmp/tauri-onnxruntime/src-tauri/target/debug/tauri-onnxruntime: error while loading shared libraries: libonnxruntime.so.1.8.1: cannot open shared object file: No such file or directory
```

### `build -verbose` error message
```
dvk@pop-os:~/tmp/tauri-onnxruntime$ cargo tauri build --verbose
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
     Running [tauri_cli] Command `cargo  build --features custom-protocol --release`
   Compiling app v0.1.0 (/home/dvk/tmp/tauri-onnxruntime/src-tauri)
    Finished release [optimized] target(s) in 24.11s
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] built glob set; 0 literals, 2 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
       Debug [globset] glob converted to regex: Glob { glob: "**/npm-debug.log*", re: "(?-u)^(?:/?|.*/)npm\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('n'), Literal('p'), Literal('m'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-debug.log*", re: "(?-u)^(?:/?|.*/)yarn\\-debug\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('d'), Literal('e'), Literal('b'), Literal('u'), Literal('g'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] glob converted to regex: Glob { glob: "**/yarn-error.log*", re: "(?-u)^(?:/?|.*/)yarn\\-error\\.log[^/]*$", opts: GlobOptions { case_insensitive: false, literal_separator: true, backslash_escape: true }, tokens: Tokens([RecursivePrefix, Literal('y'), Literal('a'), Literal('r'), Literal('n'), Literal('-'), Literal('e'), Literal('r'), Literal('r'), Literal('o'), Literal('r'), Literal('.'), Literal('l'), Literal('o'), Literal('g'), ZeroOrMore]) }
       Debug [globset] built glob set; 4 literals, 6 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 3 regexes
       Debug [globset] built glob set; 1 literals, 0 basenames, 0 extensions, 0 prefixes, 0 suffixes, 0 required extensions, 0 regexes
    Bundling [tauri_bundler::bundle::linux::debian] tauri-onnxruntime_0.1.0_amd64.deb (/home/dvk/tmp/tauri-onnxruntime/src-tauri/target/release/bundle/deb/tauri-onnxruntime_0.1.0_amd64.deb)
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("arch")], "arch")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("icon_path")], "icon_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("icon_path")], "icon_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("appimage_filename")], "appimage_filename")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("tauri_tools_path")], "tauri_tools_path")))
       Debug [handlebars::render] Rendering value: Path(Relative(([Named("app_name")], "app_name")))
    Bundling [tauri_bundler::bundle::linux::appimage] tauri-onnxruntime_0.1.0_amd64.AppImage (/home/dvk/tmp/tauri-onnxruntime/src-tauri/target/release/bundle/appimage/tauri-onnxruntime_0.1.0_amd64.AppImage)
     Running [tauri_bundler::bundle::common] Command `/home/dvk/tmp/tauri-onnxruntime/src-tauri/target/release/bundle/appimage/build_appimage.sh `
+ export ARCH=x86_64
+ ARCH=x86_64
+ APPIMAGE_BUNDLE_XDG_OPEN=0
+ APPIMAGE_BUNDLE_GSTREAMER=0
+ TRAY_LIBRARY_PATH=0
+ '[' x86_64 == i686 ']'
+ linuxdeploy_arch=x86_64
+ mkdir -p tauri-onnxruntime.AppDir
+ cp -r ../appimage_deb/data/usr tauri-onnxruntime.AppDir
+ cd tauri-onnxruntime.AppDir
+ mkdir -p usr/bin
+ mkdir -p usr/lib
+ [[ 0 != \0 ]]
+ [[ 0 != \0 ]]
++ dirname '{}'
+ find /usr/lib /usr/lib32 /usr/lib64 /usr/libexec /usr/libx32 -name WebKitNetworkProcess -exec mkdir -p . ';' -exec cp --parents '{}' . ';'
++ dirname '{}'
+ find /usr/lib /usr/lib32 /usr/lib64 /usr/libexec /usr/libx32 -name WebKitWebProcess -exec mkdir -p . ';' -exec cp --parents '{}' . ';'
++ dirname '{}'
+ find /usr/lib /usr/lib32 /usr/lib64 /usr/libexec /usr/libx32 -name libwebkit2gtkinjectedbundle.so -exec mkdir -p . ';' -exec cp --parents '{}' . ';'
+ wget -q -4 -N -O /home/dvk/.cache/tauri/AppRun https://github.com/AppImage/AppImageKit/releases/download/continuous/AppRun-x86_64
+ chmod +x /home/dvk/.cache/tauri/AppRun
+ cp /home/dvk/.cache/tauri/AppRun .
+ cp usr/share/icons/hicolor/256x256@2/apps/tauri-onnxruntime.png .DirIcon
+ ln -s usr/share/icons/hicolor/256x256@2/apps/tauri-onnxruntime.png tauri-onnxruntime.png
+ ln -s usr/share/applications/tauri-onnxruntime.desktop tauri-onnxruntime.desktop
+ cd ..
+ [[ 0 != \0 ]]
+ gst_plugin=
+ wget -q -4 -N -O /home/dvk/.cache/tauri/linuxdeploy-plugin-gtk.sh https://raw.githubusercontent.com/tauri-apps/linuxdeploy-plugin-gtk/master/linuxdeploy-plugin-gtk.sh
+ wget -q -4 -N -O /home/dvk/.cache/tauri/linuxdeploy-x86_64.AppImage https://github.com/tauri-apps/binary-releases/releases/download/linuxdeploy/linuxdeploy-x86_64.AppImage
+ chmod +x /home/dvk/.cache/tauri/linuxdeploy-plugin-gtk.sh
+ chmod +x /home/dvk/.cache/tauri/linuxdeploy-x86_64.AppImage
+ dd if=/dev/zero bs=1 count=3 seek=8 conv=notrunc of=/home/dvk/.cache/tauri/linuxdeploy-x86_64.AppImage
3+0 records in
3+0 records out
3 bytes copied, 0.000144287 s, 20.8 kB/s
+ OUTPUT=tauri-onnxruntime_0.1.0_amd64.AppImage
+ /home/dvk/.cache/tauri/linuxdeploy-x86_64.AppImage --appimage-extract-and-run --appdir tauri-onnxruntime.AppDir --plugin gtk --output appimage
linuxdeploy version 1-alpha (git commit ID 56760df), GitHub actions build 90 built on 2022-07-12 10:39:09 UTC

-- Creating basic AppDir structure -- 
Creating directory tauri-onnxruntime.AppDir/usr/bin/ 
Creating directory tauri-onnxruntime.AppDir/usr/lib/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/applications/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/icons/hicolor/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/icons/hicolor/16x16/apps/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/icons/hicolor/32x32/apps/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/icons/hicolor/64x64/apps/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/icons/hicolor/128x128/apps/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/icons/hicolor/256x256/apps/ 
Creating directory tauri-onnxruntime.AppDir/usr/share/icons/hicolor/scalable/apps/ 

-- Deploying dependencies for existing files in AppDir -- 
Deploying dependencies for ELF file tauri-onnxruntime.AppDir/usr/bin/tauri-onnxruntime 
ERROR: Could not find dependency: libonnxruntime.so.1.8.1 
ERROR: Failed to deploy dependencies for existing files 
       Error [tauri_cli] failed to bundle project: error running appimage.sh: error running appimage.sh: `failed to run /home/dvk/tmp/tauri-onnxruntime/src-tauri/target/release/bundle/appimage/build_appimage.sh`
```