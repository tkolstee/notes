
```toc
```

## Initialization Files
| File              | Usage                                 |
| ----------------- | ------------------------------------- |
| `~/.bash_profile` | Executed for interactive login shells |
| `~/.bashrc`       | Executed on every shell, including noninteractive                                      |

## Manipulating variables
Uppercase first letter: `${var^}`
Uppercase whole string: `${var^^}`
Last n characters of string: `${var: -`*n*`}` (space is significant)

## Displaying error if variable is null or unset
```bash
var="${var_name?:Error \$var_name not set. Bye}"
var="${1?:Error. Die.}"
```

## Syntax Checking
At the top of each script:
```bash
set -euxo pipefail 
```

Short for:
Command|Description
:------|:------
```set -e``` or ```set -o errexit``` | Exit if any command returns !=0
```set -x``` | Print all commands to terminal (like ```sh -x```)
```set -u``` or ```set -o nounset``` | Die on ref to undef variable
```set -o pipefail``` | Propagate errors in pipelines

Use [Shellcheck](https://www.shellcheck.net) (package or online version)

## Arrays
[Source](https://opensource.com/article/18/5/you-dont-know-bash-intro-bash-arrays)

### Defining and filling Arrays

```bash
emptyArray=()                       # empty
allThreads=(1 2 4 8 16 32 64 128)   # assign
allThreads+=( 256 512 1024 2048 )   # append
allThreads[3]=8                     # change value

str=$(ls)     # Save output as string
str=( $(ls) ) # Save output as array of files

${arr[@]:s:n} # Retrieve n elements starting at index s
```

### Retrieving from Arrays
```bash
${arr[2]}  # Get 3rd element
${arr[@]}  # Get all elements
${!arr[@]} # Get array indices
${#arr[@]} # Get array size
arr[0]
```

### Iteration
#### Over array elements
```bash
for t in ${allThreads[@]}; do  
  ./pipeline --threads $t  
done
```

#### Over array indices
```bash
for i in ${!allThreads[@]}; do  
  ./pipeline --threads ${allThreads[$i]}  
done
```

### Adding values to arrays
```bash
myArray+=( "newElement1" "newElement2" )
```


---
# Resources
[pure-bash-bible: Pure bash alternatives to external processes.](https://github.com/dylanaraps/pure-bash-bible)
[Shellcheck](https://www.shellcheck.net)
[You Don't Know Bash: An Introduction to Bash Arrays](https://opensource.com/article/18/5/you-dont-know-bash-intro-bash-arrays)
