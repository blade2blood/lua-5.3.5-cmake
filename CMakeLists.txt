cmake_minimum_required(VERSION 3.6)

project(Lua5)

option(LUA_USE_DLL " Lua Use dll" TRUE)

set(LUA_DOC_PATH ./doc)


SET(LUA_SOURCE_LIST 
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
        src/lundump.c
        src/lutf8lib.c
        src/lvm.c
        src/lzio.c
    )

SET(LUA_MAIN_SRC 
	src/lua.c
	)

SET(LUA_MAIN_C_SRC 
	src/luac.c
	)

if (LUA_USE_DLL)
	add_library(lua5dll SHARED ${LUA_SOURCE_LIST})
	add_definitions(-DLUA_BUILD_AS_DLL)
else()
	add_library(lua5dll STATIC ${LUA_SOURCE_LIST})
endif()

add_executable(lua5 ${LUA_MAIN_SRC})

target_link_libraries(lua5 lua5dll)
