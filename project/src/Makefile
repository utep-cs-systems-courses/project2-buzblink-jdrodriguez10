# makfile configuration
COMMON_OBJECTS  =
CPU             = msp430g2553
CFLAGS          = -mmcu=${CPU} -I../h
LDFLAGS		= -L/opt/ti/msp430_gcc/include

#switch the compiler (for the internal make rules)
CC              = msp430-elf-gcc
AS              = msp430-elf-as

all: toy.elf

#additional rules for files
toy.elf: ${COMMON_OBJECTS} toyMain.o led.o buzzer.o switches.o stateMachines.o wdInterruptHandler.o p2_interrupt_handler.o ../lib/libTimer.a
	${CC} ${CFLAGS} ${LDFLAGS} -o $@ $^

load: toy.elf
	msp430loader.sh toy.elf

clean:
	rm -f *.o *.elf

led.o: led.c led.h

swithces.o: switches.h led.h

buzzer.o: buzzer.h

stateMachines.o: switches.h led.h buzzer.h stateMachines.h

wdInterruptHandler.o: stateMachines.h

p2_interrupt_handler.o: switches.h

toyMain.o: switches.h led.h buzzer.h
