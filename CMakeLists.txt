include(../tp_stub/krkrz.cmake)

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
