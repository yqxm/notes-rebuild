- #+BEGIN_QUERY
  {:title "虚拟内存"
   :query [:find (pull ?p [*])
           :where 
           [?p :block/name ?name]
           [(clojure.string/starts-with? ?name "r1a5")]]
  }
  #+END_QUERY
-