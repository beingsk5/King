# SUSFS

- This is a heavily modified version of susfs v1.5.12
- It does not comply with the upstream offical susfs v1.5.12
- sus_mount functionality still remain in v1.5.5 as backporting it to the latest version will result a mount detection leak in some apps/detectors
- Increase susfs_open_redirect UID limit to <11000
- susfs magic mount support is still implemented and enabled
- sus_map is implemented and complied with the upstream v1.5.12 codebase

This commit requires a bunch of backports commits from v4.19 and v5.x to make sus_map working:

0a8cbf3725edbacc5f1ead33eeae7e4d78823b5a proc: less memory for /proc/*/map_files readdir
37ae2444584654f6785f2cc49181f05af788c9b2 mm: smaps: split PSS into components
49a5115e11350ee68f6a5fbd56b3e817bf9e5aac fs/task_mmu: add pkeys header
6f94042bed51121f8f28a5e572cda20c21fed2e1 mm/pkeys: Add an empty arch_pkeys_enabled()
bbd5aec12b32097a71dc6a0097194a18f3ee9a17 mm/pkeys, powerpc, x86: Provide an empty vma_pkey() in linux/pkeys.h
849ca8ce954d9dbb082dcf83c98af861e98e5635 mm: /proc/pid/smaps_rollup: convert to single value seq_file
6071a482c8e603be25895cc2cac5f0eab61c4051 mm: /proc/pid/smaps: factor out common stats printing
03fd2fbe9c40da8128cec5c69ef54755c0f38c6c mm: /proc/pid/smaps: factor out mem stats gathering
95f8be4c8a86a491a1c2ac9bfe470aef9e1baa8f mm: /proc/pid/*maps remove is_pid and related wrappers
27956d255e3b012372951dd6131e07c106d2daae procfs: add seq_put_hex_ll to speed up /proc/pid/maps
7f2847d02cdc4491b5ee6d4a0043854cbd6c7a1a proc: add seq_put_decimal_ull_width to speed up /proc/pid/smaps

For KernelSU side patches for this commit you need the sidex15's KernelSU-Next fork:
https://github.com/sidex15/KernelSU-Next/tree/n3x7g3n-kernel

Or if you want to patch on your own here's the commit patch of susfs in the KernelSU-Next:
(sidex15/KernelSU-Next@13b1dfd) https://github.com/sidex15/KernelSU-Next/commit/13b1dfd6e2f1b7b353e774ad8dbc66012450d80f
