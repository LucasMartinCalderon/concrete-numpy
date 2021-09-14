# What is ConcreteFHE

## Introduction

ConcreteFHE, or Concrete for short, is an open-source framework which aims to simplify the use of so-called fully homomorphic encryption (FHE) for data scientists. FHE is a new powerful cryptographic tool, which allows e.g. servers to perform computations directly on encrypted data, without needing to decrypt first. With FHE, privacy is at the center, and one can build services which ensure full privacy of the user and are the perfect equivalent of their unsecure counterpart. FHE is also a killer feature regarding data breaches: as anything done on the server is done over encrypted data, even if the server is compromised, there is in the end no leak of any kind of useful data.

The Concrete framework is made of several parts:
- a library, called concrete-lib, which contains the core cryptographic API's for computing with FHE
- a compiler, called concrete-compiler, which allows to turn an MLIR program into an FHE program, on the top of concrete-lib
- some frontends, which convert different langages to MLIR, to finally be compiled.

In the first version of Concrete framework, there is a single frontend, called homomorphic numpy (or hnp), which is the equivalent of numpy. With our toolchain, a data scientist can convert a numpy program into an FHE program, without any a-priori knowledge on cryptography.

## Organization of the documentation

Basically, we have divided our documentation into several parts:
- one about basic elements, notably description of the installation, that you are currently reading
- one dedicated to _users_ of Concrete, with tutorials, how-to's and deeper explanations
- and finally, one dedicated to _developpers_ of Concrete, who could be internal or external contributors to the framework

## A work in progress

Concrete is a work in progress, and is currently limited to a certain number of operators and features. In the future, there will be improvements as described in this [section](user/explanation/FUTURE_FEATURES.md).

The main _current_ limits are:
- Concrete is only supporting unsigned integers
- Concrete needs the integer to be less than 7 bits (included)
- Concrete is mostly restricted to scalars (by opposition to tensors). The only exception is the `dot` operator, which can dot a tensor of encrypted values with a tensor of constant values

The first two limits can be taken care of with the use of quantization, as explained a bit further in [this](user/explanation/QUANTIZATION.md) and [this](user/howto/REDUCE_NEEDED_PRECISION.md) parts of the documentation.

The scalar limitation is mainly an engineering issue, and will be fixed in the next release. Today, one needs to split all the tensors into small scalars, which is inconvenient and will be no more needed very soon.