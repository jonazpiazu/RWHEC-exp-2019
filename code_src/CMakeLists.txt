cmake_minimum_required(VERSION 3.8)

project(RWHEC_Jul2019_Exp)

find_package(Ceres REQUIRED)
find_package(OpenCV 4.0 REQUIRED COMPONENTS core highgui imgproc calib3d imgcodecs)
find_package(Eigen3 REQUIRED)

add_executable(eye-hand-calibration
CostFunctions.hpp
CostFunctions.cpp
Calibration2.hpp
Calibration2.cpp
StringFunctions.hpp
DirectoryFunctions.hpp
DirectoryFunctions.cpp
RWHEC_Jul2019_Exp.hpp
RWHEC_Jul2019_Exp.cpp
)

target_compile_options(eye-hand-calibration PRIVATE -Wall -pedantic -Wextra)
target_compile_features(eye-hand-calibration PUBLIC cxx_std_11)
target_include_directories(eye-hand-calibration SYSTEM PRIVATE ${EIGEN3_INCLUDE_DIR})
target_link_libraries(eye-hand-calibration PRIVATE ${CERES_LIBRARIES} ${OpenCV_LIBS})
