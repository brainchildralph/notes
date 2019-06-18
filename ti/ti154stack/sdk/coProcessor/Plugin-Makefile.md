


```

buildname=ti154stack
currdir=$(realpath $(shell pwd))
BUILDROOTDIR=$(realpath $(currdir)/../../..)
#bbb_BIN_DIR=/work/bitbucket/work-brainchild/buildroot/beaglebone/output/beaglebone/buildroot/output/host/bin
bbb_BIN_DIR=$(BUILDROOTDIR)/output/host/bin
bbb_PREFIX=${bbb_BIN_DIR}/arm-buildroot-linux-gnueabihf-
bbb_TI_PROC_SDK_DIR=$(realpath $(currdir))
bbb_ARCH=bbb
bbb_makeflags=
bbb_makeflags+=ARCH=$(bbb_ARCH)
bbb_makeflags+=bbb_TI_PROC_SDK_DIR=$(bbb_TI_PROC_SDK_DIR)
bbb_makeflags+=bb_BIN_DIR=$(bbb_BIN_DIR)
bbb_makeflags+=bbb_PREFIX=$(bbb_PREFIX)
bbb_components=common nv api
bbb_examples=collector
bbb_examples_bin=$(foreach _x,$(bbb_examples),$(currdir)/example/$(_x)/bbb_$(_x))

define create_all_components_rules
  $(foreach _x,$(bbb_components),$(eval $(call create_component_rules,$(_x))))
endef
define create_component_rules
make_component_$(1): 
          @make -C $(bbb_TI_PROC_SDK_DIR)/components/$(1) $(bbb_makeflags)
clean_component_$(1): 
          @make -C $(bbb_TI_PROC_SDK_DIR)/components/$(1) clean $(bbb_makeflags)
endef

define create_all_examples_rules
  $(foreach _x,$(bbb_examples),$(eval $(call create_example_rules,$(_x))))
endef
define create_example_rules
make_example_$(1): 
          @make -C $(bbb_TI_PROC_SDK_DIR)/example/$(1) $(bbb_makeflags)
clean_example_$(1): 
          @make -C $(bbb_TI_PROC_SDK_DIR)/example/$(1) clean $(bbb_makeflags)
endef

all: $(foreach _x,$(bbb_components),make_component_$(_x)) $(foreach _x,$(bbb_examples),make_example_$(_x))

clean: $(foreach _x,$(bbb_components),clean_component_$(_x)) $(foreach _x,$(bbb_examples),clean_example_$(_x))

install: 
#         @echo $(bbb_examples_bin)
#install: $(DESTDIR)/$(prefix)/bin
#         @cp -a $(TARGETOUTPUTDIR)/bd_svr  $(DESTDIR)/$(prefix)/bin
#$(DESTDIR)/$(prefix)/bin:;@mkdir -p $@

test: make_component_common

$(call create_all_components_rules)
$(call create_all_examples_rules)

```
