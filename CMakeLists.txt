cmake_minimum_required(VERSION 3.18)
project(tinyalsa)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_C_STANDARD 99)

include_directories(include)

set(libtinyalsa
        mixer.c
        mixer_hw.c
        mixer_plugin.c
        pcm.c
        pcm_hw.c
        pcm_plugin.c
        snd_utils.c
        )

add_executable(tinyplay tinyplay.c ${libtinyalsa})
target_link_libraries(tinyplay -ldl)

add_executable(tinyalsa tinyhostless.c ${libtinyalsa})
target_link_libraries(tinyalsa -ldl)

add_executable(tinymix tinymix.c ${libtinyalsa})
target_link_libraries(tinymix -ldl)

add_executable(tinyhostless tinyhostless.c ${libtinyalsa})
target_link_libraries(tinyhostless -ldl)

add_executable(tinypcminfo tinypcminfo.c ${libtinyalsa})
target_link_libraries(tinypcminfo -ldl)