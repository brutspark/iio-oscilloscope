# Copyright 2018 Analog Devices, Inc.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 3, or (at your option)
#  any later version.
# 
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
# 
#  You should have received a copy of the GNU General Public License
#  along with GNU Radio; see the file COPYING.  If not, write to
#  the Free Software Foundation, Inc., 51 Franklin Street,
#  Boston, MA 02110-1301, USA.

set(PLUGINS fmcomms1 fmcomms2 fmcomms5 fmcomms6
	fmcomms11 ad9371 adrv9009 adrv9009_adv
	fmcomms2_adv ad9371_adv ad6676 pr_config
	fmcadc3 daq2 ad9739a AD5628_1 AD7303 cn0357
	motor_control dmm debug)

set(PLUGIN_GLADE_FILES "")

foreach(plugin ${PLUGINS})

	add_library(${plugin} ${plugin}.c)
	target_link_libraries(${plugin} LINK_PRIVATE osc)

	set_target_properties(${plugin} PROPERTIES
		PREFIX ""
	)

endforeach()

install(TARGETS ${PLUGINS}
	LIBRARY DESTINATION ${PLIB_DEST}
)
