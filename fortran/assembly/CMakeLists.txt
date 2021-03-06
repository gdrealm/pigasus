##########################################################################
# fem directory
##########################################################################
set(HEADER_FILES 
	${PIGASUS_DIRECTORY_TOOLS}/used_precision.mod 
	${PIGASUS_DIRECTORY_TRACELOG}/tracelog_module.mod 
	${PIGASUS_DIRECTORY_BLACKBOXES}/bbox_def.mod 
	${PIGASUS_DIRECTORY_BLACKBOXES}/bbox_modules.mod 
	${PIGASUS_DIRECTORY_GEOMETRIES}/bspline.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/bsp.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/crv.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/vol.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/iga.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/srf.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/geometries_def.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/geometrie_module.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/geometries_module.mod
	${PIGASUS_DIRECTORY_GEOMETRIES}/geometry_tools.mod
	${PIGASUS_DIRECTORY_CONNECTIVITIES}/connectivities_def.mod
	${PIGASUS_DIRECTORY_CONNECTIVITIES}/connectivities.mod
	${PIGASUS_DIRECTORY_CONNECTIVITIES}/connectivity_module.mod
	${PIGASUS_DIRECTORY_GRIDS}/grids_def.mod
	${PIGASUS_DIRECTORY_GRIDS}/elements_module.mod
	${PIGASUS_DIRECTORY_GRIDS}/elements_tensor_module.mod
	${PIGASUS_DIRECTORY_GRIDS}/grids.mod
	${PIGASUS_DIRECTORY_SPM}/spm_def.mod
	${PIGASUS_DIRECTORY_SPM}/spm.mod
	${PIGASUS_DIRECTORY_FEM}/fem_def.mod)	
include_directories(
	${PIGASUS_DIRECTORY_TOOLS}
	${PIGASUS_DIRECTORY_TRACELOG}
	${PIGASUS_DIRECTORY_BLACKBOXES}
	${PIGASUS_DIRECTORY_GEOMETRIES}
	${PIGASUS_DIRECTORY_CONNECTIVITIES}
	${PIGASUS_DIRECTORY_GRIDS}
	${PIGASUS_DIRECTORY_SPM}
	${PIGASUS_DIRECTORY_FEM})

set(assembly_files 
	assembly_def.F90 
	mass.F90 
	stiffness.F90 
	advection.F90 
	second_deriv.F90 
	operators.F90 
	l2_projector.F90 
	l2_projector_grad.F90 
	l2_projector_curl.F90 
	projectors.F90 
	identity_field.F90 
	grad_field.F90 
	curl_field.F90 
	second_deriv_field.F90 
	grad_s_field.F90 
	second_deriv_s_field.F90 
	hessian_field.F90 
	fields_operators.F90
	l2_norm.F90 
	H1_norm.F90 
	norms.F90
	assembly_tools.F90 
	assembly.F90 
	fields_tools.F90)
set(assembly_mods 
	advection_module.mod 
	l2_norm_module.mod 
	assembly_def.mod 
	l2_projector_curl_module.mod 
	assembly_module.mod 
	l2_projector_grad_module.mod 
	assembly_tools.mod 
	l2_projector_module.mod 
	curl_field_module.mod 
	mass_module.mod 
	fields_operators_module.mod 
	norms_module.mod 
	fields_tools_module.mod 
	operators_module.mod 
	grad_field_module.mod 
	projectors_module.mod 
	grad_s_field_module.mod 
	second_deriv_field_module.mod 
	h1_norm_module.mod 
	second_deriv_module.mod 
	hessian_field_module.mod 
	second_deriv_s_field_module.mod 
	identity_field_module.mod 
	stiffness_module.mod)

add_library(assembly SHARED ${assembly_files})
target_link_libraries(assembly tools tracelog geometries connectivities grids blackboxes spm fem)
install(TARGETS assembly DESTINATION lib)
##########################################################################
