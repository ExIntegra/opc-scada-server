add_executable(opc_server
    main.c
    init.c
    config.c
    math_model.c
    opcSettings.c
)

target_link_libraries(opc_server PRIVATE open62541)

target_include_directories(opc_server PRIVATE
    ${PROJECT_SOURCE_DIR}/src
    ${PROJECT_SOURCE_DIR}/external/open62541/include
    ${PROJECT_BINARY_DIR}/external/open62541
)
