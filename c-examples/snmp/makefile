# c-examples/snmp/makefile
#
# $Header: /usr/app/odstb/CVS/snacc/c-examples/snmp/makefile,v 1.6 1995/07/27 09:57:38 rj Exp $
# $Log: makefile,v $
# Revision 1.6  1995/07/27 09:57:38  rj
# rfc1155-smi.asn1, rfc1157-snmp.asn1 and rfc1213-mib2.asn1 renamed from 1155-smi.asn1, 1157-snmp.asn1 and 1213-mib2.asn1 to accomodate to snacc's new file name generation scheme.
#
# Revision 1.5  1995/07/24  20:48:27  rj
# `cd && make' instead of `cd; make'.
#
# changed `_' to `-' in file names.
#
# Revision 1.4  1995/02/20  11:52:11  rj
# build snacc if it doesn't exist.
#
# Revision 1.3  1995/02/13  15:05:48  rj
# augment CPPFLAGS, not overwrite.
# we need the compiler for the dependencies, so make it if it doesn't yet exist.
#
# Revision 1.2  1994/08/31  23:25:46  rj
# print a less irritating usage.
#
# Revision 1.1  1994/08/31  08:46:34  rj
# first check-in. for a list of changes to the snacc-1.1 distribution please refer to the ChangeLog.
#

#include ../../makehead

TOP		= /usr

ASN1_SRC_DIR	= $(TOP)/include/snacc/asn1

ASN1_C_LIB_DIR	= $(TOP)/lib
ASN1_C_INC_DIR	= $(TOP)/include/snacc/c
ASN1_C_LIB	= $(ASN1_C_LIB_DIR)/libasn1csbuf.a

COMPILERDIR	= $(TOP)/bin
SNACC		= $(COMPILERDIR)/snacc

CPPFLAGS	+= -g -I$(TOP) -I$(ASN1_C_INC_DIR) -DUSE_SBUF

ASN1FILES = \
	$(ASN1_SPEC_DIR)/rfc1155-smi.asn1	\
	$(ASN1_SPEC_DIR)/rfc1157-snmp.asn1	\
	$(ASN1_SPEC_DIR)/rfc1213-mib2.asn1

ASN1HFILES = \
	rfc1155-smi.h	\
	rfc1213-mib2.h	\
	rfc1157-snmp.h

ASN1CFILES = \
	rfc1155-smi.c	\
	rfc1213-mib2.c	\
	rfc1157-snmp.c

DISTFILES = \
	README		\
	makefile	\

#-------------------------------------------------------------------------------

default::	warning

warning::
		@echo ''
		@echo 'read the README and enter `$(MAKE) fail` to test for yourself'
		@echo ''

fail::		$(ASN1HFILES) $(ASN1CFILES)
		$(CC) $(CPPFLAGS) $(CFLAGS) -c $(ASN1CFILES)

$(ASN1HFILES)	\
$(ASN1CFILES):	$(SNACC) $(ASN1FILES)
		$(REASON)
		$(SNACC) -P $(ASN1FILES) > snacc.output~
		mv snacc.output~ snacc.output

$(SNACC):
		cd $(@D) && $(MAKE) $(@F)

check::
		@echo "the purpose of this directories' contents is to show deficiencies."
		@echo "if you want to exercise 'em, make the phony target "'`'"fail'"

clean::
		$(RM) *.o *~ .emacs* core $(ASN1HFILES) $(ASN1CFILES) snacc.output

depend::	$(SNACC)

#include ../../maketail
