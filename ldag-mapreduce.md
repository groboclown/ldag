# LDAG and MapReduce

The LDAG<sub>*L*</sub>​ category provides an algebraic and compositional categorification of the MapReduce paradigm.

Specifically:

* Vertices = Mapped data items,
* Labels = Evaluation keys / priorities,
* Edges = Evaluation dependencies,
* Monoid = Aggregation semantics,
* Fold = Reduce operation,
* Morphisms = Job or data transformations (map/fold rewrites).

LDAG<sub>ℕ</sub> captures both data order and evaluation dependency, absent from naive MapReduce formulations.
