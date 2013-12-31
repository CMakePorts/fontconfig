set(sub_dir_name src)

set( fontconfig_SRCS
    fcarch.c
    fcatomic.c
    fcblanks.c
    fccache.c
    fccfg.c
    fccharset.c
    fccompat.c
    fcdbg.c
    fcdefault.c
    fcdir.c
    fcformat.c
    fcfreetype.c
    fcfs.c
    fchash.c
    fcinit.c
    fclang.c
    fclist.c
    fcmatch.c
    fcmatrix.c
    fcname.c
    fcobjs.c
    fcpat.c
    fcserialize.c
    fcstat.c
    fcstr.c
    fcxml.c
    ftglue.c
)

include_directories(
${CMAKE_CURRENT_BINARY_DIR}
${CMAKE_CURRENT_BINARY_DIR}/../fc-lang
)

if(MSVC)
add_definitions( -DWINPOSIX_EXPORT= -DPIC )
set( fontconfig_SRCS ${fontconfig_SRCS} dirent.c unistd.c mmap.c )
endif(MSVC)

add_library( fontconfig SHARED ${fontconfig_SRCS} )
set_target_properties(fontconfig PROPERTIES OUTPUT_NAME fontconfig )

target_link_libraries( fontconfig ${FREETYPE_LIBRARIES})
target_link_libraries( fontconfig ${EXPAT_LIBRARY} )

install( TARGETS fontconfig RUNTIME DESTINATION bin LIBRARY DESTINATION lib ARCHIVE DESTINATION lib )

