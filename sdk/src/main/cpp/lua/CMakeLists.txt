
# 指定 CMake 最低版本
cmake_minimum_required(VERSION 3.18.1)

# 定义源文件的路径
set(LUA_SOURCES
        lapi.c
        lauxlib.c
        lbaselib.c
        lcode.c
        lcorolib.c
        lctype.c
        ldblib.c
        ldebug.c
        ldo.c
        ldump.c
        lfunc.c
        lgc.c
        linit.c
        liolib.c
        llex.c
        lmathlib.c
        lmem.c
        loadlib.c
        lobject.c
        lopcodes.c
        loslib.c
        lparser.c
        lstate.c
        lstring.c
        lstrlib.c
        ltable.c
        ltablib.c
        ltm.c
        lua.c       #lua.c的main是编译运行时用的
#        luac.c     #luac.c的main是编译一个将lua代码编译成EXE用的，我们需要去掉此文件的编译
        lundump.c
        lutf8lib.c
        lvm.c
        lzio.c
)

# 设置编译静态库
add_library(lua_static STATIC ${LUA_SOURCES})

# 设置静态库保存到libs中
set_target_properties(
        lua_static
        PROPERTIES
        ARCHIVE_OUTPUT_DIRECTORY
        "${CMAKE_CURRENT_SOURCE_DIR}/libs/${ANDROID_ABI}"
)

# 设置编译动态库
add_library(lua SHARED ${LUA_SOURCES})

# 设置动态库保存到libs中
set_target_properties(
        lua
        PROPERTIES
        LIBRARY_OUTPUT_DIRECTORY
        "${CMAKE_CURRENT_SOURCE_DIR}/libs/${ANDROID_ABI}"
)







