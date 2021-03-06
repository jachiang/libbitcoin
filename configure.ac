###############################################################################
#  Copyright (c) 2014-2018 libbitcoin developers (see COPYING).
#
#         GENERATED SOURCE CODE, DO NOT EDIT EXCEPT EXPERIMENTALLY
#
###############################################################################

# Standard declarations.
#==============================================================================
# Requires Automake 1.14 or newer.

# Declare the required version of Autoconf.
AC_PREREQ([2.65])

# Process command-line arguments and perform initialization and verification.
AC_INIT([libbitcoin], [4.0.0], [eric@voskuil.org])

# Do compilation tests.
AC_LANG(C++)

# Specify the temporary directory for build tools.
AC_CONFIG_AUX_DIR([build-aux])

# Specify the directory of additional local Autoconf macros.
AC_CONFIG_MACRO_DIR([m4])

# Run macros for operation of generated Makefiles, enable non-recursive make.
# Unless [foreign] is specified standard GNU files will be required,
# specifically: AUTHORS, COPYING, INSTALL, NEWS, README and ChangeLog.
AM_INIT_AUTOMAKE([subdir-objects])

# Enable C and POSIX extensions that may be disabled on certain platforms.
AC_USE_SYSTEM_EXTENSIONS

# Enable the archiver.
AM_PROG_AR

# Initialize libtool.
LT_PREREQ(2.4.2)
LT_INIT

# Determine C++ compiler to use.
AC_PROG_CXX

# Enable shared libraries if available, and static if they don't conflict.
AC_PROG_LIBTOOL

# Enable sed for substitution.
AC_PROG_SED

# Compute the canonical host-system type variable host, including host_os.
AC_CANONICAL_HOST

# Enable silent rules option.
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

# Check for pkg-config.
PKG_PROG_PKG_CONFIG
AS_IF([test -n "$PKG_CONFIG"], [],
    [AC_MSG_ERROR([pkg-config is required but was not found.])])

AS_CASE([${enable_static}],
    [yes], [AC_SUBST([PKG_CONFIG], ["$PKG_CONFIG --static"])],
    [])

# Declare environment variables that affect the build.
#------------------------------------------------------------------------------
AC_ARG_VAR([CC], "C compiler to use, such as gcc or clang")
AC_ARG_VAR([CXX], "C++ compiler to use, such as g++ or clang++")
AC_ARG_VAR([PKG_CONFIG_PATH], "Additional directories for package discovery.")

# Check for baseline language coverage in the compiler for the C++11 standard.
#------------------------------------------------------------------------------
AX_CXX_COMPILE_STDCXX_11([noext], [mandatory])


# Process options.
#==============================================================================
# Implement --with-pkgconfigdir and output ${pkgconfigdir}.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--with-pkgconfigdir option])
AC_ARG_WITH([pkgconfigdir],
    AS_HELP_STRING([--with-pkgconfigdir=DIR],
        [Path to pkgconfig directory. @<:@default=${libdir}/pkgconfig@:>@]),
    [pkgconfigdir=$withval],
    [pkgconfigdir=${libdir}/pkgconfig])
AC_MSG_RESULT([$pkgconfigdir])
AC_SUBST([pkgconfigdir])

# Implement --with-tests and declare WITH_TESTS.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--with-tests option])
AC_ARG_WITH([tests],
    AS_HELP_STRING([--with-tests],
        [Compile with unit tests. @<:@default=yes@:>@]),
    [with_tests=$withval],
    [with_tests=yes])
AC_MSG_RESULT([$with_tests])
AM_CONDITIONAL([WITH_TESTS], [test x$with_tests != xno])

# Implement --with-examples and declare WITH_EXAMPLES.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--with-examples option])
AC_ARG_WITH([examples],
    AS_HELP_STRING([--with-examples],
        [Compile with examples. @<:@default=yes@:>@]),
    [with_examples=$withval],
    [with_examples=yes])
AC_MSG_RESULT([$with_examples])
AM_CONDITIONAL([WITH_EXAMPLES], [test x$with_examples != xno])

# Implement --with-icu and define BOOST_HAS_ICU and output ${icu}.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--with-icu option])
AC_ARG_WITH([icu],
    AS_HELP_STRING([--with-icu],
        [Compile with International Components for Unicode. @<:@default=no@:>@]),
    [with_icu=$withval],
    [with_icu=no])
