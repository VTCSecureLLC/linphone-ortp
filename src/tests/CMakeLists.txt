############################################################################
# CMakeLists.txt
# Copyright (C) 2014  Belledonne Communications, Grenoble France
#
############################################################################
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
#
############################################################################

if (NOT IOS)
	set(EXECUTABLES rtpsend rtprecv mrtpsend mrtprecv test_timer tevrtpsend tevrtprecv rtpsend_stupid)
	foreach(executable ${EXECUTABLES})
		apply_compile_flags(${executable}.c "CPP" "C")
		add_executable(${executable} ${executable}.c)
		target_link_libraries(${executable} ortp)
	endforeach()

	install(TARGETS ${EXECUTABLES}
		RUNTIME DESTINATION bin
		PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
	)
endif()
