# Makefile
# Copyright (C) 2013, 2018 Eric Herman <eric@freesa.org>
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
#	https://www.gnu.org/licenses/lgpl-2.1.txt

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
