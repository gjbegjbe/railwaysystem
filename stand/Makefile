# This is the makefile file
all:	rs_server rs_client clean

CC=gcc
CFLAGS= -I /usr/include/mysql -L /usr/lib/mysql -l mysqlclient -Wall
DFLAGS= -lncursesw

rs_server: rs_server.o rs_mq.o rs_dbm.o
	${CC} ${CFLAGS} rs_server.o rs_mq.o rs_dbm.o -o rs_server
rs_client: rs_client.o rs_ui.o rs_mq.o
	${CC} ${CFLAGS} ${DFLAGS} rs_client.o rs_mq.o rs_ui.o -o rs_client
rs_server.o: rs_server.c rs_mq.h rs_dbm.h
	${CC} ${CFLAGS} -c rs_server.c
rs_mq.o: rs_mq.c rs_mq.h rs_dbm.h
	${CC} ${CFLAGS} -c rs_mq.c
rs_dbm.o: rs_dbm.c rs_dbm.h
	${CC} ${CFLAGS} -c rs_dbm.c
rs_client.o: rs_client.c rs_mq.h rs_dbm.h
	${CC} ${CFLAGS} -c rs_client.c
rs_ui.o: rs_ui.c rs_mq.h rs_dbm.h
	${CC} ${CFLAGS} ${DFLAGS} -c rs_ui.c

clean:
	rm -f *.o
