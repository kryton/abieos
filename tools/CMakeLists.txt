# copyright defined in abieos/LICENSE.txt

find_package(Threads)

add_executable(name name.cpp)
target_link_libraries(name abieos ${CMAKE_THREAD_LIBS_INIT})

add_custom_command( TARGET name POST_BUILD COMMAND ${CMAKE_COMMAND} -E create_symlink $<TARGET_FILE:name> ${CMAKE_CURRENT_BINARY_DIR}/name2num )
add_custom_command( TARGET name POST_BUILD COMMAND ${CMAKE_COMMAND} -E create_symlink $<TARGET_FILE:name> ${CMAKE_CURRENT_BINARY_DIR}/num2name )

add_executable(hex_to_json hex_to_json.c)
target_link_libraries(hex_to_json abieos ${CMAKE_THREAD_LIBS_INIT})

add_custom_command( TARGET hex_to_json POST_BUILD COMMAND ${CMAKE_COMMAND} -E create_symlink $<TARGET_FILE:hex_to_json> ${CMAKE_CURRENT_BINARY_DIR}/json2hex )
add_custom_command( TARGET hex_to_json POST_BUILD COMMAND ${CMAKE_COMMAND} -E create_symlink $<TARGET_FILE:hex_to_json> ${CMAKE_CURRENT_BINARY_DIR}/hex2json )
