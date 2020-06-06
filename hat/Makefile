#!/usr/bin/make -f

DTS := $(wildcard *.dts)
CFG := $(wildcard *.cfg)
DTSI := $(wildcard *.dtsi)
HEADERS := $(wildcard *.h)

DTBO := ${DTS:.dts=.dtbo}
EEP := ${CFG:.cfg=.eep}

TARGETS := $(DTBO) $(EEP)

all: eep
.PHONY: all clean eep dtbo 

eep: $(EEP)
dtbo: $(DTBO)

%.eep: %.cfg %.dtbo
	eepmake $< $@ $(patsubst %.cfg,%.dtbo,$<)

%.dtbo: %.dts $(DTSI) $(HEADERS)
	dtc -@ -I dts -O dtb -o $@ $<

clean:
	rm -rf $(DTBO) $(EEP)
