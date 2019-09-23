# The IOTA bee framework

Bee will be a Rust framework to build IOTA nodes and tools that interact with
the IOTA network. The final product is envisioned to be a highly modular
collection of foundational crates that can be mixed and matched and extended
upon.

Bee is the IOTA Foundation's effort to streamline its different libraries into
one fundamental collection of Rust crates. These will expose foreign function
interfaces (FFIs) to be used in more high level languages and form the basis
for the next iteration of client APIs.

## Motivation

Our primary motivation is to make IOTA an awesome open source project. When
somebody hears about IOTA and checks out bee, they should encounter good
documentation, clear examples of increasing complexity, and well tested code.
We want to make entry to IOTA as straight forward as possible, so that people
can start contributing, extending, and building their ideas on top of the IOTA
network and the bee framework. As such, we want to be ready for both future
iterations as driven by our dev and research teams, as well as for ideas coming
out of the community that we haven't thought of.

One of the Iota Foundation's primary drivers is to only have one central
reference implementation of the most important data structures and algorithms.
To have these verified and eventually certified, it is crucial to have one core
implementation for each of the hashing, signing, and verification procedures.
Going this route, we hope that improvements in either one will quickly propagate
to all other libraries building on these, rather than having to fix each single
implementation we encounter.

Our final motiviation for writing bee is IF's eventual goal to machines of all
performance levels contribute to the IOTA framework, from microcontrollers and
single-board computers, to phones, web browsers, desktop machines and servers.
Next to C and C++, Rust is the only language that fits the requirements and has
the community momentum to cover all these different areas. While C and C++ are
extremely capable languages, we have opted for Rust because of its memory and
safety guarantees and well-integrated tooling.

## Milestones

1. Support Trinity v2
2. Build a node running alongside IRI
3. Build a node running coordicide