AC_MSG_RESULT([$with_icu])
AS_CASE([${with_icu}], [yes], AC_DEFINE([BOOST_HAS_ICU]))
AS_CASE([${with_icu}], [yes], AC_SUBST([icu], [-DWITH_ICU]))

# Implement --with-png and output ${png}.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--with-png option])
AC_ARG_WITH([png],
    AS_HELP_STRING([--with-png],
        [Compile with Libpng support. @<:@default=no@:>@]),
    [with_png=$withval],
    [with_png=no])
AC_MSG_RESULT([$with_png])
AS_CASE([${with_png}], [yes], AC_SUBST([png], [-DWITH_PNG]))

# Implement --with-qrencode and output ${qrencode}.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--with-qrencode option])
AC_ARG_WITH([qrencode],
    AS_HELP_STRING([--with-qrencode],
        [Compile with QREncode. @<:@default=no@:>@]),
    [with_qrencode=$withval],
    [with_qrencode=no])
AC_MSG_RESULT([$with_qrencode])
AS_CASE([${with_qrencode}], [yes], AC_SUBST([qrencode], [-DWITH_QRENCODE]))

# Implement --enable-ndebug and define NDEBUG.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--enable-ndebug option])
AC_ARG_ENABLE([ndebug],
    AS_HELP_STRING([--enable-ndebug],
        [Compile without debug assertions. @<:@default=yes@:>@]),
    [enable_ndebug=$enableval],
    [enable_ndebug=yes])
AC_MSG_RESULT([$enable_ndebug])
AS_CASE([${enable_ndebug}], [yes], AC_DEFINE([NDEBUG]))

# Inherit --enable-shared and define BOOST_ALL_DYN_LINK.
#------------------------------------------------------------------------------
AS_CASE([${enable_shared}], [yes], AC_DEFINE([BOOST_ALL_DYN_LINK]))

# Implement --enable-isystem.
#------------------------------------------------------------------------------
AC_MSG_CHECKING([--enable-isystem option])
AC_ARG_ENABLE([isystem],
    AS_HELP_STRING([--enable-isystem],
        [Substitute -isystem for -I in dependencies. @<:@default=no@:>@]),
    [enable_isystem=$enableval],
    [enable_isystem=no])
AC_MSG_RESULT([$enable_isystem])


# Check dependencies.
#==============================================================================
# Require Boost of at least version 1.62.0 and output ${boost_CPPFLAGS/LDFLAGS}.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_BOOST_BASE([1.62.0],
        [AC_SUBST([boost_CPPFLAGS], [${BOOST_CPPFLAGS}])
         AC_SUBST([boost_ISYS_CPPFLAGS], [`echo ${BOOST_CPPFLAGS} | $SED s/^-I/-isystem/g | $SED s/' -I'/' -isystem'/g`])
         AC_SUBST([boost_LDFLAGS], [${BOOST_LDFLAGS}])
         AC_MSG_NOTICE([boost_CPPFLAGS : ${boost_CPPFLAGS}])
         AC_MSG_NOTICE([boost_ISYS_CPPFLAGS : ${boost_ISYS_CPPFLAGS}])
         AC_MSG_NOTICE([boost_LDFLAGS : ${boost_LDFLAGS}])],
        [AC_MSG_ERROR([Boost 1.62.0 or later is required but was not found.])])])

AS_CASE([${enable_isystem}],[yes],
    [AC_SUBST([boost_BUILD_CPPFLAGS], [${boost_ISYS_CPPFLAGS}])],
    [AC_SUBST([boost_BUILD_CPPFLAGS], [${boost_CPPFLAGS}])])

AC_MSG_NOTICE([boost_BUILD_CPPFLAGS : ${boost_BUILD_CPPFLAGS}])

AX_BOOST_CHRONO
AC_SUBST([boost_chrono_LIBS], [${BOOST_CHRONO_LIB}])
AC_MSG_NOTICE([boost_chrono_LIBS : ${boost_chrono_LIBS}])

AX_BOOST_DATE_TIME
AC_SUBST([boost_date_time_LIBS], [${BOOST_DATE_TIME_LIB}])
AC_MSG_NOTICE([boost_date_time_LIBS : ${boost_date_time_LIBS}])

AX_BOOST_FILESYSTEM
AC_SUBST([boost_filesystem_LIBS], [${BOOST_FILESYSTEM_LIB}])
AC_MSG_NOTICE([boost_filesystem_LIBS : ${boost_filesystem_LIBS}])

