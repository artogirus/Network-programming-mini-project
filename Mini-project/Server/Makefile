.SUFFIXES:
.SUFFIXES: .c .h .o

SHELL = /bin/bash

CC 	= gcc
INCLDIR = inc
OBJDIR 	= obj
SRCDIR 	= src
BINDIR 	= bin

_BIN	= server
BIN	= $(addprefix $(BINDIR)/,$(_BIN))

CFLAGS = -I$(INCLDIR) -pthread

DEPS 	= $(wildcard $(INCLDIR)/*.h)

SRCS	= $(wildcard $(SRCDIR)/*.c)

_OBJS	= $(patsubst $(SRCDIR)/%.c,%.o,$(SRCS))
OBJS	= $(addprefix $(OBJDIR)/,$(_OBJS))

SERVEROBJ	= $(OBJDIR)/server.o

.PHONY: 
.PHONY: all

all: $(BIN) 

$(BIN): $(OBJS) $(BINDIR) $(SERVEROBJ)
	$(CC) $(CFLAGS) $(OBJS) $(SERVEROBJ) -o $(BIN)

$(SERVEROBJ): server.c $(OBJDIR) $(OBJS)
	$(CC) $(CFLAGS) -c $< -o $@

$(OBJDIR)/%.o: $(SRCDIR)/%.c $(OBJDIR)
	$(CC) $(CFLAGS) -c $< -o $@

$(OBJDIR):
	mkdir -p $(OBJDIR)

$(BINDIR):
	mkdir -p $(BINDIR)

.PHONY: clean
clean:
	rm -f $(OBJDIR)/*.o *~
