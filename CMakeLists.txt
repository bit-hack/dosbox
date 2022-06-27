cmake_minimum_required(VERSION 3.0)
project(dosbox)

find_package(SDL REQUIRED)

file(GLOB SOURCE

  include/*.h
  src/*.cpp

  src/cpu/core_dyn_x86/*.h
  src/cpu/core_dyn_x86/*.cpp
  src/cpu/core_dynrec/*.h
  src/cpu/core_dynrec/*.cpp
  src/cpu/core_full/*.h
  src/cpu/core_full/*.cpp
  src/cpu/core_normal/*.h
  src/cpu/core_normal/*.cpp
  src/cpu/*.h
  src/cpu/*.cpp

  src/debug/*.h
  src/debug/*.cpp

  src/dos/*.h
  src/dos/*.cpp

  src/fpu/*.h
  src/fpu/*.cpp

  src/gui/*.h
  src/gui/*.cpp

  src/hardware/mame/*.h
  src/hardware/mame/*.cpp

  src/hardware/serialport/*.h
  src/hardware/serialport/*.cpp

  src/hardware/*.h
  src/hardware/*.cpp

  src/ints/*.h
  src/ints/*.cpp

  src/misc/*.h
  src/misc/*.cpp

  src/platform/visualc/*.h
  src/platform/visualc/*.cpp

  src/shell/*.h
  src/shell/*.cpp
)


add_executable(dosbox
  ${SOURCE}
)

target_include_directories(dosbox
  PUBLIC
  ${SDL_INCLUDE_DIR}
  include
  src/platform/visualc
)

target_link_libraries(dosbox
  ${SDL_LIBRARY}
  OPENGL32.lib
  winmm.lib
)
