OPC SCADA Server
Данный проект представляет собой учебный программный комплекс, включающий:
 - OPC UA сервер, написанный на C с использованием библиотеки open62541,
 - модель технологического процесса (реактор, клапаны, сенсоры, ПИД-регуляторы),
 - SCADA-проект в Ignition 8.1, реализующий визуализацию процесса и управление.
Проект предназначен для демонстрации:
- интеграции C-приложений с SCADA-системами,
- работы промышленных протоколов (OPC UA),
- моделирования технологических процессов,
- настройки человеко-машинного интерфейса (HMI).
  <img width="971" height="585" alt="{6683BE47-0F80-4C05-9EEF-595731C34A3D}" src="https://github.com/user-attachments/assets/d0283e15-ee54-47f1-953e-ea2619998b8c" />








opc-scada-server/
│
├── src/                     # Исходники OPC UA сервера
├── external/open62541/      # Встроенная библиотека open62541
├── IgnitionProject/         # Проект SCADA (Ignition 8.1)
├── CMakeLists.txt           # CMake-конфигурация сборки
└── README.md

1. Установка OPC UA сервера на Linux
   Требоввания:
   
   sudo apt-get update
   
   sudo apt-get install -y git build-essential cmake

   Сборка:
   
   git clone https://github.com/ExIntegra/opc-scada-server.git
   
   cd opc-scada-server
   
   mkdir build
   
   cd build
   
   cmake ..
   
   cmake --build .

   Запуск:
   
   ./opc_server

   endpoint сервера:
   
   opc.tcp://localhost:4840

3. Установка OPC UA сервера на Windows
   Требования:
   
    - Visual Studio 2019/2022 (Desktop development with C++)

    - CMake 3.16+
      
    - Git for Windows

   Сборка:
   
   Открыть x64 Native Tools Command Prompt for VS
   
   git clone https://github.com/ExIntegra/opc-scada-server.git
   
   cd opc-scada-server
   
   mkdir build
   
   cd build
   
   cmake .. -G "Visual Studio 17 2022" -A x64
   
   cmake --build . --config Release

   Запуск:
   
   .\build\Release\opc_server.exe

5. Установка и настройка Ignition 8.1
6. 
   Шаг 1. Установка Ignition
   
   Скачать Ignition 8.1 для Windows/Linux:
   
   https://inductiveautomation.com/downloads
  
   Установить с настройками по умолчанию.
   
   После запуска перейти в браузере на:
   
   http://localhost:8088
   
8. Импорт SCADA-проекта в Ignition

  Зайти в браузере в Gateway:
  
  http://localhost:8088
  
  В меню выбрать:
  
  Config → Projects → Import
  
  Нажать Choose File
  
  Выбрать файл:
  
  IgnitionProject/lab_scada_ignition_8_1.zip
  
  Нажать Import
  
  Проект появится в списке проектов.

5. Настройка подключения к OPC UA серверу
  Открыть:

  http://localhost:8088
  
  Перейти:
  
  Config → OPC Client → Servers
  
  Добавить новый сервер (или отредактировать существующий):
  
  Name: LocalOPCUA
  
  Endpoint:
  
  opc.tcp://localhost:4840
  
  Security: None (если у тебя не настроена криптография)
  
  Нажать Save Changes
  
  Должен появиться статус Connected

7. Запуск SCADA в Designer
  На странице Gateway:

  http://localhost:8088
  
  В разделе Launch Designer → скачать .jnlp или запускаемый клиент.
  
  Запустить Designer.
  
  Открыть проект lab_scada_ignition_8_1.zip
  
  Открыть окна визуализации.

9. Проверка работы
  Запустить OPC UA сервер:

  ./opc_server

Открыть визуализацию в Ignition.
Менять параметры, наблюдать за реакцией симулятора.
Смотреть значения тегов в модуле OPC Browser.
Проверять, что теги обновляются в реальном времени.
