
if WANT_JANSSON
JANSSON_INCLUDES= -I$(top_srcdir)/compat/jansson
else
JANSSON_INCLUDES=
endif

EXTRA_DIST	= example-cfg.json nomacro.pl

SUBDIRS		= compat

ALL_INCLUDES	= @PTHREAD_FLAGS@ -fno-strict-aliasing $(JANSSON_INCLUDES) -I.

bin_PROGRAMS	= cpuminer

dist_man_MANS	= cpuminer.1

cpuminer_SOURCES = \
  cpu-miner.c \
  util.c \
  uint256.cpp \
  api.c \
  sysinfos.c \
  algo-gate-api.c\
  crypto/oaes_lib.c \
  crypto/c_keccak.c \
  crypto/c_groestl.c \
  crypto/c_blake256.c \
  crypto/c_jh.c \
  crypto/c_skein.c \
  crypto/hash.c \
  crypto/aesb.c \
  crypto/magimath.cpp \
  algo/blake/sph_blake.c \
  algo/blake/blake-hash-4way.c \
  algo/blake/blake-gate.c \
  algo/blake/blake.c \
  algo/blake/blake-4way.c \
  algo/blake/sph_blake2b.c \
  algo/blake/blake2b.c \
  algo/blake/sph-blake2s.c \
  algo/blake/blake2s-hash-4way.c \
  algo/blake/blake2s.c \
  algo/blake/blake2s-gate.c \
  algo/blake/blake2s-4way.c \
  algo/blake/blakecoin-gate.c \
  algo/blake/mod_blakecoin.c \
  algo/blake/blakecoin.c \
  algo/blake/blakecoin-4way.c \
  algo/blake/decred-gate.c \
  algo/blake/decred.c \
  algo/blake/decred-4way.c \
  algo/blake/pentablake-gate.c \
  algo/blake/pentablake-4way.c \
  algo/blake/pentablake.c \
  algo/bmw/sph_bmw.c \
  algo/bmw/bmw-hash-4way.c \
  algo/bmw/bmw256.c \
  algo/cubehash/sph_cubehash.c \
  algo/cubehash/sse2/cubehash_sse2.c\
  algo/cubehash/cube-hash-2way.c \
  algo/echo/sph_echo.c \
  algo/echo/aes_ni/hash.c\
  algo/gost/sph_gost.c \
  algo/groestl/sph_groestl.c \
  algo/groestl/groestl.c \
  algo/groestl/myrgr-gate.c \
  algo/groestl/myrgr-4way.c \
  algo/groestl/myr-groestl.c \
  algo/groestl/aes_ni/hash-groestl.c \
  algo/groestl/aes_ni/hash-groestl256.c \
  algo/fugue/sph_fugue.c \
  algo/hamsi/sph_hamsi.c \
  algo/hamsi/hamsi-hash-4way.c \
  algo/haval/haval.c \
  algo/haval/haval-hash-4way.c \
  algo/luffa/sph_luffa.c \
  algo/luffa/luffa.c \
  algo/luffa/luffa_for_sse2.c \
  algo/luffa/luffa-hash-2way.c \
  algo/pluck.c \
  algo/ripemd/sph_ripemd.c \
  algo/ripemd/ripemd-hash-4way.c \
  algo/ripemd/lbry-gate.c \
  algo/ripemd/lbry.c \
  algo/ripemd/lbry-4way.c \
  algo/sha/sph_sha2.c \
  algo/sha/sph_sha2big.c \
  algo/sha/sha2-hash-4way.c \
  algo/sha/sha2.c \
  algo/sha/sha256t-gate.c \
  algo/sha/sha256t-4way.c \
  algo/sha/sha256t.c \
  algo/shabal/sph_shabal.c \
  algo/shabal/shabal-hash-4way.c \
  algo/shavite/sph_shavite.c \
  algo/shavite/sph-shavite-aesni.c \
  algo/shavite/shavite.c \
  algo/skein/sph_skein.c \
  algo/skein/skein-hash-4way.c \
  algo/skein/skein.c \
  algo/skein/skein-4way.c \
  algo/skein/skein-gate.c \
  algo/skein/skein2.c \
  algo/skein/skein2-4way.c \
  algo/skein/skein2-gate.c \
  algo/sm3/sm3.c \
  algo/sm3/sm3-hash-4way.c \
  algo/tiger/sph_tiger.c \
  algo/whirlpool/sph_whirlpool.c \
  algo/whirlpool/whirlpool-hash-4way.c \
  algo/whirlpool/whirlpool-gate.c \
  algo/whirlpool/whirlpool-4way.c \
  algo/whirlpool/whirlpool.c \
  algo/whirlpool/whirlpoolx.c \
  algo/yespower/yespower.c \
  algo/yespower/sha256.c \
  algo/yespower/yespower-opt.c

disable_flags =

if HAVE_WINDOWS
   cpuminer_SOURCES += compat/winansi.c
endif

cpuminer_LDFLAGS	= @LDFLAGS@
cpuminer_LDADD	= @LIBCURL@ @JANSSON_LIBS@ @PTHREAD_LIBS@ @WS2_LIBS@ -lssl -lcrypto -lgmp
cpuminer_CPPFLAGS = @LIBCURL_CPPFLAGS@ $(ALL_INCLUDES)
cpuminer_CFLAGS   = -Wno-pointer-sign -Wno-pointer-to-int-cast $(disable_flags)

if HAVE_WINDOWS
cpuminer_CFLAGS += -Wl,--stack,10485760
endif

if HAVE_WINDOWS
# use to profile an object
# gprof_cflags = -pg -g3
# cpuminer_LDFLAGS += -pg
# cpuminer_CFLAGS += -fno-inline-functions -static

# copy/paste from generated Makefile
common_ccflags = $(DEFS) $(ALL_INCLUDES) $(cpuminer_CPPFLAGS) $(CPPFLAGS) $(cpuminer_CFLAGS) $(CFLAGS)

endif
