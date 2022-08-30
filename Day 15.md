# Exercises of Chapter 7 
## 7. Exercise: norm loop
```Ocaml
let norm_loop x =
  let n = ref 0. in
  for i = 0 to Array.length x - 1 do
  n := !n +. (x.(i) ** 2.)
  done;
  sqrt !n
```
## 8. Exercise: normalize loop
```Ocaml
let normalize x =
  let nx = norm x in 
  for i = 0 to Array.length x - 1 
  do x.(i) <- x.(i) /. nx
  done
```
