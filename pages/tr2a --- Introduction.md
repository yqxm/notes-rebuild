- #+BEGIN_QUERY
  {:title "Introduction"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "r2a1")]]
  }
  #+END_QUERY
-