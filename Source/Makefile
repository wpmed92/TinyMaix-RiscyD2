CC=riscv64-unknown-elf-gcc
CXX=riscv64-unknown-elf-g++
AR=riscv64-unknown-elf-ar
LD=riscv64-unknown-elf-ld
OBJCOPY=riscv64-unknown-elf-objcopy
CFLAGS=-O1 -march=rv32im -mabi=ilp32 -ffreestanding
LDFLAGS= -L. -ltinymaix --specs=picolibc.specs -Triscyd2.ld
INC=-I../TinyMaix/src -I../TinyMaix/include -I../Include

all: mnist_riscy.o

mnist_riscy.o: mnist_elf
	$(OBJCOPY) -O binary mnist_elf mnist_riscy.o

mnist_elf: libtinymaix.a
	$(CC) $(CFLAGS) $(INC) main.c -o mnist_elf $(LDFLAGS)

tm_model.o:
	$(CC) $(CFLAGS) $(INC) -c ../TinyMaix/src/tm_model.c

tm_layers.o:
	$(CC) $(CFLAGS) $(INC) -c ../TinyMaix/src/tm_layers.c


libtinymaix.a: tm_layers.o tm_model.o
	$(AR) rcs libtinymaix.a tm_layers.o tm_model.o

libs: libtinymaix.a

clean:
	rm -f mnist_elf mnist_elf *.o *.a *.gch #This way is cleaner than your clean