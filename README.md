# The IOTA Bee framework

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
somebody hears about IOTA and checks out Bee, they should encounter good
documentation, clear examples of increasing complexity, and well tested code.
We want to make entry to IOTA as straight forward as possible, so that people
can start contributing, extending, and building their ideas on top of the IOTA
network and the Bee framework. As such, we want to be ready for both future
iterations as driven by our dev and research teams, as well as for ideas coming
out of the community that we haven't thought of.

One of the Iota Foundation's primary drivers is to only have one central
reference implementation of the most important data structures and algorithms.
To have these verified and eventually certified, it is crucial to have one core
implementation for each of the hashing, signing, and verification procedures.
Going this route, we hope that improvements in either one will quickly
propagate to all other libraries building on these, rather than having to fix
each single implementation we encounter.

Our final motiviation for writing Bee is IF's eventual goal to have machines of
all performance levels contribute to the IOTA framework, from microcontrollers
and single-board computers, to phones, web browsers, desktop machines and
servers. We thus want to implement Bee's constituent libraries from the ground
up. You should be able to import each library on its own, and each library
should have as few dependencies as possible. Having microcontrollers in mind,
we want these libraries to not rely on a runtime, which includes language
runtimes such as garbage collection, but also OS integration (which, in the
case of Rust, is provided by its `libstd` standard library). Rust is our
language of choice because we think it fits this bill perfectly. If you want to
read more about our choice, see the [Why Rust? section](README.md#).

## Milestones

The Bee framework was mainly created to support the implementation of the IOTA
[Coordicide](https://coordicide.iota.org/). As previously stated, on the path
to Coordicide we want to make this framework as open, vetted and used as
possible by supporting the creation of tools, clients, nodes...

Here are the proposed milestones to achieve this goal.

1. **Fundamental crates** - Specification and implementation of the Bee
   fundamental crates `bee-trinary`, `bee-model`, and `bee-crypto`. These are
   the IOTA essential bricks without which it's not possible to write anything
   IOTA-related.
2. **FFI** - Foreign Function Interface to make the Bee crates available to
   other languages. The first project relying on Bee crates through FFI will be
   Trinity v2.
    + We will also investigate in how far WebAssembly, `wasm`, might be an
      intermediate milestone.
3. **Rust IRI** - Specification and implementation of the node-specific crates
   `bee-network`, `bee-tangle`, `bee-api`, `bee-consensus`, and `bee-gossip`.
   To demonstrate the modularity and robustness of the Bee framework, a node
   for the current mainnet will be implemented. Some of these crates will be
   kept for the Coordicide node.
4. **Coordicide** - Specification and implementation of new Coordicide
   node-specific crates as soon as research specifications are delivered.

## Contributing

Please see
[`bee/CONTRIBUTING.md`](https://github.com/iotaledger/bee/blob/master/CONTRIBUTING.md)
for guidelines on how to contribute. Please note that we have a Review for
Comments (RFC) process in place to propose, discuss, and vote on new features
entering the Bee framework. You can find it at
[`iotaledger/bee-rfcs`](https://github.com/iotaledger/bee-rfcs/).

## Why Rust?

This question inevitably comes up, since Rust is a relatively young language,
so we want to answer it directly in the README.

As laid out in the motivation section, we want to have all sorts of devices run
on the IOTA network: from microcontrollers to phones and servers. We thus need
to consider devices that run with minimal resources and do not provide an
operating system. Microcontrollers aside, we also want energy efficiency to not
boil our oceans and good performance when calculating hashes, and signing and
verifying messages to make the network run well and provide a good user
experience. These requirements alone already restrict the choice of programming
languages to C, C++, Rust, and Ada (and probably a few others we are not aware
of; but the ones mentioned  are the most commonly used with tooling and
resources accessible to normal people).

So, why Rust and not one of the others? While C and C++ are very powerful, they
are also not easy to get right. Rust operates at a comparable performance while
providing much stronger memory safety guarantees. Together with its well
integrated modern tooling, we think it helps us iterating our designs faster
while being more confident that our code does what we intend it to do (without
accessing uninitialized memory, double free, use after free, null pointer
dereference, and buffer overflows that are all security concerns).
