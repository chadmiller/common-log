CFLAGS := -std=c99 -pipe -g -MMD -W -Wall

.PHONY : clean

common-log-parse : common-log.tab.o common-log.yy.o buf.o
	$(CC) $^ -o $@ -ll -ly

common-log.tab.o common-log.yy.o : common-log.tab.h common-log.yy.h

common-log.yy.c common-log.yy.h :	common-log.l common-log.tab.c common-log.tab.h
	/usr/local/bin/flex common-log.l

common-log.tab.c common-log.tab.h : common-log.y
	/usr/local/bin/bison --locations --defines=common-log.tab.h common-log.y

clean :
	rm -f common-log-parse *.o common-log.tab.c common-log.tab.h common-log.yy.c common-log.yy.h *.d

-include *.d
