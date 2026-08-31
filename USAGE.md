# Simulator quick reference (Windows)

## Start

```cmd
cd C:\SRC\Simulator\build-mingw
```

Console mode (type commands directly in the window):

```cmd
grblHAL_sim.exe
```

Telnet mode (connect a g-code sender to `localhost:23`):

```cmd
grblHAL_sim.exe -p 23
```

With step/block logging:

```cmd
grblHAL_sim.exe -p 23 -s step.out -b block.out
```

## Use

- Console commands: `$$` (settings), `$I` (info), `?` (status), `G91` + `G1 X10 F500` (move)
- Exit console mode: **Ctrl-X** (Ctrl-C force-kills)
- Sender: io-sender (https://iosender.com) or UGS — connect as Raw TCP / TCP to `127.0.0.1:23`, then stream `untitled-part.nc`
- "Fatal: socket error 10054" on disconnect = harmless

## Validate a g-code file without starting the sim

```cmd
grblHAL_validator.exe <file.nc>
```

Exit code 0 = OK, otherwise prints the first error.

## Rebuild

```cmd
cmake --build build-mingw -j 8
```

`cmake` is the VS-bundled one: `C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin\cmake.exe`
