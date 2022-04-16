---
title: 'clang-error:undefined reference to'
date: 2022-03-31 16:32:36
tags:
---
# clang-error:undefined reference to 
    grep-2.19.c.origin.c:(.text+0xd8f6): 
    undefined reference to `pcre_exec'/usr/bin/ld: /tmp/grep-2-d00552.o: in function `EGexecute':
    solution:
    `clang -lpcre ` 

    grep-2.19.c.origin.c:(.text+0x1228b): undefined reference to `__msan_unpoison'
    clang: error: linker command failed with exit code 1 (use -v to see invocation)
    solution:
    `clang -D __msan_unpoison(s,z)`
