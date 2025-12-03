cmake_minimum_required(VERSION 3.16)
project(opc_server_project C)

set(CMAKE_C_STANDARD 99)

# Подключаем open62541 как под-проект
add_subdirectory(external/open62541)

# Твой исполняемый файл
add_executable(opc_server
    src/main.c
    src/init.c
    src/config.c
    src/math_model.c
    src/opcuaSettings.c
)

# Инклюды для твоих заголовков и open62541
target_include_directories(opc_server PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/src
    ${CMAKE_CURRENT_SOURCE_DIR}/external/open62541/include
    ${CMAKE_CURRENT_BINARY_DIR}/external/open62541
)

# Линкуемся с библиотекой open62541
target_link_libraries(opc_server PRIVATE open62541)
