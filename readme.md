# Veritas

This repository holds an experimental operating system with the following goals:

 - [ ] Zero blocking behaviors; in the kernel, across syscalls, in userland. 
 - [ ] Userspace code and kernel code is identical; the kernel maintains safety by running a verifier over userspace code before loading and executing, but after verification the userspace code performs cooperative multitasking with the rest of the OS, allowing for a zero-overhead execution environment.
 - [ ] TODO


# Organization

Because operating systems require a fine-tuned knowledge of everything underneath them
(which the author does not posess), Veritas's source code is setup as a journey which includes
market research before final product development.

 - `veritas-research-01` - an EFI program to ensure we can do several important things:
    - [ ] Control which CPU gets hardware & software interrupts and explore limits on how much ~~user-space~~ code can run without interruption.
    - [ ] Print hardware & design initials of hardware control interfaces

 - `veritas-research-02` - an EFI program which builds on top of `veritas-research-01` to add:
    - [ ] "Resource path" API; this will be similar to plan9's filesystem, we plan on explosing everything (incl. data within files; "./path/to/img.png/\*[0,0,256,256]" should return the pixels specified by the box encoded w/ the images' encoding settings; ideally the reader could specify output encodings as well.)
         - The string _strictly after_ a file path (`stuff` in `/path/to/file/stuff`)
    - [ ] Persistent storage capability (w/ possibility of multiple FS drivers) & a userspace API
    - [ ] Network drivers & a userspace API

 - `veritas-research-02` - a basic OS which builds on top of `veritas-research-02` to add:
    - [ ] Verifyer which can read an executable format & decide if the code is "safe to run" given a set of constraints (does the program terminate in < XXX instructions given an environment? does the program read/write to a network system? can the verifier prove the program yields control at least every XXX instructions?)
    - [ ] Ability to load 3rd-party machines using `qemu` or similar with the goal of executing the guest's kernel functions to control hardware that `veritas` currently cannot.

- `veritas-research-03` - TODO






