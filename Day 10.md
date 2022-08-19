# Exercises of Chapter 4 part 2
## 3. Exercise: sum_cube_odd
```Ocaml
let rec ( -- ) i j = if i > j then [] else i :: i + 1 – j;;

let sum_cube_odd n =
  let l = 0 -- n in
    let odd_filter = List.filter (fun x -> x mod 2 = 1) l in 
      let odd_cube = List.map (fun x -> x * x * x) odd_filter in
        List.fold_left (+) 0 odd_cube
 ```
## 4. Exercise: sum_cube_odd pipeline
```Ocaml
let rec ( -- ) i j = if i > j then [] else i :: i + 1 -- j;;

let sum_cube_odd_p n =
  0 -- n
  |> List.filter (fun x -> x mod 2 = 1)
  |> List.map (fun x -> x * x * x)
  |> List.fold_left (+) 0 
```
