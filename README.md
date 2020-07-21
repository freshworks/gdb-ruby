GDB extension for Ruby (tested with Ruby 2.1, 2.2 and 2.3)

Not just live process, also works with coredump


# Install

Download the gdb_ruby.py and then when invoking gdb:


```
(gdb) source /path/to/gdb_ruby.py
```

or 

```
gdb ... -ex 'source /path/to/gdb_ruby.py' ...
```

To use with coredump:

```
gdb `which ruby` --ex 'source /tmp/gdb_ruby.py' /tmp/core_dump.28467
```

# Usage

To get callstack:

```
(gdb) ruby_bt
```

To get callstack of all threads:

```
(gdb) thread apply all ruby_bt
```

To get callstack of "current" Ruby thread, one holding GVL lock:

```
(gdb) ruby_bt_curr
```

To print local variables:

```
(gdb) ruby_locals
```

To print global variables:

```
(gdb) ruby_globals
```

To print ruby variable from some other variable (like Ruby VM C variable etc, in this case 'klass' local variable in C)

```
(gdb) python print_ruby_value(gdb.parse_and_eval('klass'))
```

