# AWK Cheat-Sheet

| Command | Description |
| --- | --- |
| `awk '/pattern/ {print $1}'` | standard Unix shells |
| `awk '/pattern/ {print "$1"}'` | compiled with DJGPP, Cygwin |
| `awk "/pattern/ {print \"$1\"}"` | GnuWin32, UnxUtils, Mingw |
| `awk '1;{print ""}'` | double space a file |
| `awk 'BEGIN{ORS="\n\n"};1'` | double space a file |
| `awk 'NF{print $0 "\n"}'` | double space a file which already has blank lines |
| `awk '1;{print "\n"}'` | triple space a file |
| `awk '{print FNR "\t" $0}' files*` | precede each line by its line number |
| `awk '{print NR "\t" $0}' files*` | precede each line by its line number for all files together |
| `awk '{printf("%5d : %s\n", NR,$0)}'` | number each line of a file |
| `awk 'NF{$0=++a " :" $0};1'` | number each line of a file, but only print numbers if line is not blank |
| `awk 'END{print NR}'` | count lines (emulates "wc -l") |
| `awk '{s=0; for (i=1; i<=NF; i++) s=s+$i; print s}'` | print the sums of the fields of every line |
| `awk '{for (i=1; i<=NF; i++) s=s+$i}; END{print s}'` | add all fields in all lines and print the sum |
| `awk '{for (i=1; i<=NF; i++) if ($i < 0) $i = -$i; print }'` | print every line after replacing each field with its absolute value |
| `awk '{for (i=1; i<=NF; i++) $i = ($i < 0) ? -$i : $i; print }'` | print every line after replacing each field with its absolute value |
| `awk '{ total = total + NF }; END {print total}' file` | print the total number of fields ("words") in all lines |
| `awk '/Beth/{n++}; END {print n+0}' file` | print the total number of lines that contain "Beth" |
| `awk '$1 > max {max=$1; maxline=$0}; END{ print max, maxline}'` | print the largest first field and the line that contains it |
| `awk '{ print NF ":" $0 }'` | print the number of fields in each line, followed by the line |
| `awk '{ print $NF }'` | print the last field of each line |
| `awk '{ field = $NF }; END{ print field }'` | print the last field of the last line |
| `awk 'NF > 4'` | print every line with more than 4 fields |
| `awk '$NF > 4'` | print every line where the value of the last field is > 4 |
