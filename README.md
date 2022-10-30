Scripts for controlling Linux's dynamic debug

# Usage
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

# License
GPLv2
