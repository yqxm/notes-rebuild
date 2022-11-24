- #+BEGIN_QUERY
  {:title "DSACPP"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "r3a")]]
  }
  #+END_QUERY
-