AX_BOOST_IOSTREAMS
AC_SUBST([boost_iostreams_LIBS], [${BOOST_IOSTREAMS_LIB}])
AC_MSG_NOTICE([boost_iostreams_LIBS : ${boost_iostreams_LIBS}])

AX_BOOST_LOCALE
AC_SUBST([boost_locale_LIBS], [${BOOST_LOCALE_LIB}])
AC_MSG_NOTICE([boost_locale_LIBS : ${boost_locale_LIBS}])

AX_BOOST_LOG_SETUP
AC_SUBST([boost_log_setup_LIBS], [${BOOST_LOG_SETUP_LIB}])
AC_MSG_NOTICE([boost_log_setup_LIBS : ${boost_log_setup_LIBS}])

AX_BOOST_LOG
AC_SUBST([boost_log_LIBS], [${BOOST_LOG_LIB}])
AC_MSG_NOTICE([boost_log_LIBS : ${boost_log_LIBS}])

AX_BOOST_PROGRAM_OPTIONS
AC_SUBST([boost_program_options_LIBS], [${BOOST_PROGRAM_OPTIONS_LIB}])
AC_MSG_NOTICE([boost_program_options_LIBS : ${boost_program_options_LIBS}])

AX_BOOST_REGEX
AC_SUBST([boost_regex_LIBS], [${BOOST_REGEX_LIB}])
AC_MSG_NOTICE([boost_regex_LIBS : ${boost_regex_LIBS}])

AX_BOOST_SYSTEM
AC_SUBST([boost_system_LIBS], [${BOOST_SYSTEM_LIB}])
AC_MSG_NOTICE([boost_system_LIBS : ${boost_system_LIBS}])

AX_BOOST_THREAD
AC_SUBST([boost_thread_LIBS], [${BOOST_THREAD_LIB}])
AC_MSG_NOTICE([boost_thread_LIBS : ${boost_thread_LIBS}])

AS_CASE([${with_tests}], [yes],
    [AX_BOOST_UNIT_TEST_FRAMEWORK
     AC_SUBST([boost_unit_test_framework_LIBS], [${BOOST_UNIT_TEST_FRAMEWORK_LIB}])
     AC_MSG_NOTICE([boost_unit_test_framework_LIBS : ${boost_unit_test_framework_LIBS}])],
    [AC_SUBST([boost_unit_test_framework_LIBS], [])])

# Require pthread if not on android and output ${pthread_CPPFLAGS/LIBS}.
#------------------------------------------------------------------------------
# Hard wired -lpthread because AX_PTHREAD does not do it.
AS_CASE([${host_os}],
    [*android*],
    [AC_SUBST([pthread_LIBS], [])],
    [AX_PTHREAD(
        [AC_SUBST([pthread_CPPFLAGS], [${PTHREAD_CPPFLAGS}])
         AC_SUBST([pthread_ISYS_CPPFLAGS], [`echo ${PTHREAD_CPPFLAGS} | $SED s/^-I/-isystem/g | $SED s/' -I'/' -isystem'/g`])
         AC_SUBST([pthread_LIBS], [-lpthread])
         AC_MSG_NOTICE([pthread_CPPFLAGS : ${pthread_CPPFLAGS}])
         AC_MSG_NOTICE([pthread_ISYS_CPPFLAGS : ${pthread_ISYS_CPPFLAGS}])],
        [AC_MSG_ERROR([pthread library is required but was not found.])])

    AS_CASE([${enable_isystem}],[yes],
        [AC_SUBST([pthread_BUILD_CPPFLAGS], [${pthread_ISYS_CPPFLAGS}])],
        [AC_SUBST([pthread_BUILD_CPPFLAGS], [${pthread_CPPFLAGS}])])

    AC_MSG_NOTICE([pthread_BUILD_CPPFLAGS : ${pthread_BUILD_CPPFLAGS}])])

AC_MSG_NOTICE([pthread_LIBS : ${pthread_LIBS}])

# Require rt if on linux if not on android and output ${rt_LIBS}.
#------------------------------------------------------------------------------

AS_CASE([${host_os}],
    [*android*],
    [AC_SUBST([rt_LIBS], [])],
    [*linux*],
    [AC_CHECK_LIB([rt], [clock_gettime],
        [AC_SUBST([rt_LIBS], [-lrt])],
        [AC_MSG_ERROR([rt library is required but was not found.])])],
    [AC_SUBST([rt_LIBS], [])])

