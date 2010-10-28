MAKE = make
CFLAGS ?= -g -Wall -O2
CC ?= gcc
OBJS = driver_comm.o spidermonkey.o spidermonkey_drv.o
ERLANG_ROOT := $(shell erl -eval 'io:format("~s", [code:root_dir()])' -s init stop -noshell)
ERL_INC_DIR = $(ERLANG_ROOT)/usr/include
LDFLAGS = -ljs -lerts -L$(ERLANG_ROOT)/usr/lib

all: $(OBJS)
	$(CC) $(LDFLAGS) -shared -o erlang_js_drv.so $(OBJS)


%.o: %.c
	$(CC) $(CFLAGS) $(LDFLAGS) -I $(ERL_INC_DIR) -DXP_UNIX -o $@ -c $<

clean:
	rm -f *~ *.o *.so
