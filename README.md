Script for controlling Linux's dynamic debug

# Usage
```
Usage: dyndbgctl [options] command pattern
  options:
        -e|--enabled Show currently enabled dynamic debugs (for list command)
        -f|--flags   Decoration flags (default: flmt, for enable command)
                       f: Include function name
                       l: Include Line number
                       m: Include module name
                       t: Include thread ID

        -p|--path    Path to dynamic_deubg/control (default: /proc/dynamic_debug/control)
        -h|--help    Show this help message

  command:
        list         Show list of available dynamic debugs
        enable       Enable dynamic debug
        disable      Disable dynamic debug
        reset        Clear all settings

  pattern:           Dynamic debug pattern (for enable/disable)
                     Examples:
                       "file XXX.c", "file dir/subdir/*"
                       "func func_name"
                       "module mod_name"

See https://www.kernel.org/doc/html/latest/admin-guide/dynamic-debug-howto.html for details
```

Example:
```
$ ./dyndbgctl -e list
$ sudo ./dyndbgctl enable "file init/main.c"
enable 6 debugs
$ ./dyndbgctl -e list
init/main.c:1427 [main]run_init_process =pmflt "    %s\012"
init/main.c:1425 [main]run_init_process =pmflt "  with environment:\012"
init/main.c:1424 [main]run_init_process =pmflt "    %s\012"
init/main.c:1422 [main]run_init_process =pmflt "  with arguments:\012"
init/main.c:1216 [main]initcall_blacklisted =pmflt "initcall %s blacklisted\012"
init/main.c:1177 [main]initcall_blacklist =pmflt "blacklisting initcall %s\012"
$ sudo ./dyndbgctl reset
disable 6 debugs
```

# License
GPLv2
