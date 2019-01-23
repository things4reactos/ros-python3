#Disable for test build only
remove_definitions(-Werror)
add_definitions(-DPy_DEBUG)

#INCLUDES
include_directories(${REACTOS_SOURCE_DIR}/sdk/include/psdk)
#use ReactOS system lybrary for zlib instead of Python's
#include_directories (${REACTOS_SOURCE_DIR}/sdk/include/reactos/libs/zlib)

include_directories (Modules/zlib)

include_directories(Include)
include_directories(PC)



##########################################################################
# Modules
list(APPEND MOD_SOURCES
    Modules/_threadmodule.c  
    Modules/signalmodule.c  
    Modules/errnomodule.c 
#    Modules/pwdmodule.c
    Modules/_sre.c
    Modules/_codecsmodule.c
    Modules/_weakref.c
    Modules/_functoolsmodule.c  
    Modules/_operator.c
    Modules/_collectionsmodule.c
    Modules/itertoolsmodule.c
    Modules/atexitmodule.c
    Modules/_stat.c
    Modules/_localemodule.c
    Modules/_io/_iomodule.c
    Modules/_io/iobase.c
    Modules/_io/fileio.c 
    Modules/_io/bytesio.c
    Modules/_io/bufferedio.c
    Modules/_io/textio.c
    Modules/_io/stringio.c 
    Modules/zipimport.c
    Modules/faulthandler.c 
    Modules/_tracemalloc.c 
    Modules/hashtable.c  
    Modules/symtablemodule.c  
    Modules/xxsubtype.c
)

#Build-INs
list(APPEND MOD_BUILDIN
    Modules/arraymodule.c
    Modules/audioop.c
    Modules/binascii.c
    Modules/cmathmodule.c
    Modules/mathmodule.c
    Modules/_math.c
    Modules/md5module.c
    Modules/sha1module.c
    Modules/sha256module.c
    Modules/sha512module.c
    Modules/timemodule.c
    Modules/_winapi.c
    Modules/_randommodule.c
    Modules/_bisectmodule.c
    Modules/_heapqmodule.c
    Modules/_lsprof.c
    Modules/rotatingtree.c
    Modules/mmapmodule.c
    Modules/parsermodule.c
    Modules/_struct.c
    Modules/_datetimemodule.c
    PC/winreg.c
    Modules/_json.c
    #Modules/zlibmodule.c
    Modules/cjkcodecs/multibytecodec.c
    Modules/cjkcodecs/_codecs_cn.c
    Modules/cjkcodecs/_codecs_hk.c
    Modules/cjkcodecs/_codecs_iso2022.c
    Modules/cjkcodecs/_codecs_jp.c
    Modules/cjkcodecs/_codecs_kr.c
    Modules/cjkcodecs/_codecs_tw.c
#    Modules/_pickle.c
    Modules/_opcode.c
    Modules/_csv.c
)

list(APPEND MODULE_SOURCES
    PC/msvcrtmodule.c
    PC/config.c
    PC/getpathp.c
    Modules/main.c
    Modules/gcmodule.c
)

##########################################################################
# Parser
list(APPEND PSRCS
    Parser/acceler.c
    Parser/grammar1.c
    Parser/listnode.c 
    Parser/node.c 
    Parser/parser.c 
    Parser/bitset.c 
    Parser/metagrammar.c 
    Parser/firstsets.c 
    Parser/grammar.c 
    Parser/pgen.c
)

list(APPEND PARSER_SORCES
    ${PSRCS} 
    Parser/myreadline.c 
    Parser/parsetok.c 
    Parser/tokenizer.c
)

list(APPEND PGSRCS
    Objects/obmalloc.c 
	Python/dynamic_annotations.c 
	Python/mysnprintf.c 
	Python/pyctype.c 
	Parser/tokenizer_pgen.c 
    Parser/printgrammar.c 
	Parser/parsetok_pgen.c 
	Parser/pgenmain.c
)

