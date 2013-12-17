
## Assmeble list of source files
file (GLOB libphoenix_sources *.cpp)

## Compiler instructions
add_library (phoenix ${libphoenix_sources})
