cmake_minimum_required(VERSION 3.0)
project(meshfix)

include_directories(include/TMesh)
include_directories(include/Kernel)


add_library(algorithms src/Algorithms/checkAndRepair.cpp
	              src/Algorithms/detectIntersections.cpp
		      src/Algorithms/holeFilling.cpp
		      src/Algorithms/marchIntersections.cpp
		      src/Algorithms/subdivision.cpp)
add_library(kernel src/Kernel/coordinates.cpp
            src/Kernel/graph.cpp
            src/Kernel/heap.cpp
				 src/Kernel/jqsort.cpp
				 src/Kernel/list.cpp
				 src/Kernel/matrix.cpp
				 src/Kernel/orientation.c
				 src/Kernel/point.cpp
				 src/Kernel/tmesh.cpp)
			 add_library(tmesh src/TMesh/edge.cpp
				           src/TMesh/io.cpp
					   src/TMesh/tin.cpp
					   src/TMesh/triangle.cpp
					   src/TMesh/vertex.cpp)
				   add_executable(meshfix src/MeshFix/meshfix.cpp)
				   target_link_libraries(meshfix algorithms kernel tmesh)

