#
# project: fips-sx
#
cmake_minimum_required(VERSION 2.8)

# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")


fips_setup(PROJECT fips-sx)
    # just suppress this pesky "missing field initializer warning" for now
    if (FIPS_CLANG OR FIPS_GCC)
        set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-missing-field-initializers")
    endif()
    if (FIPS_GCC)
        set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-missing-braces")
    endif()

    fips_add_subdirectory(sx)

fips_finish()


