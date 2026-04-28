NAME = klib
BASE_SRCS = $(shell find src/ -name "*.c")

I386_SRCS = \
  src/builtins/i386/ashldi3.S \
  src/builtins/i386/ashrdi3.S \
  src/builtins/i386/lshrdi3.S \
  src/builtins/i386/divdi3.S \
  src/builtins/i386/moddi3.S \
  src/builtins/i386/muldi3.S \
  src/builtins/i386/udivdi3.S \
  src/builtins/i386/umoddi3.S

I386_GENERIC_SRCS = \
  src/builtins/ashldi3.c \
  src/builtins/ashrdi3.c \
  src/builtins/divdi3.c \
  src/builtins/lshrdi3.c \
  src/builtins/moddi3.c \
  src/builtins/muldi3.c \
  src/builtins/udivdi3.c \
  src/builtins/umoddi3.c

RISCV64_SRCS = src/builtins/riscv/muldi3.S
RISCV64_GENERIC_SRCS = src/builtins/muldi3.c

RISCV32_SRCS = src/builtins/riscv/mulsi3.S

FILTERED_SRCS = $(filter-out \
  $(if $(filter x86,$(ISA)),$(I386_GENERIC_SRCS)) \
  $(if $(filter riscv64,$(ISA)),$(RISCV64_GENERIC_SRCS)), \
  $(BASE_SRCS))

ARCH_SRCS = \
  $(if $(filter x86,$(ISA)),$(I386_SRCS)) \
  $(if $(filter riscv64,$(ISA)),$(RISCV64_SRCS)) \
  $(if $(filter riscv32 riscv32e minirv,$(ISA)),$(RISCV32_SRCS))

SRCS = $(FILTERED_SRCS) $(ARCH_SRCS)
include $(AM_HOME)/Makefile
