- #+BEGIN_QUERY
  {:title "Permanent Note"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "p")]]
  }
  #+END_QUERY