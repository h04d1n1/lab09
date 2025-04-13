$ export GITHUB_USERNAME=h04d1n1
$ alias gsed=sed # for *-nix system

$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
~/h04d1n1/workspace ~
$ source scripts/activate

$ git clone https://github.com/${GITHUB_USERNAME}/lab04 projects/lab05
Cloning into 'projects/lab05'...
remote: Enumerating objects: 36, done.
remote: Counting objects: 100% (36/36), done.
remote: Compressing objects: 100% (23/23), done.
remote: Total 36 (delta 5), reused 30 (delta 5), pack-reused 0 (from 0)
Receiving objects: 100% (36/36), 14.39 KiB | 320.00 KiB/s, done.
Resolving deltas: 100% (5/5), done.
$ cd projects/lab05
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab05

$ mkdir third-party
$ git submodule add https://github.com/google/googletest third-party/gtest
Cloning into '/home/freeman/h04d1n1/workspace/projects/lab05/third-party/gtest'...
remote: Enumerating objects: 27991, done.
remote: Counting objects: 100% (234/234), done.
remote: Compressing objects: 100% (149/149), done.
remote: Total 27991 (delta 146), reused 86 (delta 84), pack-reused 27757 (from 4)
Receiving objects: 100% (27991/27991), 13.51 MiB | 5.72 MiB/s, done.
Resolving deltas: 100% (20736/20736), done.
$ cd third-party/gtest && git checkout release-1.8.1 && cd ../..
Note: switching to 'release-1.8.1'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 2fe3bd99 Merge pull request #1433 from dsacre/fix-clang-warnings
$ git add third-party/gtest
$ git commit -m"added gtest framework"
[main 516b853] added gtest framework
 2 files changed, 4 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 third-party/gtest
 
 $ gsed -i '/option(BUILD_EXAMPLES "Build examples" OFF)/a\
option(BUILD_TESTS "Build tests" OFF)
' CMakeLists.txt
$ cat >> CMakeLists.txt <<EOF

