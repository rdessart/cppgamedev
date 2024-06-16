cmake_minimum_required(VERSION 3.5.0)
project(Chapter02 VERSION 0.1.0 LANGUAGES C CXX)
set (CMAKE_CXX_STANDARD 11)

add_executable(Chapter02 Actor.cpp AnimSpriteComponent.cpp BGSpriteComponent.cpp Component.cpp Game.cpp Main.cpp Math.cpp Ship.cpp SpriteComponent.cpp)

file(COPY Assets DESTINATION .)

find_package(SDL2 CONFIG REQUIRED)
target_link_libraries(Chapter02
    PRIVATE
    $<TARGET_NAME_IF_EXISTS:SDL2::SDL2main>
    $<IF:$<TARGET_EXISTS:SDL2::SDL2>,SDL2::SDL2,SDL2::SDL2-static>
)

find_package(SDL2_image CONFIG REQUIRED)
target_link_libraries(Chapter02 PRIVATE $<IF:$<TARGET_EXISTS:SDL2_image::SDL2_image>,SDL2_image::SDL2_image,SDL2_image::SDL2_image-static>)