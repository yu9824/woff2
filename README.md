# woff2
Convert ttf to woff2 and vice versa.

woff2 is a compressed file that is mainly used for using fonts on websites.

If the file is still too large after this compression, you may need to 'subset' the original ttf file - extract only the fonts you need.
For example, you can use [サブセットフォントメーカー](https://opentype.jp/subsetfontmk.htm).

## Build
```bash
git clone --recursive https://github.com/yu9824/woff2.git   # clone with submodule, brotli
```

```bash
cd woff2    # change directory to the cloned one
```

```bash
sh docker/build.sh  # build docker image
```

```bash
sh docker/run.sh    # run docker container
```
docker containerでbashを起動したタイミングで，`make clean all`が実行され，自動的に以下のRunコマンドが実行できるようになる．

## Run

Ensure the binaries from the build process are in your $PATH, then:
### Compress (ttf → woff2)
```
woff2_compress myfont.ttf
```

### Decompress (woff2 → ttf)
```
woff2_decompress myfont.woff2
```

## Changes from the original repository
- Create docker image and container
- Change git settings to ignore submodules changes when build commands.
    ```bash
    git config --local diff.ignoreSubmodules dirty
    ```

forked from [google/woff2](https://github.com/google/woff2)
> This is a README for the font compression reference code. There are several
> compression related modules in this repository.
> 
> brotli/ contains reference code for the Brotli byte-level compression
> algorithm. Note that it is licensed under the MIT license.
> 
> src/ contains the C++ code for compressing and decompressing fonts.
> 
> # Build & Run
> 
> This document documents how to run the compression reference code. At this
> writing, the code, while it is intended to produce a bytestream that can be
> reconstructed into a working font, the reference decompression code is not
> done, and the exact format of that bytestream is subject to change.
> 
> The build process depends on the g++ compiler.
> 
> ## Build
> 
> On a standard Unix-style environment:
> 
> ```
> git clone --recursive https://github.com/google/woff2.git
> cd woff2
> make clean all
> ```
> 
> Alternatively, if Brotli is already installed on your system you can use CMake
> to build executables and libraries:
> 
> ```
> git clone https://github.com/google/woff2.git
> cd woff2
> mkdir out
> cd out
> cmake ..
> make
> make install
> ```
> 
> By default, shared libraries are built. To use static linkage, do:
> 
> ```
> cd woff2
> mkdir out-static
> cmake -DBUILD_SHARED_LIBS=OFF ..
> make
> make install
> ```
> 
> ## Run
> 
> Ensure the binaries from the build process are in your $PATH, then:
> 
> ```
> woff2_compress myfont.ttf
> woff2_decompress myfont.woff2
> ```
> 
> # References
> 
> http://www.w3.org/TR/WOFF2/
> http://www.w3.org/Submission/MTX/
> 
> Also please refer to documents (currently Google Docs):
> 
> WOFF Ultra Condensed file format: proposals and discussion of wire format
> issues (PDF is in docs/ directory)
> 
> WIFF Ultra Condensed: more discussion of results and compression techniques.
> This tool was used to prepare the data in that document.
> 