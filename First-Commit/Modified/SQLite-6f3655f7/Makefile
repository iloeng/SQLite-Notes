# Generated automatically from Makefile.in by configure.
#!/usr/make
#
# Makefile for SQLITE

# The toplevel directory of the source tree
#
TOP = /mnt/e/Projects/github/SQLite-Notes/First-Commit/Modified/SQLite-6f3655f7

# C Compiler and options for use in building executables that
# will run on the platform that is doing the build.
#
BCC = gcc -g -O2

# C Compile and options for use in building executables that 
# will run on the target platform.
#
TCC = gcc -g -O2 -DOS_UNIX=1 -DOS_WIN=0 -I. -I${TOP}/src

# Tools used to build a static library.
#
AR = ar cr
RANLIB = ranlib

# Compiler options needed for programs that use the GDBM library.
#
GDBM_FLAGS = 

# The library that programs using GDBM must link against.
#
LIBGDBM = -lgdbm 

# Compiler options needed for programs that use the readline() library.
#
READLINE_FLAGS = -DHAVE_READLINE=1 -I/usr/include/readline

# The library that programs using readline() must link against.
#
LIBREADLINE = -lreadline 

# Object files for the SQLite library.
#
LIBOBJ = build.o dbbe.o main.o parse.o tokenize.o util.o vdbe.o where.o

# This is the default Makefile target.  The objects listed here
# are what get build when you type just "make" with no arguments.
#
all:	libsqlite.a sqlite
# libtclsqlite.a tclsqlite

libsqlite.a:	$(LIBOBJ)
	$(AR) libsqlite.a $(LIBOBJ)
	$(RANLIB) libsqlite.a

sqlite:	$(TOP)/src/shell.c libsqlite.a $(TOP)/src/sqlite.h
	$(TCC) $(READLINE_FLAGS) -o sqlite $(TOP)/src/shell.c \
		libsqlite.a $(LIBGDBM) $(LIBREADLINE)

# Rules to build the LEMON compiler generator
#
lemon:	$(TOP)/tool/lemon.c $(TOP)/tool/lempar.c
	$(BCC) -o lemon $(TOP)/tool/lemon.c
	cp $(TOP)/tool/lempar.c .

# Header files used by all library source files.
#
HDR = \
   $(TOP)/src/sqlite.h  \
   $(TOP)/src/sqliteInt.h  \
   $(TOP)/src/dbbe.h  \
   $(TOP)/src/vdbe.h  \
   parse.h

build.o:	$(TOP)/src/build.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c $(TOP)/src/build.c

dbbe.o:	$(TOP)/src/dbbe.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c $(TOP)/src/dbbe.c

main.o:	$(TOP)/src/main.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c $(TOP)/src/main.c

parse.o:	parse.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c parse.c

parse.h:	parse.c

parse.c:	$(TOP)/src/parse.y lemon
	cp $(TOP)/src/parse.y .
	./lemon parse.y

tokenize.o:	$(TOP)/src/tokenize.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c $(TOP)/src/tokenize.c

util.o:	$(TOP)/src/util.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c $(TOP)/src/util.c

vdbe.o:	$(TOP)/src/vdbe.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c $(TOP)/src/vdbe.c

where.o:	$(TOP)/src/where.c $(HDR)
	$(TCC) $(GDBM_FLAGS) -c $(TOP)/src/where.c

clean:	
	rm -f *.o sqlite libsqlite.a
	rm -f lemon lempar.c parse.*
