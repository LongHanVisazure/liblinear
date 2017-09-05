CMAKE_MINIMUM_REQUIRED(VERSION 2.8.3)

OPTION (BUILD_SHARED_LIBS "Build shared libraries." ON)

SET(CMAKE_PROJECT_NAME "liblinear")

SET(BLAS_SRCS blas/blas.h blas/blasp.h blas/daxpy.c blas/ddot.c blas/dnrm2.c blas/dscal.c)

SET(LIBBLAS blas)

SET(LIBLINEAR linear)

SET(TRAIN train)

SET(PREDICT predict)

SET(LINEAR_SRCS linear.cpp tron.cpp tron.h linear.h)

ADD_LIBRARY(${LIBBLAS} ${BLAS_SRCS})

ADD_LIBRARY(${LIBLINEAR} ${LINEAR_SRCS} ${LIBBLAS})

ADD_EXECUTABLE(${TRAIN} train.c ${LIBLINEAR} ${LIBBLAS})

ADD_EXECUTABLE(${PREDICT} predict.c ${LIBLINEAR} ${LIBBLAS})
