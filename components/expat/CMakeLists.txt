set(COMPONENT_ADD_INCLUDEDIRS expat/expat/lib port/include)
set(COMPONENT_SRCS "expat/expat/lib/loadlibrary.c"
                   "expat/expat/lib/xmlparse.c"
                   "expat/expat/lib/xmlrole.c"
                   "expat/expat/lib/xmltok.c"
                   "expat/expat/lib/xmltok_impl.c"
                   "expat/expat/lib/xmltok_ns.c")
register_component()

target_compile_definitions(${COMPONENT_LIB} PRIVATE HAVE_EXPAT_CONFIG_H)
target_compile_definitions(${COMPONENT_LIB} PRIVATE HAVE_GETRANDOM)

# Temporary suppress "fallthrough" warnings until they are fixed in expat repo
if(GCC_NOT_5_2_0)
    target_compile_options(${COMPONENT_LIB} PRIVATE -Wno-implicit-fallthrough)
endif()