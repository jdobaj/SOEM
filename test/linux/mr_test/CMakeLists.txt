
set(SOURCES mr_test.c)
add_executable(mr_test ${SOURCES})
target_link_libraries(mr_test soem)
install(TARGETS mr_test DESTINATION bin)
