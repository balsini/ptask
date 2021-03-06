# Add include directory
include_directories(.)
include_directories(../src/)

# Create the executable.
add_executable(time time.c)
add_executable(key key.c)
add_executable(key_opt key_opt.c)
add_executable(test_cores test_cores.c)
add_executable(task_create task_create.c)
add_executable(task_aperiodic task_aperiodic.c)

# Indicate that ptask library dependency
target_link_libraries(time ptask)
target_link_libraries(key ptask Threads::Threads)
target_link_libraries(key_opt ptask Threads::Threads)
target_link_libraries(test_cores ptask Threads::Threads)
target_link_libraries(task_create ptask Threads::Threads)
target_link_libraries(task_aperiodic ptask Threads::Threads)

# Create tests from executables
add_test(timeTest time)
add_test(Test time)
add_test(keyTest key)
add_test(key_optTest key_opt)
add_test(test_coresTest test_cores)
add_test(task_createTest task_create)
add_test(task_aperiodicTest task_aperiodic)

file(COPY runtest.sh DESTINATION ${CMAKE_CURRENT_BINARY_DIR})