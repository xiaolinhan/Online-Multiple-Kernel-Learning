DEBUG_FLAG=1

DEBUG=-g -Wall
RELEASE=-O2 -s

INCLUDE=-I . -I ./data -I ./loss -I./optimizer
VPATH=.:./data:./loss:./optimizer

CFLAGS=-c $(INCLUDE) -Wno-write-strings
LDFLAGS=-lpthread -lz

ifeq ($(DEBUG_FLAG),1)
	CFLAGS += $(DEBUG)
else
	CFLAGS += $(RELEASE)
endif

OBJS=Params.o basic_io.o
TARGET=SOL

all:$(TARGET)

$(TARGET):main.o $(OBJS)
	g++ $^ -o $@ $(LDFLAGS)

main.o: main.cpp optimizer/STG.h optimizer/Optimizer.h
%.o:%.cpp
	g++ $< -o $@ $(CFLAGS)

.PHONY:clean
clean:
	-rm -f *.o $(TARGET) $(addsuffix .exe, $(TARGET)) tags cscope*


