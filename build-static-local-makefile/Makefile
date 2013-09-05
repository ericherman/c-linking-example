LIB_SRC = ctest1.c ctest2.c
LIB_OBJ = $(LIB_SRC:.c=.o)
LIB_OUT = libctest.a

SRC = prog.c
OBJ = prog.o
OUT = prog

CFLAGS = -Wall
CC = gcc

default: $(OUT)

.c.o:
	$(CC) -c $(CFLAGS) $< -o $@

$(LIB_OUT): $(LIB_OBJ)
	ar -cvsq $(LIB_OUT) $(LIB_OBJ)

$(OUT): $(LIB_OUT)
	$(CC) -c $(CFLAGS) $(SRC) -o $(OBJ)
	$(CC) $(OBJ) $(LIB_OUT) -o $(OUT)

check: $(OUT)
	./$(OUT)

clean:
	rm -f *.o *.a $(LIB_OUT) $(OUT)