AC_MSG_NOTICE([rt_LIBS : ${rt_LIBS}])

# Require icu-i18n of at least version 51.2 and output ${icu_i18n_CPPFLAGS/LIBS/PKG}.
#------------------------------------------------------------------------------
AS_CASE([${with_icu}], [yes],
    [PKG_CHECK_MODULES([icu_i18n], [icu-i18n >= 51.2],
        [icu_i18n_INCLUDEDIR="`$PKG_CONFIG --variable=includedir "icu-i18n >= 51.2" 2>/dev/null`"
         icu_i18n_OTHER_CFLAGS="`$PKG_CONFIG --cflags-only-other "icu-i18n >= 51.2" 2>/dev/null`"],
        [icu_i18n_INCLUDEDIR=""
         icu_i18n_OTHER_CFLAGS=""])
     AC_SUBST([icu_i18n_PKG], ['icu-i18n >= 51.2'])
     AC_SUBST([icu_i18n_CPPFLAGS], [${icu_i18n_CFLAGS}])
     AS_IF([test x${icu_i18n_INCLUDEDIR} != "x"],
        [AC_SUBST([icu_i18n_ISYS_CPPFLAGS], ["-isystem${icu_i18n_INCLUDEDIR} ${icu_i18n_OTHER_CFLAGS}"])],
        [AC_SUBST([icu_i18n_ISYS_CPPFLAGS], [${icu_i18n_OTHER_CFLAGS}])])
     AC_MSG_NOTICE([icu_i18n_CPPFLAGS : ${icu_i18n_CPPFLAGS}])
     AC_MSG_NOTICE([icu_i18n_ISYS_CPPFLAGS : ${icu_i18n_ISYS_CPPFLAGS}])
     AC_MSG_NOTICE([icu_i18n_OTHER_CFLAGS : ${icu_i18n_OTHER_CFLAGS}])
     AC_MSG_NOTICE([icu_i18n_INCLUDEDIR : ${icu_i18n_INCLUDEDIR}])
     AC_MSG_NOTICE([icu_i18n_LIBS : ${icu_i18n_LIBS}])],
    [AC_SUBST([icu_i18n_PKG], [])])

AS_CASE([${enable_isystem}],[yes],
    [AC_SUBST([icu_i18n_BUILD_CPPFLAGS], [${icu_i18n_ISYS_CPPFLAGS}])],
    [AC_SUBST([icu_i18n_BUILD_CPPFLAGS], [${icu_i18n_CPPFLAGS}])])

AC_MSG_NOTICE([icu_i18n_BUILD_CPPFLAGS : ${icu_i18n_BUILD_CPPFLAGS}])

# Require dl if on linux and output ${dl_LIBS}.
#------------------------------------------------------------------------------

AS_CASE([${host_os}],
    [*linux*],
    [AC_CHECK_LIB([dl], [dlopen],
        [AC_SUBST([dl_LIBS], [-ldl])],
        [AC_MSG_ERROR([dl library is required but was not found.])])],
    [AC_SUBST([dl_LIBS], [])])

AC_MSG_NOTICE([dl_LIBS : ${dl_LIBS}])

# Require png of at least version 1.6.29 and output ${png_CPPFLAGS/LIBS/PKG}.
#------------------------------------------------------------------------------
AS_CASE([${with_png}], [yes],
    [PKG_CHECK_MODULES([png], [libpng >= 1.6.29],
        [png_INCLUDEDIR="`$PKG_CONFIG --variable=includedir "libpng >= 1.6.29" 2>/dev/null`"
         png_OTHER_CFLAGS="`$PKG_CONFIG --cflags-only-other "libpng >= 1.6.29" 2>/dev/null`"],
        [png_INCLUDEDIR=""
         png_OTHER_CFLAGS=""])
     AC_SUBST([png_PKG], ['libpng >= 1.6.29'])
     AC_SUBST([png_CPPFLAGS], [${png_CFLAGS}])
     AS_IF([test x${png_INCLUDEDIR} != "x"],
        [AC_SUBST([png_ISYS_CPPFLAGS], ["-isystem${png_INCLUDEDIR} ${png_OTHER_CFLAGS}"])],
        [AC_SUBST([png_ISYS_CPPFLAGS], [${png_OTHER_CFLAGS}])])
     AC_MSG_NOTICE([png_CPPFLAGS : ${png_CPPFLAGS}])
     AC_MSG_NOTICE([png_ISYS_CPPFLAGS : ${png_ISYS_CPPFLAGS}])
     AC_MSG_NOTICE([png_OTHER_CFLAGS : ${png_OTHER_CFLAGS}])
     AC_MSG_NOTICE([png_INCLUDEDIR : ${png_INCLUDEDIR}])
     AC_MSG_NOTICE([png_LIBS : ${png_LIBS}])],
    [AC_SUBST([png_PKG], [])])

