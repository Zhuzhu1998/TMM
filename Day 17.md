# Exercises of Chapter 8 
## 1. Exercise: hashtbl usage
```Ocaml
let ( -- ) i j =
   let rec from i j l =
     if i > j then l
     else from i (j - 1) (j :: l)
   in from i j [];;
let tab = Hashtbl.create 16;;
let ans = List.map (fun x -> (x, string_of_int x)) (1 -- 31) ;;
List.iter (fun (k, v) -> Hashtbl.add tab k v) ans;;
```
**Notice:**  
**Refer to [Hashtbl.create]( https://v2.ocaml.org/api/Hashtbl.html#VALcreate)**  
> Hashtbl.create n creates a new, empty hash table, with initial size n.
