CC=gcc -g
AR=ar -rcs
OBJECTS_MAIN=main.o
OBJECTS_LIB = isort.o
FLAGS= -Wall -fPIC

all: isorts isortd mains isort
mains: $(OBJECTS_MAIN) libmyisort.a
	$(CC) $(FLAGS) -o mains $(OBJECTS_MAIN) libmyisort.a
isort: $(OBJECTS_MAIN) libmyisort.so
	$(CC) $(FLAGS) -o isort $(OBJECTS_MAIN) ./libmyisort.so
isorts: libmyisort.a
libmyisort.a: $(OBJECTS_LIB) isort.h
	$(AR) libmyisort.a $(OBJECTS_LIB)
iisortd: libmyisort.so
libmyisort.so: $(OBJECTS_LIB) isort.h
	$(CC) -shared -o libmyisort.so $(OBJECTS_LIB)
main.o: main.c
	$(CC) $(FLAGS) -c main.c
isort.o: isort.c isort.h
	$(CC) $(FLAGS) -c isort.c

.PHONY: clean all isorts isortd

clean:
	rm -f *.o *.a *.so mains isort