cmake_minimum_required(VERSION 3.4 FATAL_ERROR)

project(TelegramRecorder VERSION 1.0 LANGUAGES CXX)

add_subdirectory(td)
find_package(spdlog REQUIRED)
find_package(OpenSSL REQUIRED)
find_library(config++ config++)
find_library(fmt fmt)

add_executable(tgrec main.cpp telegram_recorder.cpp auth.cpp message_reader.cpp config.cpp db.cpp telegram_data.cpp hash.cpp)
target_link_libraries(tgrec PRIVATE Td::TdStatic config++ spdlog::spdlog fmt ssl)
set_property(TARGET tgrec PROPERTY CXX_STANDARD 17)
