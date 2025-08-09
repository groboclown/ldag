# Directed Graph as a Monoid

## The Category

We define a labeled directed graph over *L* (**LDAG**<sub>*L*</sub>) as a family of categories parameterized by the labeling set *L*, where:

* *L* is a finite, totally ordered set (*L*, ≤<sub>*L*</sub>​)
  * ∀*x*,*y*∈*L*, either *x*<*y*, *x*=*y*, or *x*>*y*
* |*L*|≥|*V*| for each DAG *G*=(*V*,*E*,ℓ)
* The labeling function ℓ is injective.
  * As |*L*|≥|*V*|, an injective labeling exists

The injective labeling means that

> ℓ(*u*)=ℓ(*v*)⇒*u*=*v* for all *u*,*v*∈*V*.

### Objects in LDAG<sub>*L*</sub>

An object *G* in LDAG<sub>*L*</sub> is the triple:

> *G*=(*V*,*E*,ℓ)

where:

* *V*: finite set of vertices,
* *E*⊆V×V: a binary relation on *V* that specifies a directed edge from one vertex *u* to another *v* whenever (*u*,*v*)∈*E*,
  * The acyclicity condition of a dag (*V*,*E*) is ensured by requiring that the transitive closure *E*<sup>+</sup> of the relation *E* is irreflexive; i.e. (*v*, *v*) /∈ *E*<sup>+</sup> for all *v*∈*V*.
* ℓ:*V*→*L*: injective labeling of the vertices such that:
  * ℓ(*u*)&lt;<sub>*L*</sub>ℓ(*u*) is a total order on the verticies.

The injectivity implies per-vertex label uniqueness, not uniqueness of the labeling scheme.

Initially, we first look at *E* as acyclic directed edges, and return to this later in a more general digraph.

Also note that a system may not have preference on the injectivity ordering, or it may have strict requirements, as in some scenarios requiring ordered children.  The labeling may also use extended sets to allow for additional features, such as group operations on the labels.

### Morphisms

A morphism *f*:*G*→*H* between labeled DAGs *G*=(*V*,*E*,ℓ) and *H*=(*V*′,*E*′,ℓ′) is a function *f*:*V*→*V*′ satisfying:

* Graph homomorphism:
  > (*u*,*v*)∈*E*⇒(*f*(*u*),*f*(*v*))∈*E*′
* Label order preservation:
  > ℓ(*u*)<ℓ(*v*)⇒ℓ′(*f*(*u*))<ℓ′(*f*(*v*))

This implies that edge structure (including direction) is retained in the homomorphism.

### Identity and Composition

* Identity morphism: id<sub>*G*</sub>(*v*)=*v*, structure- and label-preserving.
* Composition:
  > *f*:*G*→*H*

  > *g*:*H*→*K*⇒*g*∘*f*:*G*→*K*

  also preserves both graph structure and label order.

### As a Category

We can view this LDAG<sub>*L*</sub> as a concrete category:

* Objects: DAGs + labeling,
* Morphisms: graph homomorphisms preserving structure and label order,
* Identity and composition respect both structure and label semantics.

This means that for two LDAG<sub>*L*</sub> to be isomorphic, both the DAGs and labels must be isomorphic.

## Folding

We then define a fold functor:
> ***F***:LDAG<sub>*L*</sub>→**Mon**

where:

* **Mon**: category of monoids, with objects as monoids (*M*,⋅,*e*) and morphisms are monoid homomorphisms.

This functor will evaluate a labeled DAG into a single monoid value by folding over its vertex labels.

### Object Mapping

For an object *G*=(*V*,*E*,ℓ), we define:
> ***F***(*G*)=⋅<sub>*v*∈sorted(*V*,ℓ)</sub>ϕ(*v*)

where:

* ϕ:*V*→*M*: a labeling or interpretation of vertices as monoid elements,
* Vertices are processed in ascending order of ℓ.

Thus, the DAG is folded in label order to produce a single monoid value.

If ϕ is fixed, this becomes a fold over the graph structure itself; if ϕ varies per graph, it could be part of a natural transformation or higher structure.

### Morphism Mapping

Given *f*:*G*→*H* in **LDAG**<sub>ℕ</sub>​, define:
> ***F***(*f*):***F***(*G*)→***F***(*H*)

as a monoid homomorphism that maps folded values consistently.

If ϕ<sub>*H*</sub>∘*f*=ϕ<sub>*G*</sub>ϕ<sub>H</sub>​∘*f*=ϕ<sub>*G*</sub>​, then:
> ***F***(*f*)(⋅ϕ<sub>*G*</sub>(<sub>v</sub>))=⋅ϕ<sub>*H*</sub>(*f*(*v*))

so ***F***(*f*) is the induced monoid morphism from the relabeling of vertex evaluations.

The morphism must satisfy:

* Graph homomorphism condition

  For every edge (*u*→*v*)∈*E*<sub>*G*</sub>​, we must have:
    > (*f*(*u*)→*f*(*v*))∈*E*<sub>*H*</sub>

  This preserves the edge structure.

* Label order preservation condition

  For every pair *u*,*v*∈*V*<sub>*G*</sub>​, if:
  > ℓ<sub>*G*</sub>(*u*)<ℓ<sub>*G*</sub>(*v*) then ℓ<sub>*H*</sub>(*f*(*u*))<ℓ<sub>*H*</sub>(*f*(*v*))

  This ensures the monoidal fold order is respected.

## Further with Digraphs

We can extend this with the more general directed graphs, which allows for cycles.
