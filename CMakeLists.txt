cmake_minimum_required(VERSION 3.22.1)
#start by declaring the version of cmake to use. for me using ubuntu 22.04
#so I had to run the following command to see the version of cmake installed [cmake --version]   

project(CMake_tutorial)
#use the method provide to a project name to reffer to your project

add_executable(${PROJECT_NAME} main.c) 
#This one links any related files to the project in this case main.c is the only file with me 
#Note the keyword ${PROJECT_NAME};this is a variable tht holds the project name so in either ${PROJECT_NAME}=Cmake_tutorial 
#in the case of our project.The assignment of this variable is done by default by cmake 

add_subdirectory(header) 
# I created a folder named hearder where I can can edit some c code so as to use it latter as a header file. 
#In the directory I have edited the add.c file with some function to do simple summing of numbers.
#Again created add.h to hold the function defination and lastly a CMakeLists.txt where I'm creating add.h to be a library.  
target_include_directories(${PROJECT_NAME} PUBLIC header)
#This is to include the header directory into the project

target_link_directories(${PROJECT_NAME} PRIVATE header)
#Link the header directory with the project

target_link_libraries(${PROJECT_NAME} add)
#Link the library with the project
