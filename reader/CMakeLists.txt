ADD_LIBRARY(reader INTERFACE)
TARGET_SOURCES(reader INTERFACE
  ${CMAKE_CURRENT_SOURCE_DIR}/PlainTextMapEventReader.h
  ${CMAKE_CURRENT_SOURCE_DIR}/PlainTextReader.h
  ${CMAKE_CURRENT_SOURCE_DIR}/Reader.h)

IF(GTEST_FOUND AND GMOCK_FOUND AND WITH_TESTS)
  ADD_EXECUTABLE(PlainTextReaderTest PlainTextReaderTest.cc PlainTextReader.h)
  TARGET_LINK_LIBRARIES(PlainTextReaderTest
    core ${GTEST_LIBRARIES} ${GMOCK_BOTH_LIBRARIES} ${COMMON_LIBRARIES})
  ADD_TEST(PlainTextReaderTest PlainTextReaderTest)
ENDIF()
