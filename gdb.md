# GDB

GDB, the GNU Debugger, is useful for peeking inside binaries.

## Useful GDB commands
- `layout reg`, shortcut for `layout register`: shows windows that contain
  registers and the execution
- `conti`, shortcut for `continue`: continue execution
- `b *0x...`, shortcut for `breakpoint`: break at the memory address `0x...`
- `ni`, shortcut for `next instruction`: go to the next instruction
- `si`, shortcut for `step instruction`: step inside a function call
- `x/16x ...`: view the next 16 bytes of memory of a certain address. e.g.
  `x/16x *0xffffde00` or `x/16x $esp` (for stack pointer)
- `x/16s ...`: view the next 16 null-terminated strings
- `start`: runs the program and breaks in the entrypoint
- `start < ...`: starts the program with input from a certain file

## Useful GDB args
- `gdb -x bin.gdb ./bin`: starts `./bin` on gdb and auto execute the commands
  listed in `bin.gdb`
- `gdb --args ./bin a b`: starts `./bin a b` on gdb
