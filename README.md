# Explorations into Labeled Directed Acyclic Graphs

## DAGs and Monoids

I've analyzed [isomorphisms between directed acyclic groups and monoids](ldag-monoid.md), which allows us to apply monoid parallel computation algorithms onto directed acyclic graphs (DAGs) with injected labeling.  This requires adding an *injected* (strictly ordered) labels on the DAGs, which formed a category called LDAG<sub>*L*</sub>.

## DAGs and MapReduce

The application of [LDAG onto MapReduce](ldag-mapreduce.md) allows for extending map-reduce to include evaluation dependencies and data ordering.

