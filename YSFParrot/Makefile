CC      = cc
CXX     = c++
CFLAGS  = -g -O3 -Wall -std=c++0x -pthread
LIBS    = -lpthread
LDFLAGS = -g

OBJECTS = Network.o Parrot.o StopWatch.o Thread.o Timer.o UDPSocket.o YSFParrot.o

all:		YSFParrot

YSFParrot:	$(OBJECTS)
		$(CXX) $(OBJECTS) $(CFLAGS) $(LIBS) -o YSFParrot

%.o: %.cpp
		$(CXX) $(CFLAGS) -c -o $@ $<

YSFParrot.o: GitVersion.h FORCE

.PHONY: GitVersion.h

FORCE:

install:
		install -m 755 YSFParrot /usr/local/bin/

clean:
		$(RM) YSFParrot *.o *.d *.bak *~ GitVersion.h
 
GitVersion.h:
ifneq ("$(wildcard ../.git/index)","")
	echo "const char *gitversion = \"$(shell git rev-parse HEAD)\";" > $@
else
	echo "const char *gitversion = \"0000000000000000000000000000000000000000\";" > $@
endif
