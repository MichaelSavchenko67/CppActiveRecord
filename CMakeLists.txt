cmake_minimum_required (VERSION 3.5)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_COMPILER /usr/local/arm_linux_4.8/bin/arm-linux-g++)
set(CMAKE_C_COMPILER /usr/local/arm_linux_4.8/bin/arm-linux-gcc)

project(cpp-active-record)
set(CMAKE_C_FLAGS "-O2 -pipe -std=gnu99")
set(CMAKE_CXX_FLAGS "-O2 -pipe -std=c++11 -Werror -Wno-pmf-conversions -Wall")
set(CMAKE_EXE_LINKER_FLAGS "-lsqlite3")

include_directories(/usr/local/arm_linux_4.8/arm-nuvoton-linux-uclibceabi/include/sqlite3/)
include_directories(/usr/local/arm_linux_4.8/arm-nuvoton-linux-uclibceabi/include/boost/)
include_directories(include/)

aux_source_directory(src srcDir)
aux_source_directory(src/sqlite srcSqliteDir)
set(HEADERS ${srcDir} ${srcSqliteDir})

add_library(cpp-active-record SHARED ${srcDir} ${srcSqliteDir} ${HEADERS})