list(APPEND PARSER_HEADERS
    Parser/parser.h 
    Include/parsetok.h 
	Parser/tokenizer.h

)
##########################################################################
#  PYTHON
list(APPEND PYTHON_SORCES
    Python/_warnings.c
    Python/Python-ast.c
    Python/asdl.c
    Python/ast.c
    Python/bltinmodule.c
    Python/ceval.c
    Python/compile.c
    Python/codecs.c
    Python/dynamic_annotations.c
    Python/errors.c
#    Python/frozenmain.c
    Python/future.c
    Python/getargs.c
    Python/getcompiler.c
    Python/getcopyright.c
    Python/getplatform.c
    Python/getversion.c
    Python/graminit.c
    Python/import.c
    Python/importdl.c
    Python/marshal.c
    Python/modsupport.c
    Python/mystrtoul.c
    Python/mysnprintf.c
    Python/peephole.c
    Python/pyarena.c
    Python/pyctype.c
    Python/pyfpe.c
    Python/pyhash.c
    Python/pymath.c
    Python/pystate.c
    Python/pythonrun.c
    Python/pytime.c
    Python/random.c
    Python/structmember.c
    Python/symtable.c
    Python/sysmodule.c
    Python/traceback.c
    Python/getopt.c
    Python/pystrcmp.c
    Python/pystrtod.c
    Python/dtoa.c
    Python/formatter_unicode.c
    Python/fileutils.c
#    Python/dynload_shlib.c
    Python/dynload_win.c
    Python/thread.c
)

##########################################################################
# LIBRARY
list(APPEND OBJECTS_SOURCES
    Objects/abstract.c
    Objects/accu.c
    Objects/boolobject.c
    Objects/bytes_methods.c
    Objects/bytearrayobject.c
    Objects/bytesobject.c
    Objects/cellobject.c
    Objects/classobject.c
    Objects/codeobject.c
    Objects/complexobject.c
    Objects/descrobject.c
    Objects/enumobject.c
    Objects/exceptions.c
    Objects/genobject.c
    Objects/fileobject.c
    Objects/floatobject.c
    Objects/frameobject.c
    Objects/funcobject.c
    Objects/iterobject.c
    Objects/listobject.c
    Objects/longobject.c
    Objects/dictobject.c
    Objects/memoryobject.c
    Objects/methodobject.c
    Objects/moduleobject.c
    Objects/namespaceobject.c
    Objects/object.c
    Objects/obmalloc.c
    Objects/capsule.c
    Objects/rangeobject.c
    Objects/setobject.c
    Objects/sliceobject.c
    Objects/structseq.c
    Objects/tupleobject.c
    Objects/typeobject.c
    Objects/unicodeobject.c
    Objects/unicodectype.c
    Objects/weakrefobject.c
    PC/errmap.h
)

##########################################################################
# objects that get linked into the Python library
list(APPEND LIBRARY_SOURCES
    Modules/getbuildinfo.c
    ${PARSER_SORCES}
    ${OBJECTS_SOURCES}
    ${PYTHON_SORCES}
    ${MODULE_SOURCES}
    ${MOD_SOURCES}
    ${MOD_BUILDIN}
    Python/frozen.c
)
		
		
##########################################################################
# Python building



add_library(python3 SHARED
#    PC/python3dll.c
    Modules/posixmodule.c 
    PC/dl_nt.c
    #Modules/python.c
    ${LIBRARY_SOURCES}
    PC/python3.def
    PC/python34stub.def
)

set_module_type(python3 win32dll UNICODE)

add_importlibs(python3 msvcrt advapi32 user32 shell32 shlwapi kernel32)



#set_target_properties(
#    python3 PROPERTIES 
#        COMPILE_FLAGS 
#            "-Werror=implicit-function-declaration"
#)

add_cd_file(TARGET python3 DESTINATION reactos/system32 FOR all)
