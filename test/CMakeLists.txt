#
#
# Compiling/running tests
set ( CMAKE_RUNTIME_OUTPUT_DIRECTORY ${dist_dir}/test )

function (sa_test name)
  add_executable ( ${name}_test ${name}_test.c test_utils.c)
  target_link_libraries ( ${name}_test PRIVATE icelib stunlib sockaddrutil )
  target_include_directories ( ${name}_test PRIVATE ../include )
  add_test ( NAME ${name} COMMAND ${name}_test )
endfunction()

sa_test ( icelib )
sa_test ( icelibtypes )
sa_test ( icelib_running )
sa_test ( icelib_ce )
sa_test ( icelib_nomination )

include ( CTest )
