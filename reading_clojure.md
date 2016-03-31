## Syntax that is not obvious

`defn-` : same as `defn` but visible only within the defined namespace 


`->` : thread as second argument

    (-> "foo" (str "bar") (str "zoo"))
    => "foobarzoo"
    (str (str "foo" "bar") "zoo")
    "foobarzoo"

`->>` : thread as last argument

    (->> "foo" (str "bar") (str "zoo"))
    => "zoobarfoo"
    (str "zoo" (str "bar" "foo"))
    => "zoobarfoo"

`into` : merge two collections either list, vector or hash

    (into () '(1 2 3))
    =>(3 2 1)
    
    (into [] [1 2 3])
    => [1 2 3]
    
    (into {:a 1} {:a 2, :b 3, :c 4})
    => {:a 2, :b 3, :c 4}

`defprotocol` and `defrecord` : define an interface and an implementation

    (defprotocol Fly
      "A simple protocol for flying"
      (fly [this] "Method to fly"))
    
    (defrecord Bird [name species]
      Fly
      (fly [this] (str (:name this) " flies...")))
    
    (extends? Fly Bird)
    -> true
    
    (def crow (Bird. "Crow" "Corvus corax"))
    
    (fly crow)
    -> "Crow flies..."
