$ export GITHUB_USERNAME=h04d1n1
$ export GITHUB_EMAIL=fedor.z1234@yandex.ru
$ alias edit=nvim
$ alias gsed=sed

$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
~/h04d1n1/workspace ~/h04d1n1/workspace
$ source scripts/activate

$ git clone https://github.com/${GITHUB_USERNAME}/lab05 projects/lab06
Cloning into 'projects/lab06'...
remote: Enumerating objects: 26, done.
remote: Counting objects: 100% (26/26), done.
remote: Compressing objects: 100% (16/16), done.
remote: Total 26 (delta 2), reused 23 (delta 1), pack-reused 0 (from 0)
Receiving objects: 100% (26/26), 9.04 KiB | 2.26 MiB/s, done.
Resolving deltas: 100% (2/2), done.
$ cd projects/lab06
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab06

$ gsed -i '/project(print)/a\
set(PRINT_VERSION_STRING "v\${PRINT_VERSION}")
' CMakeLists.txt
$ gsed -i '/project(print)/a\
set(PRINT_VERSION\
  \${PRINT_VERSION_MAJOR}.\${PRINT_VERSION_MINOR}.\${PRINT_VERSION_PATCH}.\${PRINT_VERSION_TWEAK})
' CMakeLists.txt
$ gsed -i '/project(print)/a\
set(PRINT_VERSION_TWEAK 0)
' CMakeLists.txt
$ gsed -i '/project(print)/a\
set(PRINT_VERSION_PATCH 0)
' CMakeLists.txt
$ gsed -i '/project(print)/a\
set(PRINT_VERSION_MINOR 1)
' CMakeLists.txt
$ gsed -i '/project(print)/a\
set(PRINT_VERSION_MAJOR 0)
' CMakeLists.txt
$ git diff
diff --git a/CMakeLists.txt b/CMakeLists.txt
index 28c6745..be54843 100644
--- a/CMakeLists.txt
+++ b/CMakeLists.txt
@@ -6,6 +6,13 @@ set(CMAKE_CXX_STANDARD_REQUIRED ON)
 option(BUILD_EXAMPLES "Build examples" OFF)
 
 project(print)
+set(PRINT_VERSION_MAJOR 0)
+set(PRINT_VERSION_MINOR 1)
+set(PRINT_VERSION_PATCH 0)
+set(PRINT_VERSION_TWEAK 0)
+set(PRINT_VERSION
+  ${PRINT_VERSION_MAJOR}.${PRINT_VERSION_MINOR}.${PRINT_VERSION_PATCH}.${PRINT_VERSION_TWEAK})
+set(PRINT_VERSION_STRING "v${PRINT_VERSION}")
 
 add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
 

$ touch DESCRIPTION && edit DESCRIPTION
$ touch ChangeLog.md
$ export DATE="`LANG=en_US date +'%a %b %d %Y'`"
$ cat > ChangeLog.md <<EOF
* ${DATE} ${GITHUB_USERNAME} <${GITHUB_EMAIL}> 0.1.0.0
- Initial RPM release
EOF

$ cat > CPackConfig.cmake <<EOF
include(InstallRequiredSystemLibraries)
EOF

$ cat >> CPackConfig.cmake <<EOF
set(CPACK_PACKAGE_CONTACT ${GITHUB_EMAIL})
set(CPACK_PACKAGE_VERSION_MAJOR \${PRINT_VERSION_MAJOR})
set(CPACK_PACKAGE_VERSION_MINOR \${PRINT_VERSION_MINOR})
set(CPACK_PACKAGE_VERSION_PATCH \${PRINT_VERSION_PATCH})
set(CPACK_PACKAGE_VERSION_TWEAK \${PRINT_VERSION_TWEAK})
set(CPACK_PACKAGE_VERSION \${PRINT_VERSION})
set(CPACK_PACKAGE_DESCRIPTION_FILE \${CMAKE_CURRENT_SOURCE_DIR}/DESCRIPTION)
set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "static C++ library for printing")
EOF

$ cat >> CPackConfig.cmake <<EOF

set(CPACK_RESOURCE_FILE_LICENSE \${CMAKE_CURRENT_SOURCE_DIR}/LICENSE)
set(CPACK_RESOURCE_FILE_README \${CMAKE_CURRENT_SOURCE_DIR}/README.md)
EOF

$ cat >> CPackConfig.cmake <<EOF

set(CPACK_RPM_PACKAGE_NAME "print-devel")
set(CPACK_RPM_PACKAGE_LICENSE "MIT")
set(CPACK_RPM_PACKAGE_GROUP "print")
set(CPACK_RPM_CHANGELOG_FILE \${CMAKE_CURRENT_SOURCE_DIR}/ChangeLog.md)
set(CPACK_RPM_PACKAGE_RELEASE 1)
EOF

$ cat >> CPackConfig.cmake <<EOF

set(CPACK_DEBIAN_PACKAGE_NAME "libprint-dev")
set(CPACK_DEBIAN_PACKAGE_PREDEPENDS "cmake >= 3.0")
set(CPACK_DEBIAN_PACKAGE_RELEASE 1)
EOF

$ cat >> CPackConfig.cmake <<EOF

include(CPack)
EOF

$ cat >> CMakeLists.txt <<EOF

include(CPackConfig.cmake)
EOF

$ gsed -i 's/lab05/lab06/g' README.md

$ git add .
$ git commit -m"added cpack config"
[main 5586ed2] Added CPack config
 5 files changed, 51 insertions(+), 16 deletions(-)
 create mode 100644 CPackConfig.cmake
 create mode 100644 ChangeLog.md
 create mode 100644 DESCRIPTION
$ git tag v0.1.0.0
$ git push origin main --tags
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (7/7), 1.32 KiB | 1.32 MiB/s, done.
Total 7 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/h04d1n1/lab06
   1d4dff5..5586ed2  main -> main
 * [new tag]         v0.1.0.0 -> v0.1.0.0
 
$ cmake -H. -B_build
-- The C compiler identification is GNU 14.2.1
-- The CXX compiler identification is GNU 14.2.1
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/freeman/h04d1n1/workspace/projects/lab06/_build
$ cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
$ cd _build
$ cpack -G "TGZ"
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/freeman/h04d1n1/workspace/projects/lab06/_build/print-0.1.0.0-Linux.tar.gz generated.
$ cd ..

$ cmake -H. -B_build -DCPACK_GENERATOR="TGZ"
-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/freeman/h04d1n1/workspace/projects/lab06/_build
$ cmake --build _build --target package
[100%] Built target print
Run CPack packaging tool...
CPack: Create package using TGZ
CPack: Install projects
CPack: - Run preinstall target for: print
CPack: - Install project: print []
CPack: Create package
CPack: - package: /home/freeman/h04d1n1/workspace/projects/lab06/_build/print-0.1.0.0-Linux.tar.gz generated.

$ mkdir artifacts
$ mv _build/*.tar.gz artifacts
$ tree artifacts
artifacts/
└── print-0.1.0.0-Linux.tar.gz

1 directory, 1 file
