cmake_minimum_required (VERSION 3.6)

project(HLSL2GLSLConverter CXX)

set(SOURCE 
    src/HLSL2GLSLConverterApp.cpp
)

if(PLATFORM_WIN32)
    add_executable(HLSL2GLSLConverter ${SOURCE})
else()
    message(FATAL_ERROR "Unsupported platform")
endif()

set_common_target_properties(HLSL2GLSLConverter)

target_include_directories(HLSL2GLSLConverter PRIVATE
    ../../DiligentCore/Graphics/HLSL2GLSLConverterLib/include
)

target_compile_definitions(HLSL2GLSLConverter PRIVATE UNICODE)

target_link_libraries(HLSL2GLSLConverter 
PRIVATE 
    BuildSettings 
    TargetPlatform
    Common
    GraphicsTools
    HLSL2GLSLConverterLib 
    GraphicsEngineOpenGL-static
)

source_group("source" FILES ${SOURCE})

set_target_properties(HLSL2GLSLConverter PROPERTIES
    FOLDER Tools
)
