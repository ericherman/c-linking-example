# Makefile
# Copyright (C) 2013, 2016, 2018 Eric Herman <eric@freesa.org>
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

LIB_SRC=ctest1.c ctest2.c
LIB_OBJ=$(LIB_SRC:.c=.o)
SO_OBJS=ctest1.o ctest2.o
SO_NAME=libctest.so

INCLUDES=-I.
SRC=prog.c
OBJ=prog.o
OUT=prog

CFLAGS=-Wall
LDFLAGS=-L.
LDADD=-lctest
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
	$(CC) $(OBJ) $(LDFLAGS) -o $(OUT) $(LDADD)

check: $(OUT)
	LD_LIBRARY_PATH=. ./$(OUT)

clean:
	rm -f *.o *.a *.so  $(SO_NAME).* $(OUT)
