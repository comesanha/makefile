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

override DEBUG := 1 #debug or release ****testar

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

CXX_STANDARD = c++17 #C++ standard
CXX_WARNINGS = -Wall -Wextra -Wpedantic # enables all and extra Warnings

CXX = g++ # C++ compiler
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
CPPFLAGS = -I $(INCLUDE_DIR)#indicate includes to preprocessor
LDFLAGS = 

#Debug or Release flag -- not working completelly
ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0 #not optimize  and generate debug symbols
EXECUTABLE_NAME = mainDebug #Name of executable file
else
CXXFLAGS += -O3 #highest optimization level
EXECUTABLE_NAME = mainRelease #Name of executable file
endif



CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS) # concatenatio of variables

# busca todos os arquivos.cpp
CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cpp)
#Substitui os .cpp por .o no nome dos arquivos.
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(CXX_SOURCES))


build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)
	
execute:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

# clean is often used as a target that removes the outputs of other targets.
clean:
	rm -f $(BUILD_DIR)/*.o
	rm -f $(BUILD_DIR)/$(EXECUTABLE_NAME)

##############
###PATTERNS###
##############

#gera um arquivo objeto (.o) para cada arquivo .cpp presente no diretório
# $@: the file name of the target
# $<: The name of the first dependency
# $^: The names of the all prerequisites
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	$(CXX_COMPILER_CALL) -c $< -o $@

# %.o: %.cc
# 	$(CXX_COMPILER_CALL) -c $< -o
# %.o: %.cxx
# 	$(CXX_COMPILER_CALL) -c $< -o