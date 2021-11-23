cmake_minimum_required(VERSION 3.19)

project(sendosc)
set (CMAKE_CXX_STANDARD 11)

if (WIN32)
	set(IpSystemTypePath ${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/win32)
	set(LIBS ${LIBS} Ws2_32 winmm)
else()
	set(IpSystemTypePath ${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/posix)
endif()

add_library(oscpack
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/IpEndpointName.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/IpEndpointName.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/NetworkingUtils.h

	${IpSystemTypePath}/NetworkingUtils.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/NetworkingUtils.h

	${IpSystemTypePath}/UdpSocket.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/UdpSocket.h

	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/PacketListener.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/ip/TimerListener.h

	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscTypes.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscTypes.cpp 
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscHostEndianness.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscException.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscPacketListener.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/MessageMappingOscPacketListener.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscReceivedElements.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscReceivedElements.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscPrintReceivedElements.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscPrintReceivedElements.cpp
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscOutboundPacketStream.h
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack/osc/OscOutboundPacketStream.cpp	
)

target_include_directories(oscpack
	PUBLIC
	${CMAKE_CURRENT_SOURCE_DIR}/lib/oscpack
)

add_executable(sendosc sendosc.cpp)
target_link_libraries(sendosc oscpack ${LIBS})
