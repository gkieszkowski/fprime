####
# F prime CMakeLists.txt:
#
# SOURCE_FILES: combined list of source and autocoding diles
# MOD_DEPS: (optional) module dependencies
#
####
if(FPRIME_USE_STUBBED_DRIVERS)
    add_definitions(-DSTUBBED_LINUX_I2C_DRIVER)
    set(SOURCE_FILES
        "${CMAKE_CURRENT_LIST_DIR}/LinuxI2cDriverComponentAi.xml"
        "${CMAKE_CURRENT_LIST_DIR}/LinuxI2cDriverComponentImplStub.cpp"
    )
    register_fprime_module()
elseif(${CMAKE_SYSTEM_NAME} STREQUAL "Linux")
    set(SOURCE_FILES
        "${CMAKE_CURRENT_LIST_DIR}/LinuxI2cDriverComponentAi.xml"
        "${CMAKE_CURRENT_LIST_DIR}/LinuxI2cDriverComponentImpl.cpp"
    )
    register_fprime_module()
else()
    message(STATUS "Cannot use ${CMAKE_CURRENT_LIST_DIR} with platform ${CMAKE_SYSTEM_NAME}. Skipping.")
endif()


