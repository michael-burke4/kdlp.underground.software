## Overview

What is memory management?

1. Phsyical and virtual memory

1. Allocation

1. Paging

Just scratching the surface!

## Virtual memory

We start without any: this is NOMMU mode

### Address space isolation

Clone system call

Demo: `man 2 clone`

Aside: See `posix_spawn(3)`

Question: How is fork defined?

A: it's just clone

`kernel/fork.c`
```
2887 #ifdef __ARCH_WANT_SYS_FORK
2888 SYSCALL_DEFINE0(fork)
2889 {
2890 #ifdef CONFIG_MMU
2891         struct kernel_clone_args args = {
2892                 .exit_signal = SIGCHLD,
2893         };
2894
2895         return kernel_clone(&args);
2896 #else
2897         /* can not support in nommu mode */
2898         return -EINVAL;
2899 #endif
2900 }
2901 #endif
```

Namespace interlude

`clone(CLONE_VM)`

1. `CLONE_VM`: The new process shares the same memory space as the parent.
1. `CLONE_FS`: Shares file system information.
1. `CLONE_FILES`: Shares file descriptors.
1. `CLONE_SIGHAND`: Shares signal handlers.

Discuss namespaces: isolated view of system resources

* Mount Namespace (mnt) – Isolates filesystem mount points.
* Process Namespace (pid) – Provides separate process ID trees.
* Network Namespace (net) – Gives processes their own networking stack.
* User Namespace (user) – Provides separate user and group IDs.
* UTS Namespace (uts) – Isolates hostname and domain name.
* IPC Namespace (ipc) – Isolates inter-process communication mechanisms.
* Cgroup Namespace (cgroup) – Provides separate views of control groups.

Demo: `unshare`

```
sudo unshare --pid --fork --mount-proc bash
```

`--pid`: Creates a new PID namespace.

`--fork`: Forks a new process to run the specified program (in this case, bash).

`--mount-proc`: Mounts a new `/proc` filesystem for the new PID namespace.

Look at `ps auxf` inside and outside the new shell

Find the external PID X of the new internal PID 1

Look at both of `sudo ls -l /proc/{$X,$$}/ns`


### NOMMU demo

Q: Can we achieve address space isolation without the MMU?

A: No

#### What can a nommu do?

1. NOMMU lack of memory isolation demo

#### Enabling the MMU:

1. Enable the MMU (disable RISCV_M_MODE, enable MMU in menuconfig)

1. Recompile the kernel, init, and run

1. Successful segfault!

Types of kernel addresses in MMU mode

Logical: fixed offset from physical memory

* This is what `phys_to_virt` does

Virtual: has entry in page tables

## Slob/Slab/Slub allocators

1. SLOB

    * Simple list of blocks

    * Slowest, oldest, simplest

    * Uses global `slob_lock`

1. SLAB

    * Newer, but not the best

    * Still locks

    * Improved performance via caching and per-cpu lists

1. SLUB

    * fastest, newest

    * Lockless fastpath for alloc/deallocs

    * Locks only when crossing CPU boundary

Demo: `/proc/slabinfo`

To set allocator: add `slab_allocator=sl{u,a,o}b` to kernel command line at boot

Collectively, these are the "slab allocators" or "slab layer"

## Paging, page reclaim, swap

What weighs more: 10G of physical memory of 10G of virtual memory (joke)

Technically: virtual memory requires pagetables so there is some overhead

What's bigger: physical or virtual memory?

Answer: virtual memory. Why?

On 64 bit system each process had maximum address space of size 2^64!

Therefore: we need to swap out pages so physical memory doesn't get full


### What is page reclaim

When kernel is under memory pressure:

* Toss **File-backed** memory pages away

* If pages are dirty, write back to backing file first

* Swap out **Anonymous** pages

### What is swap?

Move memory pages into swap space

* Demo: look at `free -mh`

Can be a swap file, partition, or compressed RAM

* Demo: see `zram` with `lsblk`

Uses least recently used (LRU) algorithm

### OOM

Q: What happens when you run out of memory?

Answer: out of memory killer is activated to kill a memory-hogging process

Demo: look at `mm/oom_kill.c`

### Page allocation: buddy system

Pages allocation in power-of-two groups

Use `get_free_pages()` API

You can go around the slab allocators

## Summary

* `fork()` is a mirage

* Virtual memory is not strictly required

* Virtual memory provides important protections

* The kernel contains multiple memory allocators

* The slab allocators rely on the page allocator on the backend

* There are many aspects to the kernel memory management system beyond this intro

* We are only scratching the surface
