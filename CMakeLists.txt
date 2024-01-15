cmake_minimum_required(VERSION 3.15)
project(cards)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_BUILD_TYPE Debug)

set(GLFW_BUILD_TESTS
    OFF
    CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES
    OFF
    CACHE BOOL "" FORCE)

add_subdirectory(libs/glfw)
add_subdirectory(libs/glad)
add_subdirectory(libs/glm)

set(SOURCES
    src/stb_image.cpp
    src/render/shadermanager.cpp
    src/render/shaderprogram.cpp
    src/render/renderable.cpp
    src/render/renderer.cpp
    src/render/renderables/sprite.cpp
    src/render/texture.cpp
    src/render/texturemanager.cpp
    src/input/clickable.cpp
    src/input/inputmanager.cpp
    src/main.cpp
    src/core/logging.cpp
    src/core/paths.cpp
    src/core/transform.cpp
    src/core/application.cpp
    src/game/card.cpp
    src/game/deckstack.cpp
    src/game/cardstack.cpp
    src/game/gamebase.cpp
    src/game/solitaire/solitairegame.cpp)

set(INCLUDES
    src/stb_image.h
    src/render/texturemanager.h
    src/render/shadermanager.h
    src/render/texture.h
    src/render/renderer.h
    src/render/renderable.h
    src/render/shaderprogram.h
    src/render/renderables/sprite.h
    src/input/clickable.h
    src/input/inputmanager.h
    src/core/application.h
    src/core/paths.h
    src/core/logging.h
    src/core/transform.h
    src/core/rect.h
    src/game/card.h
    src/game/cardtypes.h
    src/game/deckstack.h
    src/game/cardstack.h
    src/game/gamebase.h
    src/game/solitaire/solitairegame.h)

add_executable(${PROJECT_NAME} ${SOURCES} ${INCLUDES})
target_include_directories(${PROJECT_NAME}
                           PUBLIC ${CMAKE_CURRENT_SOURCE_DIR/src/})
target_include_directories(${PROJECT_NAME}
                           PUBLIC {CMAKE_CURRENT_SOURCE_DIR}/include/glm/glm)
target_link_libraries(${PROJECT_NAME} glfw glad glm)
