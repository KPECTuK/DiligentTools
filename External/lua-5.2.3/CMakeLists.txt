cmake_minimum_required (VERSION 3.3)

project(Lua CXX)

if(MSVC)
	add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

set(SOURCE 
	src/lapi.c
	src/lauxlib.c
	src/lbaselib.c
	src/lbitlib.c
	src/lcode.c
	src/lcorolib.c
	src/lctype.c
	src/ldblib.c
	src/ldebug.c
	src/ldo.c
	src/ldump.c
	src/lfunc.c
	src/lgc.c
	src/linit.c
	src/liolib.c
	src/llex.c
	src/lmathlib.c
	src/lmem.c
	src/loadlib.c
	src/lobject.c
	src/lopcodes.c
	src/loslib.c
	src/lparser.c
	src/lstate.c
	src/lstring.c
	src/lstrlib.c
	src/ltable.c
	src/ltablib.c
	src/ltm.c
#	src/lua.c
#	src/luac.c
	src/lundump.c
	src/lvm.c
	src/lzio.c
)

# We need to compile all source files with c++ compiler
set_source_files_properties(${SOURCE} PROPERTIES LANGUAGE CXX)

set(INCLUDE 
	src/lapi.h
	src/lauxlib.h
	src/lcode.h
	src/lctype.h
	src/ldebug.h
	src/ldo.h
	src/lfunc.h
	src/lgc.h
	src/llex.h
	src/llimits.h
	src/lmem.h
	src/lobject.h
	src/lopcodes.h
	src/lparser.h
	src/lstate.h
	src/lstring.h
	src/ltable.h
	src/ltm.h
	src/lua.h
	src/lua.hpp
	src/luaconf.h
	src/lualib.h
	src/lundump.h
	src/lvm.h
	src/lzio.h
	src/winappstubs.h
)

include_directories(
	src
)

add_library(
	Lua ${SOURCE} ${INCLUDE}
)

source_group("source" FILES ${SOURCE})
source_group("include" FILES ${INCLUDE})