AS_CASE([${enable_isystem}],[yes],
    [AC_SUBST([png_BUILD_CPPFLAGS], [${png_ISYS_CPPFLAGS}])],
    [AC_SUBST([png_BUILD_CPPFLAGS], [${png_CPPFLAGS}])])

AC_MSG_NOTICE([png_BUILD_CPPFLAGS : ${png_BUILD_CPPFLAGS}])

# Require qrencode of at least version 3.4.4 and output ${qrencode_CPPFLAGS/LIBS/PKG}.
#------------------------------------------------------------------------------
AS_CASE([${with_qrencode}], [yes],
    [PKG_CHECK_MODULES([qrencode], [libqrencode >= 3.4.4],
        [qrencode_INCLUDEDIR="`$PKG_CONFIG --variable=includedir "libqrencode >= 3.4.4" 2>/dev/null`"
         qrencode_OTHER_CFLAGS="`$PKG_CONFIG --cflags-only-other "libqrencode >= 3.4.4" 2>/dev/null`"],
        [qrencode_INCLUDEDIR=""
         qrencode_OTHER_CFLAGS=""])
     AC_SUBST([qrencode_PKG], ['libqrencode >= 3.4.4'])
     AC_SUBST([qrencode_CPPFLAGS], [${qrencode_CFLAGS}])
     AS_IF([test x${qrencode_INCLUDEDIR} != "x"],
        [AC_SUBST([qrencode_ISYS_CPPFLAGS], ["-isystem${qrencode_INCLUDEDIR} ${qrencode_OTHER_CFLAGS}"])],
        [AC_SUBST([qrencode_ISYS_CPPFLAGS], [${qrencode_OTHER_CFLAGS}])])
     AC_MSG_NOTICE([qrencode_CPPFLAGS : ${qrencode_CPPFLAGS}])
     AC_MSG_NOTICE([qrencode_ISYS_CPPFLAGS : ${qrencode_ISYS_CPPFLAGS}])
     AC_MSG_NOTICE([qrencode_OTHER_CFLAGS : ${qrencode_OTHER_CFLAGS}])
     AC_MSG_NOTICE([qrencode_INCLUDEDIR : ${qrencode_INCLUDEDIR}])
     AC_MSG_NOTICE([qrencode_LIBS : ${qrencode_LIBS}])],
    [AC_SUBST([qrencode_PKG], [])])

AS_CASE([${enable_isystem}],[yes],
    [AC_SUBST([qrencode_BUILD_CPPFLAGS], [${qrencode_ISYS_CPPFLAGS}])],
    [AC_SUBST([qrencode_BUILD_CPPFLAGS], [${qrencode_CPPFLAGS}])])

AC_MSG_NOTICE([qrencode_BUILD_CPPFLAGS : ${qrencode_BUILD_CPPFLAGS}])

# Require secp256k1 of at least version 0.0.1 and output ${secp256k1_CPPFLAGS/LIBS/PKG}.
#------------------------------------------------------------------------------
PKG_CHECK_MODULES([secp256k1], [libsecp256k1 >= 0.0.1],
    [secp256k1_INCLUDEDIR="`$PKG_CONFIG --variable=includedir "libsecp256k1 >= 0.0.1" 2>/dev/null`"
     secp256k1_OTHER_CFLAGS="`$PKG_CONFIG --cflags-only-other "libsecp256k1 >= 0.0.1" 2>/dev/null`"],
    [secp256k1_INCLUDEDIR=""
     secp256k1_OTHER_CFLAGS=""])
