CC=gcc -g
AR=ar -rcs
OBJECTS_MAIN=main.o
OBJECTS_LIB = txfind.o
FLAGS= -Wall -fPIC

all: finds findd mains txtfind
mains: $(OBJECTS_MAIN) libmytxfind.a
	$(CC) $(FLAGS) -o mains $(OBJECTS_MAIN) libmytxfind.a
txtfind: $(OBJECTS_MAIN) libmytxfind.so
	$(CC) $(FLAGS) -o txtfind $(OBJECTS_MAIN) ./libmytxfind.so
finds: libmytxfind.a
libmytxfind.a: $(OBJECTS_LIB) txfind.h
	$(AR) libmytxfind.a $(OBJECTS_LIB)
findd: libmytxfind.so
libmytxfind.so: $(OBJECTS_LIB) txfind.h
	$(CC) -shared -o libmytxfind.so $(OBJECTS_LIB)
main.o: main.c
	$(CC) $(FLAGS) -c main.c
txfind.o: txfind.c txfind.h
	$(CC) $(FLAGS) -c txfind.c

.PHONY: clean all finds findd

clean:
	rm -f *.o *.a *.so mains txtfind