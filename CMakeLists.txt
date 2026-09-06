#SELECT VERSIONS AND INITIALIZE PROJECT/EXECD
cmake_minimum_required(VERSION 3.31)
set(CMAKE_CXX_STANDARD 20)
project(VulkanRenderer)
include(FetchContent)
add_executable(VulkanRenderer)

#ADD SRC FILES
target_sources(VulkanRenderer
        PRIVATE
            main.cpp
)

#Find dependencies
find_package(Vulkan REQUIRED)

FetchContent_Declare(
        glm
        GIT_REPOSITORY	https://github.com/g-truc/glm.git
        GIT_TAG 	0af55ccecd98d4e5a8d1fad7de25ba429d60e863
)
FetchContent_MakeAvailable(glm)

#Disables GLFW tests, examples and docs
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

FetchContent_Declare(
        glfw
        GIT_REPOSITORY	https://github.com/glfw/glfw.git
        GIT_TAG 	3.5.1
)

FetchContent_MakeAvailable(glfw)

#ADD DEPENDENCIES
target_link_libraries(VulkanRenderer
        PRIVATE
            Vulkan::Vulkan
            glm::glm
            glfw
)