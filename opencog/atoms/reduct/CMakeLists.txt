
# The atom_types.h file is written to the build directory
INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_BINARY_DIR})

ADD_LIBRARY (clearbox
	AccumulateLink.cc
	ArithmeticLink.cc
	DivideLink.cc
	FoldLink.cc
	HeavisideLink.cc
	MaxLink.cc
	MinLink.cc
	MinusLink.cc
	PlusLink.cc
	TimesLink.cc
)

# Without this, parallel make will race and crap up the generated files.
ADD_DEPENDENCIES(clearbox opencog_atom_types)

TARGET_LINK_LIBRARIES(clearbox
	atom_types
	atomcore
	atombase
	value
	${COGUTIL_LIBRARY}
)

INSTALL (TARGETS clearbox EXPORT AtomSpaceTargets
	DESTINATION "lib${LIB_DIR_SUFFIX}/opencog"
)

INSTALL (FILES
	AccumulateLink.h
	ArithmeticLink.h
	DivideLink.h
	FoldLink.h
	HeavisideLink.h
	MaxLink.h
	MinLink.h
	MinusLink.h
	PlusLink.h
	TimesLink.h
	DESTINATION "include/opencog/atoms/reduct"
)
