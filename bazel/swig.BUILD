licenses(["restricted"])  # GPLv3

exports_files(["LICENSE"])

config_setting(
    name = "on_windows",
    constraint_values = ["@platforms//os:windows"],
)

cc_binary(
    name = "swig",
    srcs = [
        "Source/Include/swigconfig.h",
        "Source/DOH/dohint.h",
        "Source/DOH/doh.h",
        "Source/Swig/swigfile.h",
        "Source/Swig/swigtree.h",
        "Source/Swig/swig.h",
        "Source/Swig/swigparm.h",
        "Source/Swig/swigwrap.h",
        "Source/Swig/swigscan.h",
        "Source/Swig/swigopt.h",
        "Source/Include/swigwarn.h",
        "Source/CParse/parser.h",
        "Source/CParse/cparse.h",
        "Source/Doxygen/doxycommands.h",
        "Source/Doxygen/doxyentity.h",
        "Source/Doxygen/javadoc.h",
        "Source/Doxygen/doxytranslator.h",
        "Source/Doxygen/doxyparser.h",
        "Source/Doxygen/pydoc.h",
        "Source/Modules/swigmod.h",
        "Source/Preprocessor/preprocessor.h",
        "Source/DOH/list.c",
        "Source/DOH/memory.c",
        "Source/DOH/base.c",
        "Source/DOH/string.c",
        "Source/DOH/hash.c",
        "Source/DOH/fio.c",
        "Source/DOH/void.c",
        "Source/DOH/file.c",
        "Source/Swig/scanner.c",
        "Source/Swig/fragment.c",
        "Source/Swig/typesys.c",
        "Source/Swig/naming.c",
        "Source/Swig/parms.c",
        "Source/Swig/deprecate.c",
        "Source/Swig/extend.c",
        "Source/Swig/typemap.c",
        "Source/Swig/error.c",
        "Source/Swig/wrapfunc.c",
        "Source/Swig/symbol.c",
        "Source/Swig/stype.c",
        "Source/Swig/cwrap.c",
        "Source/Swig/include.c",
        "Source/Swig/typeobj.c",
        "Source/Swig/misc.c",
        "Source/Swig/getopt.c",
        "Source/Swig/tree.c",
        "Source/CParse/templ.c",
        "Source/CParse/util.c",
        "Source/CParse/cscanner.c",
        "Source/CParse/parser.c",
        "Source/Preprocessor/cpp.c",
        "Source/Preprocessor/expr.c",
        "Source/Doxygen/doxytranslator.cxx",
        "Source/Doxygen/javadoc.cxx",
        "Source/Doxygen/doxyparser.cxx",
        "Source/Doxygen/doxyentity.cxx",
        "Source/Doxygen/pydoc.cxx",
        "Source/Modules/nested.cxx",
        "Source/Modules/python.cxx",
        "Source/Modules/ruby.cxx",
        "Source/Modules/main.cxx",
        "Source/Modules/lang.cxx",
        "Source/Modules/lua.cxx",
        "Source/Modules/mzscheme.cxx",
        "Source/Modules/tcl8.cxx",
        "Source/Modules/xml.cxx",
        "Source/Modules/javascript.cxx",
        "Source/Modules/directors.cxx",
        "Source/Modules/allocate.cxx",
        "Source/Modules/interface.cxx",
        "Source/Modules/java.cxx",
        "Source/Modules/emit.cxx",
        "Source/Modules/swigmain.cxx",
        "Source/Modules/go.cxx",
        "Source/Modules/csharp.cxx",
        "Source/Modules/d.cxx",
        "Source/Modules/typepass.cxx",
        "Source/Modules/contract.cxx",
        "Source/Modules/ocaml.cxx",
        "Source/Modules/overload.cxx",
        "Source/Modules/perl5.cxx",
        "Source/Modules/r.cxx",
        "Source/Modules/octave.cxx",
        "Source/Modules/utils.cxx",
        "Source/Modules/guile.cxx",
        "Source/Modules/scilab.cxx",
        "Source/Modules/php.cxx",
    ],
    copts = ["$(STACK_FRAME_UNLIMITED)"] + select({
        "on_windows": [],
        "//conditions:default": [
            "-Wno-parentheses",
            "-Wno-unused-variable",
            "-fexceptions",
        ],
    }),
    data = [":templates"],
    includes = [
        "Source/CParse",
        "Source/DOH",
        "Source/Doxygen",
        "Source/Include",
        "Source/Modules",
        "Source/Preprocessor",
        "Source/Swig",
    ],
    output_licenses = ["unencumbered"],
    visibility = ["//visibility:public"],
    deps = ["@pcre2//:pcre2"],
)

filegroup(
    name = "templates",
    srcs = glob([
        'Lib/*',
        'Lib/python/*',
        'Lib/std/*',
        'Lib/java/*',
        'Lib/typemaps/*'
    ]),
    licenses = ["notice"],  # simple notice license for Lib/
    path = "Lib",
    visibility = ["//visibility:public"],
)

genrule(
    name = "swigconfig",
    outs = ["Source/Include/swigconfig.h"],
    cmd = "cat <<EOF >$@\n" +
          "#define HAVE_BOOL\n" +
          "#define HAVE_PCRE\n" +
          "#define HAVE_POPEN\n" +
          "#define PACKAGE_BUGREPORT \"http://www.swig.org\"\n" +
          "#define PACKAGE_VERSION \"4.1.1\"\n" +
          "#define STDC_HEADERS\n" +
          "#define SWIG_CXX \"bazel4lyfe\"\n" +
          "#define SWIG_LIB \"external/swig/Lib\"\n" +
          "#define SWIG_LIB_WIN_UNIX \"\"\n" +
          "#define SWIG_PLATFORM \"bazel4lyfe\"\n" +
          "EOF",
)
