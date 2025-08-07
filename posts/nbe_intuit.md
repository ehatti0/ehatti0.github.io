## Normalization-by-Evaluation, Intuitively

Normalization-by-evaluation (NbE) is a common technique in the implementation of dependently-typed programming languages and proof assistants. A typechecker must check equality of types, and in dependently-typed languages this means checking equality of _programs_. NbE is a family of algorithms that provide an efficient way to do this.

Unfortunately, there's not many approachable high-level explanations of NbE. In this post I will tell you _what_ NbE is and _why_ is works, rather than the _how_ of implementing it.

### The Problem
