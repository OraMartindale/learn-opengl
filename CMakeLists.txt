cmake_minimum_required(VERSION 3.12)
project(learn-opengl)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# GLFW from Homebrew
find_package(glfw3 REQUIRED)

# Create glad implementation file if it doesn't exist
set(GLAD_IMPLEMENTATION_FILE "${CMAKE_CURRENT_SOURCE_DIR}/glad/glad.c")
if(NOT EXISTS ${GLAD_IMPLEMENTATION_FILE})
    file(WRITE ${GLAD_IMPLEMENTATION_FILE} "#include <glad/glad.h>\n")
endif()

# Add executable with glad implementation
add_executable(learn-opengl main.cpp ${GLAD_IMPLEMENTATION_FILE})

# Link libraries
target_link_libraries(learn-opengl PRIVATE glfw "-framework OpenGL")

# Add include directories
target_include_directories(learn-opengl PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}
)

# Add include directories
target_include_directories(learn-opengl PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${glad_SOURCE_DIR}/include
)
