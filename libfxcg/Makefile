CC=sh3eb-elf-gcc
AS=sh3eb-elf-as
AR=~/casio-gcc/bin/sh3eb-elf-gcc-ar
CFLAGS=-c -mhitachi -ffunction-sections -fdata-sections -m4a-nofpu -mb -Os -nostdlib -Wall -Lr -I../include -flto -fuse-linker-plugin
LDFLAGS= $(CFLAGS) -Wl,-static
ARFLAGS=rs
VPATH=syscalls
SHSOURCES=$(wildcard syscalls/*.S) $(wildcard misc/*.S)
CSOURCES=$(wildcard misc/*.c)
#CXXSOURCES=$(wildcard misc/*.cpp)
OBJECTS=$(SHSOURCES:.S=.o) $(CSOURCES:.c=.o) $(CXXSOURCES:.cpp=.o)
LIBRARY=../lib/libfxcg.a

all: $(SOURCES) $(LIBRARY)
	
$(LIBRARY): $(OBJECTS)
	$(AR) $(ARFLAGS) $@ $(OBJECTS) 

.S.o:
	$(CC) $(CFLAGS) $< -o $@

.c.o: 
	$(CC) $(CFLAGS) $< -o $@

.cpp.o:
	$(CC) $(CFLAGS) $< -o $@

clean:
	rm $(OBJECTS) $(LIBRARY)

