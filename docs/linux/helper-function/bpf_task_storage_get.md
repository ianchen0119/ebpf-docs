---
title: "Helper Function 'bpf_task_storage_get'"
description: "This page documents the 'bpf_task_storage_get' eBPF helper function, including its definition, usage, program types that can use it, and examples."
---
# Helper function `bpf_task_storage_get`

<!-- [FEATURE_TAG](bpf_task_storage_get) -->
[:octicons-tag-24: v5.11](https://github.com/torvalds/linux/commit/4cf1bc1f10452065a29d576fc5693fc4fab5b919)
<!-- [/FEATURE_TAG] -->

## Definition

> Copyright (c) 2015 The Libbpf Authors. All rights reserved.

Get a bpf_local_storage from the `task`. 

Logically, it could be thought of as getting the value from a `map` with `task` as the `key`. From this perspective, the usage is not much different from [`bpf_map_lookup_elem(map, &task)`](../helper-function/bpf_map_lookup_elem.md) except this helper enforces the key must be a valid BTF pointer to `struct task_struct` (see [`bpf_get_current_task_btf`](../helper-function/bpf_get_current_task_btf.md) for more information), and the map must also be a [`BPF_MAP_TYPE_TASK_STORAGE`](../map-type/BPF_MAP_TYPE_TASK_STORAGE.md). 

Underneath, the value is stored locally at `task` instead of the `map`.  The `map` is used as the bpf-local-storage "type". The bpf-local-storage "type" (i.e. the `map`) is searched against all bpf_local_storage residing at `task`.

An optional `flags` (`BPF_LOCAL_STORAGE_GET_F_CREATE`) can be used such that a new bpf_local_storage will be created if one does not exist. `value` can be used together with `BPF_LOCAL_STORAGE_GET_F_CREATE` to specify the initial value of a bpf_local_storage.  If `value` is `NULL`, the new bpf_local_storage will be zero initialized.

### Returns

A bpf_local_storage pointer is returned on success.

`NULL` if not found or there was an error in adding a new bpf_local_storage.

`#!c static void *(* const bpf_task_storage_get)(void *map, struct task_struct *task, void *value, __u64 flags) = (void *) 156;`


## Usage

!!! example "Docs could be improved"
    This part of the docs is incomplete, contributions are very welcome

### Program types

This helper call can be used in the following program types:

<!-- DO NOT EDIT MANUALLY -->
<!-- [HELPER_FUNC_PROG_REF] -->
 * [`BPF_PROG_TYPE_KPROBE`](../program-type/BPF_PROG_TYPE_KPROBE.md)
 * [`BPF_PROG_TYPE_LSM`](../program-type/BPF_PROG_TYPE_LSM.md)
 * [`BPF_PROG_TYPE_PERF_EVENT`](../program-type/BPF_PROG_TYPE_PERF_EVENT.md)
 * [`BPF_PROG_TYPE_RAW_TRACEPOINT`](../program-type/BPF_PROG_TYPE_RAW_TRACEPOINT.md)
 * [`BPF_PROG_TYPE_RAW_TRACEPOINT_WRITABLE`](../program-type/BPF_PROG_TYPE_RAW_TRACEPOINT_WRITABLE.md)
 * [`BPF_PROG_TYPE_SYSCALL`](../program-type/BPF_PROG_TYPE_SYSCALL.md)
 * [`BPF_PROG_TYPE_TRACEPOINT`](../program-type/BPF_PROG_TYPE_TRACEPOINT.md)
 * [`BPF_PROG_TYPE_TRACING`](../program-type/BPF_PROG_TYPE_TRACING.md)
<!-- [/HELPER_FUNC_PROG_REF] -->

### Example

!!! example "Docs could be improved"
    This part of the docs is incomplete, contributions are very welcome
