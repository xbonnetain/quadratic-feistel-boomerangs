# Boomerang Attacks on Quadratic Feistel Ciphers
## New results on KATAN and Simon

This repository contains the source code associated to the article "On Boomerang Attacks on Quadratic Feistel Ciphers" published in ToSC Volume 2023, Issue 3. The first part generates an SMT model searching for boomerang distinguishers on the ciphers KATAN32 and Simon-32/64 while the second part allows to check the distinguishers with C implementations of the ciphers.

###### SMT models are in ./SMT:
- SMT models are generated by katanSMTpython.py and simonSMTpython.py
- Raw outputs of the SMT solver used in the article can be found in ./SMT/out
- SMT outputs can be pretty-printed using `python3 [parse_katan.py|parse_simon.py] <output_file>`
- Pretty-printer also generates code snippets for C verification

Details on the model can be found in Appendix I of the article.

###### Code for experimental tests is in ./verification:
- katan.c contains optimized C code adapted from the reference implementation of Katan's designers (https://www.cs.haifa.ac.il/~orrd/KATAN/katan.c). It checks boomerang distinguishers.
- Simon functions are adapted from the [NSA reference implementation](https://nsacyber.github.io/simon-speck/implementations/ImplementationGuide1.1.pdf).
- simon_rk.c checks related-key boomerang distinguishers,
- simon_rx.c checks rotational-xor boomerang distinguishers,
- simon_rxd.c checks rotational-xor-differential boomerang distinguishers.
