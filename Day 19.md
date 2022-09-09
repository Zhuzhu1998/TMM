# Exercises of Chapter 8 
## 2. Exercise: hashtbl stats
```Ocaml
let buckets h = (Hashtbl.stats h).num_buckets;;
```

## 3. Exercise: hashtbl bindings
```Ocaml
let bindings h = Hashtbl.fold (fun k v acc -> (k, v) :: acc) h [];;
```

## 4. Exercise: hashtbl load factor
```Ocaml
let load_factor h =
  let stats = Hashtbl.stats h in
  (float_of_int stats.num_bindings) /. (float_of_int stats.num_buckets);;
```
**Notice:**  
**Familiar with [Standard Library Hashtbl]( https://cs3110.github.io/textbook/chapters/ds/hash_tables.html?highlight=num_buckets#standard-library-hashtbl)**
