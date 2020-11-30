cmake_minimum_required(VERSION 3.2)
project(jpegfunk C)

add_compile_options(-fopenmp)
add_link_options(-fopenmp)


# source files
set(JPEGFUNK_SOURCE_FILES
        src/jpegfunk.c
        )

find_library(JPEG_LIB NAMES libjpeg jpeg)
find_library(OMP_LIB NAMES libomp omp HINTS /opt/local/lib/libomp/)

include_directories(/usr/include /usr/local/include /opt/local/include)

add_executable(jpegfunk ${JPEGFUNK_SOURCE_FILES})
target_link_libraries(jpegfunk ${JPEG_LIB} ${OMP_LIB} m)
install(TARGETS jpegfunk DESTINATION bin)
