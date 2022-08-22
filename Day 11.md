# Exercises of Chapter 4 
## 5. Exercise: repeat
```Ocaml
let rec exist_rec p = function
    |[] -> false
    |x::xs -> p x || exist_rec p xs ;;

let exist_fold p l = List.fold_left (fun acc x -> acc || p x) false l

let exist_lib p = List.exists p
```
> List.exists : ('a -> bool) -> 'a list -> bool  
>exists f [a1; ...; an] checks if at least one element of the list satisfies the predicate f.


