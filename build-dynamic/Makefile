LIB_SRC=ctest1.c ctest2.c
LIB_OBJ=$(LIB_SRC:.c=.o)
SO_OBJS=ctest1.o ctest2.o
SO_NAME=libctest.so

INCLUDES=-I.
SRC=prog.c
OBJ=prog.o
OUT=prog

CFLAGS=-Wall
LDFLAGS=-L. -lctest
CC=gcc

default: $(OUT)

.c.o:
	$(CC) -c -fPIC $(CFLAGS) $< -o $@

$(SO_NAME): $(LIB_OBJ)
	$(CC) -shared -Wl,-soname,$(SO_NAME) -o $(SO_NAME).1.0 $(SO_OBJS)
	ln -sf ./$(SO_NAME).1.0 ./$(SO_NAME).1
	ln -sf ./$(SO_NAME).1.0 ./$(SO_NAME)

$(OUT): $(SO_NAME)
	$(CC) -c $(INCLUDES) $(CFLAGS) $(SRC) -o $(OBJ)
	$(CC) $(OBJ) $(LDFLAGS) -o $(OUT)

check: $(OUT)
	LD_LIBRARY_PATH=. ./$(OUT)

clean:
	rm -f *.o *.a *.so  $(SO_NAME).* $(OUT)
