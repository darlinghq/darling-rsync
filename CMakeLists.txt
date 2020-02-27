project(rsync)

add_definitions(-DHAVE_CONFIG_H)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}
	${CMAKE_CURRENT_SOURCE_DIR}/rsync
	${CMAKE_CURRENT_SOURCE_DIR}/rsync/popt
)

set(rsync_sources
	rsync/receiver.c
	rsync/cleanup.c
	rsync/token.c
	rsync/options.c
	rsync/socket.c
	rsync/syscall.c
	rsync/progress.c
	rsync/sender.c
	rsync/flist.c
	rsync/hlink.c
	rsync/log.c
	rsync/generator.c
	rsync/pipe.c
	rsync/fileio.c
	rsync/util.c
	rsync/rsync.c
	rsync/match.c
	rsync/chmod.c
	rsync/checksum.c
	rsync/exclude.c
	rsync/backup.c
	rsync/uidlist.c
	rsync/clientname.c
	rsync/main.c
	rsync/compat.c
	rsync/io.c
	rsync/popt/popthelp.c
	rsync/popt/findme.c
	rsync/popt/poptconfig.c
	rsync/popt/popt.c
	rsync/popt/poptparse.c
	rsync/batch.c
	rsync/lib/mdfour.c
	rsync/lib/pool_alloc.c
	rsync/lib/compat.c
	rsync/lib/permstring.c
	rsync/lib/wildmatch.c
	rsync/params.c
	rsync/loadparm.c
	rsync/clientserver.c
	rsync/access.c
	rsync/connection.c
	rsync/authenticate.c
)

add_darling_executable(rsync ${rsync_sources})
target_link_libraries(rsync z)

install(TARGETS rsync DESTINATION libexec/darling/usr/bin)
install(FILES rsync/rsync.1 DESTINATION libexec/darling/usr/share/man/man1)
