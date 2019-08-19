# Cmake

## How to emulate `make check`

- Define a custom target
```
add_custom_target(check COMMAND ${CMAKE_CTEST_COMMAND})
```

- Add a test program
```
add_executable(<testprog> EXCLUDE_FROM_ALL)
add_test(<testprog> <testprog>)
add_dependencies(check <testprog>)
```

(ref)
- https://gitlab.kitware.com/cmake/community/wikis/doc/tutorials/EmulateMakeCheck
