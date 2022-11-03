- #+BEGIN_QUERY
  {:title "Classes"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "r4a6")]]
  }
  #+END_QUERY
-