AC_SUBST([secp256k1_PKG], ['libsecp256k1 >= 0.0.1'])
AC_SUBST([secp256k1_CPPFLAGS], [${secp256k1_CFLAGS}])
AS_IF([test x${secp256k1_INCLUDEDIR} != "x"],
    [AC_SUBST([secp256k1_ISYS_CPPFLAGS], ["-isystem${secp256k1_INCLUDEDIR} ${secp256k1_OTHER_CFLAGS}"])],
    [AC_SUBST([secp256k1_ISYS_CPPFLAGS], [${secp256k1_OTHER_CFLAGS}])])
AC_MSG_NOTICE([secp256k1_CPPFLAGS : ${secp256k1_CPPFLAGS}])
AC_MSG_NOTICE([secp256k1_ISYS_CPPFLAGS : ${secp256k1_ISYS_CPPFLAGS}])
AC_MSG_NOTICE([secp256k1_OTHER_CFLAGS : ${secp256k1_OTHER_CFLAGS}])
AC_MSG_NOTICE([secp256k1_INCLUDEDIR : ${secp256k1_INCLUDEDIR}])
AC_MSG_NOTICE([secp256k1_LIBS : ${secp256k1_LIBS}])

AS_CASE([${enable_isystem}],[yes],
    [AC_SUBST([secp256k1_BUILD_CPPFLAGS], [${secp256k1_ISYS_CPPFLAGS}])],
    [AC_SUBST([secp256k1_BUILD_CPPFLAGS], [${secp256k1_CPPFLAGS}])])

AC_MSG_NOTICE([secp256k1_BUILD_CPPFLAGS : ${secp256k1_BUILD_CPPFLAGS}])


# Set flags.
#==============================================================================
# Require c++11 for all c++ products.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-std=c++11],
        [CXXFLAGS="$CXXFLAGS -std=c++11"])])

# Warn on all stuff.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wall],
        [CFLAGS="$CFLAGS -Wall"])])

# Warn on all stuff.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wall],
        [CXXFLAGS="$CXXFLAGS -Wall"])])

# Warn on extra stuff.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wextra],
        [CFLAGS="$CFLAGS -Wextra"])])

# Warn on extra stuff.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wextra],
        [CXXFLAGS="$CXXFLAGS -Wextra"])])

# Be really annoying.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wpedantic],
        [CFLAGS="$CFLAGS -Wpedantic"],
        [AX_CHECK_COMPILE_FLAG([-pedantic],
            [CFLAGS="$CFLAGS -pedantic"])])])

# Be really annoying.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wpedantic],
        [CXXFLAGS="$CXXFLAGS -Wpedantic"],
        [AX_CHECK_COMPILE_FLAG([-pedantic],
            [CXXFLAGS="$CXXFLAGS -pedantic"])])])

# Disallow warning on style order of declarations.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wno-reorder],
        [CXXFLAGS="$CXXFLAGS -Wno-reorder"])])

# Suppress warning for incomplete field initialization.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wno-missing-field-initializers],
        [CXXFLAGS="$CXXFLAGS -Wno-missing-field-initializers"])])

# Conform to style.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wno-missing-braces],
        [CXXFLAGS="$CXXFLAGS -Wno-missing-braces"])])

# Ignore comments within comments or commenting of backslash extended lines.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wno-comment],
        [CXXFLAGS="$CXXFLAGS -Wno-comment"])])

# Conflict in stdlib under clang. Enabled in clang only.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*clang*],
    [AX_CHECK_COMPILE_FLAG([-Wno-mismatched-tags],
        [CXXFLAGS="$CXXFLAGS -Wno-mismatched-tags"])])

# Protect stack.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_LINK_FLAG([-fstack-protector],
        [LDFLAGS="$LDFLAGS -fstack-protector"])])

# Protect stack comprehensively.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_LINK_FLAG([-fstack-protector-all],
        [LDFLAGS="$LDFLAGS -fstack-protector-all"])])

# Allow use of C99 'long long' type.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*],
    [AX_CHECK_COMPILE_FLAG([-Wno-long-long],
        [CFLAGS="$CFLAGS -Wno-long-long"])])

# Limit delays and warnings. Enabled in gcc only.
#------------------------------------------------------------------------------
AS_CASE([${CC}], [*gcc*],
    [AX_CHECK_COMPILE_FLAG([-fno-var-tracking-assignments],
        [CXXFLAGS="$CXXFLAGS -fno-var-tracking-assignments"])])


# Process outputs into templates.
#==============================================================================
AC_CONFIG_FILES([Makefile libbitcoin.pc])
AC_OUTPUT
