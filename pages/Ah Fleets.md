- #+BEGIN_QUERY
  {:title "Fleet Note"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "f")]]
  }
  #+END_QUERY