# RISC-V instruction generation

This is a randomised instruction generator for RISC-V, based on the
[Sail model][sail].  Currently it's mildly adapted to
[CHERIoT][cheriot].  A snapshot of the model is in the `model`
directory, and was generated from commit `6d5bece` of [this
fork][cheriot-fork] using the `-ocaml_generators ast` option.

[sail]: https://github.com/rems-project/sail-riscv
[cheriot]: https://cheriot.org/
[cheriot-fork]: https://github.com/bacam/2025-lowrisc-cheriot-sail

Building this currently requires the lem, linksem, and zarith
libraries to be installed.  The easiest way to do this is to install
[Sail using opam][opam].

[opam]: https://github.com/rems-project/sail/wiki/OPAMInstall

To generate a single instruction for CHERIoT, use
```
$ ./main.native  -restrict_registers -allow_custom_2
0x8E51 c.or a2, a2
```
where the `-restrict_registers` option reduces the registers chosen to
a small set so that they will be reused more often, and
`-allow_custom_2` includes instructions in a custom encoding space
that CHERI uses.  The full set of options can be seen with `--help`.

## Licensing

See the `LICENCE` file for details; note that the references to PPrint
and ASL code refer to code in the Sail repository that is not present
here.  Recent work on the CHERIoT architecture was performed for
lowRISC CIC in 2025.
