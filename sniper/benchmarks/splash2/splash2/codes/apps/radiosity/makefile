TARGET = RADIOSITY

OBJS = rad_main.o patchman.o elemman.o taskman.o modelman.o smallobj.o\
         display.o visible.o rad_tools.o room_model.o 
HHS = model.H parallel.H patch.H radiosity.H task.H
HS = model.h parallel.h patch.h radiosity.h task.h

GLIBDIR = ./glibdumb
GLIB    = glib.a
# look me up in man sigfpe
LIBFPE = -lfpe

CFLAGS += -I$(GLIBDIR) -I./glibps -I/usr/local/include

LOADLIBES =  $(GLIBDIR)/$(GLIB) glibps/glibps.a

x = *

$(TARGET): $(OBJS) 
	$(CC) $(CFLAGS) $(OBJS) $(LOADLIBES) $(LDFLAGS) -o $(TARGET)

.SUFFIXES:
.SUFFIXES:	.o .c .C .h .H

.H.h:	
	m4 -Ulen -Uindex ${MACROS} $*.H > $*.h

.C.c:	
	m4 -Ulen -Uindex $(MACROS) $*.C > $*.c

.c.o:	
	$(CC) -c $(CFLAGS) $*.c

.C.o:	
	m4 -Ulen -Uindex $(MACROS) $*.C > $*.c
	$(CC) -c $(CFLAGS) $*.c

$(HS): $(HHS)

radiosity.h: patch.h model.h parallel.h task.h
rad_main.c: rad_main.C $(HS)
patchman.c: patchman.C $(HS)
elemman.c: elemman.C $(HS)
taskman.c: taskman.C $(HS)
modelman.c: modelman.C $(HS)
smallobj.c: smallobj.C $(HS)
display.c: display.C $(HS)
visible.c: visible.C $(HS)
rad_tools.c: rad_tools.C $(HS)
room_model.c: room_model.C $(HS)

clean:
	$(RM) $(CS) $(ASMS) $(SS) $(OBJS) $(HS)

all: $(TARGET)
