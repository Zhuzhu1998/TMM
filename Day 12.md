# Exercises of Chapter 4 
## 6. Exercise: library uncurried
```Ocaml
let uncurried_append (l,e) = List.append l e ;;

let uncurried_compare (c1,c2) = Char.compare c1 c2 ;;

let uncurried_max (n1,n2) = Stdlib.max n1 n2 ;;
```
## 7. Exercise: map composition
```Ocaml
let f1 = List.map f (List.map g lst) ;;

let ( @@ ) f g x = x |> g |> f ;;
let f2 = List.map (f @@ g) l ;;
```

