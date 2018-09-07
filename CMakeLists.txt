
project(CMakePlay C)

############ app 1 ##############

add_library(a1 STATIC a.c)
target_link_libraries(a1 PUBLIC b1)

add_library(b1 STATIC b.c)
target_link_libraries(b1 PUBLIC c1)

add_library(c1 STATIC c.c)

add_executable(app1 main.c)
target_link_libraries(app1 a1)


############ app 2 ##############

add_library(a2 STATIC a.c)
target_link_libraries(a2 PUBLIC b2)

add_library(b2 STATIC b.c)
target_link_libraries(b2 PUBLIC c2)

add_library(c2 STATIC c.c)

add_executable(app2 main.c)
target_link_libraries(app2 -Wl,--whole-archive a2 -Wl,--no-whole-archive)

############ app 3 ##############

add_library(a3 STATIC a.c)

add_library(b3 STATIC b.c)

add_library(c3 STATIC c.c)

add_executable(app3 main.c)
target_link_libraries(app3 -Wl,--whole-archive a3 b3 c3 -Wl,--no-whole-archive)
