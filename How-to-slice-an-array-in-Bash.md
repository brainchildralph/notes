## Bash Notes
---

### How to slice an array in Bash
[Parameter Extension](https://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

```
A=( foo bar "a  b c" 42 )
B=("${A[@]:1:2}")
C=("${A[@]:1}")       # slice to the end of the array
echo "${B[@]}"        # bar a  b c
echo "${B[1]}"        # a  b c
echo "${C[@]}"        # bar a  b c 42
echo "${C[@]: -2:2}"  # a  b c 42 # The space before the - is necesssary
```

---



