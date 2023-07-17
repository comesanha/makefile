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
EXECUTABLE_NAME = main #Name of executable file

CXX_STANDARD = c++17 #C++ standard
CXX_WARNINGS = -Wall -Wextra -Wpedantic # enables all and extra Warnings

CXX = g++ # C++ compiler
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS = 

#Debug or Release flag -- not working completelly
ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0 #not optimize  and generate debug symbols
else
CXXFLAGS += -O3 #highest optimization level
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS) # concatenatio of variables




build: my_lib.o main.o
	echo $(DEBUG)
	$(COMPILER_CALL) main.o my_lib.o $(LDFLAGS) -o $(EXECUTABLE_NAME)
	
main.o:
	$(COMPILER_CALL) main.cpp -c

my_lib.o:
	$(COMPILER_CALL) my_lib.cpp -c
	



execute:
	./main

# clean is often used as a target that removes the outputs of other targets.
clean:
	rm -f *.o
	rm -f main