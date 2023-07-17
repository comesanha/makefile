###############
###VARIABLES###
###############
# Note: Variables can only be strings
# Note: Single or double quotes for variables names or values
#		have no meaning to Make.


# Predefined variables in the Makefile
# CC: Program for compiling C programs; default cc
# CXX: Program for compiling C++ programs; default g++
# CFLAGS: Extra flags to give to the C compiler
# CXXFLAGS: Extra flags to give to the C++ compiler
# CPPFLAGS: Extra flags to give to the C preprocessor
# LDFLAGS: Extra flags to give to the Linker

DEBUG = 1 #debug or release


CXX_STANDARD = c++17 #C++ standard
CXX_WARNINGS = -Wall -Wextra -Wpedantic # enables all and extra Warnings

CXX = g++ # C++ compiler
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS = 

#Debug or Release flag -- not working completelly
ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0 #not optimize  and generate debug symbols
EXECUTABLE_NAME = mainDebug #Name of executable file
else
CXXFLAGS += -O3 #highest optimization level
EXECUTABLE_NAME = mainRelease #Name of executable file
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) # concatenatio of variables

# busca tosod os arquivos.cpp
CXX_SOURCES = $(wildcard *.cpp)
#Substitui os .cpp por .o no nome dos arquivos.
CXX_OBJECTS = $(patsubst %.cpp, %.o, $(CXX_SOURCES))


build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_NAME)
	
execute:
	./main

# clean is often used as a target that removes the outputs of other targets.
clean:
	rm -f *.o
	rm -f main

##############
###PATTERNS###
##############

#gera um arquivo objeto (.o) para cada arquivo .cpp presente no diretório
# $@: the file name of the target
# $<: The name of the first dependency
# $^: The names of the all prerequisites
%.o: %.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@

# %.o: %.cc
# 	$(CXX_COMPILER_CALL) -c $< -o
# %.o: %.cxx
# 	$(CXX_COMPILER_CALL) -c $< -o