if(BUILD_TESTS)
  enable_testing()
  add_subdirectory(third-party/gtest)
  file(GLOB \${PROJECT_NAME}_TEST_SOURCES tests/*.cpp)
  add_executable(check \${\${PROJECT_NAME}_TEST_SOURCES})
  target_link_libraries(check \${PROJECT_NAME} gtest_main)
  add_test(NAME check COMMAND check)
endif()
EOF

$ mkdir tests
$ cat > tests/test1.cpp <<EOF
#include <print.hpp>

#include <gtest/gtest.h>

TEST(Print, InFileStream)
{
  std::string filepath = "file.txt";
  std::string text = "hello";
  std::ofstream out{filepath};

  print(text, out);
  out.close();

  std::string result;
  std::ifstream in{filepath};
  in >> result;

  EXPECT_EQ(result, text);
}
EOF

$ cmake -H. -B_build -DBUILD_TESTS=ON
-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/freeman/h04d1n1/workspace/projects/lab05/_build
$ cmake --build _build
[ 16%] Built target print
[ 25%] Building CXX object third-party/gtest/googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 33%] Linking CXX static library ../../../lib/libgtest.a
[ 33%] Built target gtest
[ 41%] Building CXX object third-party/gtest/googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Linking CXX static library ../../../lib/libgtest_main.a
[ 50%] Built target gtest_main
[ 58%] Building CXX object CMakeFiles/check.dir/tests/test1.cpp.o
[ 66%] Linking CXX executable check
[ 66%] Built target check
[ 75%] Building CXX object third-party/gtest/googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 83%] Linking CXX static library ../../../lib/libgmock.a
[ 83%] Built target gmock
[ 91%] Building CXX object third-party/gtest/googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../../../lib/libgmock_main.a
[100%] Built target gmock_main
$ cmake --build _build --target test
Running tests...
Test project /home/freeman/h04d1n1/workspace/projects/lab05/_build
    Start 1: check
1/1 Test #1: check ............................   Passed    0.01 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.01 sec

$ _build/check
Running main() from /home/freeman/h04d1n1/workspace/projects/lab05/third-party/gtest/googletest/src/gtest_main.cc
[==========] Running 1 test from 1 test suite.
[----------] Global test environment set-up.
[----------] 1 test from Print
[ RUN      ] Print.InFileStream
[       OK ] Print.InFileStream (0 ms)
[----------] 1 test from Print (0 ms total)

[----------] Global test environment tear-down
[==========] 1 test from 1 test suite ran. (0 ms total)
[  PASSED  ] 1 test.
$ cmake --build _build --target test -- ARGS=--verbose
Running tests...
UpdateCTestConfiguration  from :/home/freeman/h04d1n1/workspace/projects/lab05/_build/DartConfiguration.tcl
UpdateCTestConfiguration  from :/home/freeman/h04d1n1/workspace/projects/lab05/_build/DartConfiguration.tcl
Test project /home/freeman/h04d1n1/workspace/projects/lab05/_build
Constructing a list of tests
Done constructing a list of tests
Updating test list for fixtures
Added 0 tests to meet fixture requirements
Checking test dependency graph...
Checking test dependency graph end
test 1
    Start 1: check

1: Test command: /home/freeman/h04d1n1/workspace/projects/lab05/_build/check
1: Working Directory: /home/freeman/h04d1n1/workspace/projects/lab05/_build
1: Test timeout computed to be: 10000000
1: Running main() from /home/freeman/h04d1n1/workspace/projects/lab05/third-party/gtest/googletest/src/gtest_main.cc
1: [==========] Running 1 test from 1 test suite.
1: [----------] Global test environment set-up.
1: [----------] 1 test from Print
1: [ RUN      ] Print.InFileStream
1: [       OK ] Print.InFileStream (0 ms)
1: [----------] 1 test from Print (0 ms total)
1: 
1: [----------] Global test environment tear-down
1: [==========] 1 test from 1 test suite ran. (0 ms total)
1: [  PASSED  ] 1 test.
1/1 Test #1: check ............................   Passed    0.00 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.00 sec

$ gsed -i 's/lab04/lab05/g' README.md
$ gsed -i 's/\(DCMAKE_INSTALL_PREFIX=_install\)/\1 -DBUILD_TESTS=ON/' .travis.yml
$ gsed -i '/cmake --build _build --target install/a\
- cmake --build _build --target test -- ARGS=--verbose
' .travis.yml

$ travis lint

$ git add .travis.yml
$ git add tests
$ git add -p
diff --git a/third-party/gtest b/third-party/gtest
index 2fe3bd9..e90fe24 160000
--- a/third-party/gtest
+++ b/third-party/gtest
@@ -1 +1 @@
-Subproject commit 2fe3bd994b3189899d93f1d5a881e725e046fdc2
+Subproject commit e90fe2485641bab0d6af4500192dc503384950d1
$ git commit -m"added tests"
[main f4a794f] added tests
 4 files changed, 35 insertions(+), 154 deletions(-)
 create mode 100644 .travis.yml
 create mode 100644 tests/test1.cpp
$ git push origin main
Enumerating objects: 17, done.
Counting objects: 100% (17/17), done.
Delta compression using up to 8 threads
Compressing objects: 100% (10/10), done.
Writing objects: 100% (17/17), 5.06 KiB | 2.53 MiB/s, done.
Total 17 (delta 0), reused 6 (delta 0), pack-reused 0 (from 0)
To https://github.com/h04d1n1/lab05
 * [new branch]      main -> main
 
$ mkdir artifacts
$ sleep 20s && gnome-screenshot --file artifacts/screenshot.png
bash: gnome-screenshot: command not found
# Использую Hyprland, поэтому у меня нет команд gnome
