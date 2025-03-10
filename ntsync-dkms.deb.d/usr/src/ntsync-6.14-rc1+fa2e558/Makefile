obj-m := ntsync.o

KVER ?= $(shell uname -r)
KDIR ?= /lib/modules/$(KVER)/build

default:
	$(MAKE) -C $(KDIR) M=$(CURDIR) modules

clean:
	$(MAKE) -C $(KDIR) M=$(CURDIR) clean
