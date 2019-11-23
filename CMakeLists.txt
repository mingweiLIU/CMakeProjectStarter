cmake_minimum_required(VERSION 3.11)

#####################Project settings###################################
project(DTUnion LANGUAGES C CXX)
set(VERSION_MAJOR "0")
set(VERSION_MINOR "1")
set(VERSION_PATCH "0")
set(PROJECT_VERSION ${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_PATCH})

SET(CMAKE_INSTALL_PREFIX < install_path >)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/lib)
set(CMAKE_MODULE_PATH "CMAKE_MODULE_PATH;CMAKE_CURRENT_SOURCE_DIR/cmake")

if(MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /bigobj /MP /wd4996 /wd4819 /wd4251 /wd4267 /wd4244 /wd4275 /wd4005 /wd5033 /wd4018")
    add_definitions(-DGLOG_NO_ABBREVIATED_SEVERITIES -DWIN32_LEAN_AND_MEAN -DNOMINMAX -D_ENABLE_EXTENDED_ALIGNED_STORAGE) 
endif(MSVC)

if(APPLE)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-inconsistent-missing-override -Wno-unused-command-line-argument -Wno-unused-result -Wno-exceptions")
    set(CMAKE_OSX_DEPLOYMENT_TARGET "10.9" CACHE STRING "Minimum OS X deployment version")
endif(APPLE)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)
set_target_properties(${TARGET_NAME} PROPERTIES DEBUG_POSTFIX "_d")
set_target_properties(${TARGET_NAME} PROPERTIES RELEASE_POSTFIX "_r")

#设置编译对象是静态还是动态库
#ADD_LIBRARY(hello SHARED ${LIBHELLO_SRC})
#ADD_LIBRARY(hello STATIC ${LIBHELLO_SRC})


# if(H2O_BUILD_CUDA)
#     enable_language(CUDA)
#     add_definitions(-DH2O_BUILD_CUDA)
#     find_package(CUDA REQUIRED)
# endif(H2O_BUILD_CUDA)

#############################Library settings#######################################################################

find_package(Qt5 REQUIRED COMPONENTS Core Gui Widgets LinguistTools Network WinExtras)
# include(Qt5LinguistToolsMacrosNoInclude) # 添加创建翻译文件的函数

find_package(GDAL REQUIRED)

# find_package(OpenSceneGraph REQUIRED osg osgDB osgViewer osgGA osgUtil)
# include_directories(${OPENSCENEGRAPH_INCLUDE_DIRS})

find_package(Assimp REQUIRED)

find_package(PCL REQUIRED)
include_directories(${PCL_INCLUDE_DIRS})

include_directories(${CMKE_CURRENT_LIST_DIR}/pub ${CMAKE_CURRENT_SOURCE_DIR}/src)     #include
#############################Source Files#################################################################
add_subdirectory(src)
# add_subdirectory(pub)
