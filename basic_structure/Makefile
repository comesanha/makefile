# TARGETS
# target: prerequisites
#	commands

# The commands are a series of steps typiclly to make the target.
# Is need to strat each line targets with tab.
#The prerequisits are file name ssepareted by spaces.
# these files need to exist before de commandsfor de target are run.

build: my_lib.o main.o
	g++ main.o my_lib.o -o main
	
main.o:
	g++ main.cpp -c

my_lib.o:
	g++ my_lib.cpp -c
	



execute:
	./main

# clean is often used as a target that removes the outputs of other targets.
clean:
	rm -f *.o
	rm -f main