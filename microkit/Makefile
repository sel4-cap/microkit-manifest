################################################################################
# Makefile
################################################################################

#===========================================================
# Check
#===========================================================
ifndef FORCE
    EXP_INFO := sel4devkit-maaxboard-microkit-docker-dev-env 1 *
    CHK_PATH_FILE := /check.mk
    ifeq ($(wildcard ${CHK_PATH_FILE}),)
        HALT := TRUE
    else
        include ${CHK_PATH_FILE}
    endif
    ifdef HALT
        $(error Expected Environment Not Found: ${EXP_INFO})
    endif
endif

#===========================================================
# Layout
#===========================================================
TMP_PATH := tmp
OUT_PATH := out

#===========================================================
# Usage
#===========================================================
.PHONY: usage
usage: 
	@echo "usage: make <target> [FORCE=TRUE]"
	@echo ""
	@echo "<target> is one off:"
	@echo "get"
	@echo "all"
	@echo "clean"

#===========================================================
# Target
#===========================================================
.PHONY: get
get: | ${TMP_PATH}
	git -C ${TMP_PATH} clone --branch "main" "git@github.com:sel4devkit/sel4devkit-maaxboard-microkit-dev.git" sel4devkit-maaxboard-microkit-dev
	make -C ${TMP_PATH}/sel4devkit-maaxboard-microkit-dev get

.PHONY: all
all: ${OUT_PATH}/microkit-sdk-1.2.6

${TMP_PATH}:
	mkdir ${TMP_PATH}

${OUT_PATH}:
	mkdir ${OUT_PATH}

${OUT_PATH}/microkit-sdk-1.2.6: ${TMP_PATH}/sel4devkit-maaxboard-microkit-dev/out/microkit-sdk-1.2.6 | ${OUT_PATH}
	cp -r $< $@

${TMP_PATH}/sel4devkit-maaxboard-microkit-dev/out/microkit-sdk-1.2.6: | ${TMP_PATH}
	make -C ${TMP_PATH}/sel4devkit-maaxboard-microkit-dev all
	rm -rf ${TMP_PATH}
	
.PHONY: clean
clean:
	rm -rf ${TMP_PATH}
	rm -rf ${OUT_PATH}

################################################################################
# End of file
################################################################################
