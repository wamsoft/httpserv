set(TPSTUB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../tp_stub CACHE PATH "Path to tp_stub directory")
include(${TPSTUB_DIR}/krkrz.cmake)

find_package(Poco REQUIRED COMPONENTS Foundation Util Net XML)

krkrz_plugin(httpserv
    NCBIND
    SOURCES
        serv.cpp
        main.cpp
    LIBRARIES
        Poco::Foundation
        Poco::Util
        Poco::Net
        Poco::XML
)
