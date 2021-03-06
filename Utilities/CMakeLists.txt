# Wrapping and stuff

# Do jpeg (8,12, 16 lossly lossless). From ijg
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmjpeg/COPYRIGHT.dcmtk)
if(NOT GDCM_USE_SYSTEM_LJPEG)
  set(JPEG_NAMESPACE "GDCMJPEG")
  set(JPEG_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(JPEG_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(JPEG_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  set(JPEG_INSTALL_INCLUDE_DIR  ${GDCM_INSTALL_INCLUDE_DIR}/gdcmjpeg)
  subdirs(gdcmjpeg)
endif()

# Do expat
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmexpat/COPYING)
if(NOT GDCM_USE_SYSTEM_EXPAT)
  set(EXPAT_NAMESPACE "GDCMEXPAT")
  set(EXPAT_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(EXPAT_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(EXPAT_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  subdirs(gdcmexpat)
endif()

# Do openjpeg (jpeg2000 implementation)
if(GDCM_USE_OPENJPEG_V2)
  APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmopenjpeg-v2/license.txt)
else()
  APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmopenjpeg-v1/LICENSE)
endif()
if(NOT GDCM_USE_SYSTEM_OPENJPEG)
  set(OPENJPEG_NAMESPACE "GDCMOPENJPEG")
  set(OPENJPEG_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(OPENJPEG_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(OPENJPEG_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  set(OPENJPEG_INSTALL_INCLUDE_DIR  ${GDCM_INSTALL_INCLUDE_DIR}/gdcmopenjpeg)
  if(GDCM_USE_OPENJPEG_V2)
    subdirs(gdcmopenjpeg-v2)
  else()
    subdirs(gdcmopenjpeg-v1)
  endif()
endif()

# Do jpegls (JPEG-LS aka near lossless implementation)
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmcharls/License.txt)
if(GDCM_USE_JPEGLS)
if(NOT GDCM_USE_SYSTEM_CHARLS)
  set(CHARLS_NAMESPACE "GDCMCHARLS")
  set(CHARLS_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(CHARLS_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(CHARLS_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  set(CHARLS_INSTALL_INCLUDE_DIR  ${GDCM_INSTALL_INCLUDE_DIR}/gdcmcharls)
  subdirs(gdcmcharls)
endif()
endif()

# Do md5
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmmd5/COPYING)
if(GDCM_BUILD_TESTING)
if(NOT GDCM_USE_SYSTEM_MD5)
  set(MD5_NAMESPACE "GDCMMD5")
  set(MD5_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(MD5_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(MD5_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  subdirs(gdcmmd5)
endif()
endif()

# Do zlib
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmzlib/COPYING)
if(NOT GDCM_USE_SYSTEM_ZLIB)
  set(ZLIB_NAMESPACE "GDCMZLIB")
  set(ZLIB_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(ZLIB_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(ZLIB_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  subdirs(gdcmzlib)
endif()

# Do getopt
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/getopt/COPYING)
if(WIN32 AND NOT CYGWIN)
  set(GETOPT_NAMESPACE "GDCMGETOPT")
  set(GETOPT_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(GETOPT_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(GETOPT_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  subdirs(getopt)
endif()

#subdirs(doxygen)

# you could be running mingw32 on linux in which case you do NOT want the gdcmuuid lib
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/gdcmuuid/COPYING)
if(NOT WIN32 AND NOT MINGW)
  if(NOT GDCM_USE_SYSTEM_UUID)
    set(UUID_NAMESPACE "GDCMUUID")
    set(UUID_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
    set(UUID_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
    set(UUID_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
    subdirs(gdcmuuid)
  endif()
endif()

APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/pvrg/COPYING)
if(GDCM_USE_PVRG)
  if(NOT GDCM_USE_SYSTEM_PVRG)
    subdirs(pvrg)
  endif()
endif()

if(GDCM_USE_RLE)
  subdirs(rle)
endif()

# Do C99
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/C99/COPYING)

# Do wxVTK
APPEND_COPYRIGHT(${CMAKE_CURRENT_SOURCE_DIR}/wxWidgets/Copyright.txt)

#if(NOT GDCM_INSTALL_NO_DEVELOPMENT)
##  file(GLOB header_files "*.h" "*.txx")
#  install(FILES
##${header_files}
#gdcm_expat.h
##gdcm_md5.h # In an install tree there should not be the need for the md5 lib...
#gdcm_openjpeg.h
#gdcm_uuid.h
#gdcm_zlib.h
#    DESTINATION ${GDCM_INSTALL_INCLUDE_DIR} COMPONENT Headers
#  )
#endif()

#if(GDCM_USE_KWSTYLE)
  subdirs(KWStyle)
#endif()

if(NOT GDCM_USE_SYSTEM_SOCKETXX)
#set(SOCKETXX_NAMESPACE "GDCMSOCKETXX")
  set(SOCKETXX_INSTALL_NO_LIBRARIES ${GDCM_INSTALL_NO_LIBRARIES})
  set(SOCKETXX_INSTALL_BIN_DIR      ${GDCM_INSTALL_BIN_DIR})
  set(SOCKETXX_INSTALL_LIB_DIR      ${GDCM_INSTALL_LIB_DIR})
  set(SOCKETXX_INSTALL_INCLUDE_DIR  ${GDCM_INSTALL_INCLUDE_DIR}/socketxx)
  subdirs(socketxx)
endif()

add_subdirectory(gdcmrle)
