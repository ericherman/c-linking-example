LIB_SRC=ctest1.c ctest2.c
LIB_OBJ=$(LIB_SRC:.c=.o)
LIB_OUT=libctest.a

INCLUDES=-I.
SRC=prog.c
OBJ=prog.o
OUT=prog

CFLAGS=-Wall
LDFLAGS=-L. -lctest
CC=gcc

default: $(OUT)

.c.o:
	$(CC) -c $(CFLAGS) $< -o $@

$(LIB_OUT): $(LIB_OBJ)
	ar -cvsq $(LIB_OUT) $(LIB_OBJ)
	# ranlib $(LIB_OUT) # Ranlib is now embedded into the "ar" command.

$(OUT): $(LIB_OUT)
	$(CC) -c $(INCLUDES) $(CFLAGS) $(SRC) -o $(OBJ)
	$(CC) $(OBJ) $(LDFLAGS) -o $(OUT)

check: $(OUT)
	./$(OUT)

clean:
	rm -f *.o *.a $(LIB_OUT) $(OUT)
