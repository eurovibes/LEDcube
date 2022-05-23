PROJECT = LEDcube
BUILD_DIR = bin

SHARED_DIR =
CFILES = main.c
#AFILES += *.S

# TODO - you will need to edit these two lines!
DEVICE=stm32f030f4p6
OOCD_FILE = board/bluepill.cfg

# You shouldn't have to edit anything below here.
VPATH += $(SHARED_DIR)
INCLUDES += $(patsubst %,-I%, . $(SHARED_DIR))
OPENCM3_DIR=libopencm3

build: lib all

lib:
	$(Q)if [ ! "`ls -A $(OPENCM3_DIR)`" ] ; then \
		printf "######## ERROR ########\n"; \
		printf "\tlibopencm3 is not initialized.\n"; \
		printf "\tPlease run:\n"; \
		printf "\t$$ git submodule init\n"; \
		printf "\t$$ git submodule update\n"; \
		printf "\tbefore running make.\n"; \
		printf "######## ERROR ########\n"; \
		exit 1; \
	fi
	$(Q)$(MAKE) -C $(OPENCM3_DIR)

include $(OPENCM3_DIR)/mk/genlink-config.mk
include rules.mk
include $(OPENCM3_DIR)/mk/genlink-rules.mk

.PHONY: build lib
