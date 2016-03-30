## Syntax that is not obvious

`defn-` : same as `defn` but visible only within the defined namespace 


`->` : thread 

    user=> (first (.split (.replace (.toUpperCase "a b c d") "A" "X") " "))
    "X"
    
    ;; Perhaps easier to read:
    user=> (-> "a b c d" 
           .toUpperCase 
           (.replace "A" "X") 
           (.split " ") 
           first)
    "X"
