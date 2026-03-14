# Makefile for test
# 使用 CMake 构建和管理 C++ 项目


.PHONY: build run clear all debug

build:
	cmake -S . -B build -Wno-dev -DCMAKE_BUILD_TYPE=Release > /dev/null
	cmake --build build -- -s

debug:
	cmake -S . -B build -Wno-dev -DCMAKE_BUILD_TYPE=Debug > /dev/null
	cmake --build build -- -s

run:
	./bin/test

clear:
	rm -rf bin

all: build run clear
