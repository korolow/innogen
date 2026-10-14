# Overview
###### This does not contain the source for Korolow's Innogen, for that, please go to tcp6://p4.korolow.com:1666 via p4 (user: community_user1, passwd: Community#Korolow!.).

![Boot Texture](https://github.com/korolowcorp/innogen/blob/main/boottex.png?raw=true)

---

# System Requirements

### ntoskrnl.exe + csrss.exe Hosts
- Microsoft Visual Studio (`cl` / `link`) with `nmake`.
- Windows SDK headers (`opengl32.lib`, `winmm.lib`, etc.).

### Unix Hosts
- An ISO C/C++ compliant compiler (`gcc` or `clang` supporting C89 and C++98).
- `Make` (from Std 1003.1, POSIX).
- Development headers for X11/Quartz, Vulkan, Metal, or GL1.1/GL3/GLES3.
- ALSA, OSS, or CoreAudio headers for audio mixing.

---

## Compilation & Build Flags

The compilation is driven by `Makefile`, `Makefile.unix`, and `Makefile.osx`.

`ruby mkfiles/genmake.rb --renderer gl --outdir dist --objdir obj --vscript=sq # or use \`

### Available Flags
* **`-debug`** : Enables debug symbols and address/undefined sanitizers (`-fsanitize=address,undefined`).
* **`-renderer <gl|soft>`** : Selects OpenGL (`gl`) or Software (`soft`) rendering targets.
* **`-outdir <dir>`** : Directs binary and `.so`/`.dll` output to a custom directory.
* **`-objdir <dir>`** : Sets intermediate object file destinations.

---

## Compiling From Source

1. **On ntoskrnl.exe + csrss.exe Hosts:**
   nmake /f dist\Makefile

2. **On Unix Hosts:**
   make -f dist/Makefile.unix

3. **On OS X Hosts:**
   make -f dist/Makefile.osx

---

## Directory Layout & Subsystems

* **`tier0/`** : Core memory allocators, interfaces, and foundational platform hooks.
* **`tier1/`** : KeyValues parsers, string tools, and utility helpers.
* **`vstdlib/`** : Command-line argument parsing and process management.
* **`mathlib/`** : Optimized vector, matrix, and geometric math routines.
* **`vtf/ & bitmap/`** : Texture loaders, DXT compression helpers, and image format parsers.
* **`model/`** : Clean-room asset parsers for MDL, VVD, and PHY structures.
* **`audio/`** : Multi-channel audio mixing pipeline (WinMM & ALSA targets).
* **`render/`** : Modular rendering backends (`ref_gl` for OpenGL and `ref_soft` for software rasterization).
* **`game/`** : Game logic and client/server simulation modules.
* **`engine/`** : Main system loops, boot screen management, and subsystem initialization.
