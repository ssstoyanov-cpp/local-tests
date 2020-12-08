# Включаем локальные тесты

1. Скачиваем [gtest](https://github.com/google/googletest/archive/release-1.10.0.tar.gz)
2. Распаковываем в папку с проектом, называем её ```gtest``` чтобы было как на скрине

![image1](/images/image1)

3. Добавляем в корневой ```CMakeLists.txt``` вот эти строки 

```
################################
# Testing
################################

# Make PROJECT_SOURCE_DIR, PROJECT_BINARY_DIR, and PROJECT_NAME available.
set(CMAKE_CXX_STANDARD 17)
set(PROJECT_NAME Ex08)
project(${PROJECT_NAME})


# Define project test files
file(GLOB TEST_SRC_FILES ${PROJECT_SOURCE_DIR}/test/*.cpp)

# FIXME: Define all cpp files which you want to test
set(SRC_FILES ${PROJECT_SOURCE_DIR}/src/main.cpp
        ${PROJECT_SOURCE_DIR}/src/MyString.cpp
        ${PROJECT_SOURCE_DIR}/include/MyString.h )

add_library(task_lib ${SRC_FILES})

# This adds another subdirectory, which has 'poject(gtest)'.
add_subdirectory(gtest)

# Unit Tests
add_executable(runUnitTests ${TEST_SRC_FILES})

# Standard linking to gtest stuff.
target_link_libraries(runUnitTests gtest gtest_main)

# Extra linking for the project.
target_link_libraries(runUnitTests task_lib)

```

4. Редактируем исходные файлы в строке ```set(SRC_FILES...``` (звездочка не работает, чтобы добавлялись все, если найдете как сделать — напишите)
5. Меняем конфигурацию запуска, так чтобы она была как на скрине

![image2](/images/image2)
