# $FreeBSD$ 

.include <bsd.own.mk>

.PATH: ${.CURDIR}/../../contrib/ipfilter/netinet

KMOD=	ipl
SRCS=	mlfk_ipl.c ip_nat.c ip_frag.c ip_state.c ip_proxy.c ip_auth.c \
	ip_log.c ip_fil_freebsd.c fil.c ip_lookup.c ip_pool.c ip_htable.c \
	ip_sync.c
SRCS+=	opt_bpf.h opt_inet6.h

.if !defined(KERNBUILDDIR)
opt_bpf.h:
	echo "#define DEV_BPF 1" > ${.TARGET}

.if ${MK_INET6_SUPPORT} != "no"
opt_inet6.h:
	echo "#define INET6 1" > ${.TARGET}
.endif
.endif
CFLAGS+=  -I${.CURDIR}/../../contrib/ipfilter
CFLAGS+= -DIPFILTER=1 -DIPFILTER_LKM -DIPFILTER_LOG -DIPFILTER_LOOKUP
#
# If you don't want log functionality remove -DIPFILTER_LOG
#

.include <bsd.kmod.mk>

CWARNFLAGS.fil.c=		${NO_WSELF_ASSIGN} -Wno-unused
CWARNFLAGS.ip_auth.c=		-Wno-unused
CWARNFLAGS.ip_fil_freebsd.c=	-Wno-unused
CWARNFLAGS.ip_frag.c=		-Wno-unused
CWARNFLAGS.ip_htable.c=		-Wno-unused
CWARNFLAGS.ip_lookup.c=		${NO_WSELF_ASSIGN} -Wno-unused
CWARNFLAGS.ip_nat.c=		-Wno-unused
CWARNFLAGS.ip_pool.c=		-Wno-unused
CWARNFLAGS.ip_proxy.c=		${NO_WSELF_ASSIGN} -Wno-unused
CWARNFLAGS.ip_state.c=		-Wno-unused
CWARNFLAGS.ip_sync.c=		-Wno-unused
CWARNFLAGS+=			${CWARNFLAGS.${.IMPSRC:T}}
