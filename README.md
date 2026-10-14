<!-- solve-problem:b0f3ec9b-2d48-4846-bfca-da38fd7bcbea -->
# Shub–Smale integer-root τ conjecture

A [Tangle Solve problem](https://solve.tangle.tools/problems/b0f3ec9b-2d48-4846-bfca-da38fd7bcbea).

## What is the problem?

The τ-conjecture concerns straight-line programs (SLPs) over the integers without constants: an SLP of length τ is a sequence f₀, …, f_τ where f₀ = x (a single variable), and each fᵢ is either fⱼ + f_k, fⱼ − f_k, or fⱼ · f_k for j, k < i, or the variable x. This computes an integer polynomial f ∈ ℤ[x]. (Variants allow constants; the "constant-free" version uses only the variable and built-in constants, typically 1.)

**Conjecture (Shub–Smale, 1995):** There exists a universal constant C such that every nonzero integer polynomial computed by a constant-free SLP of length τ has at most (τ+1)^C distinct integer roots.

Equivalently: the number of integer roots of f is polynomially bounded in its straight-line complexity τ(f). Note the conjecture says nothing about rational, real, or complex roots — only integer roots, and only distinct ones. The key subtlety: τ(f) can be logarithmic in the degree (e.g., x^(2^τ) has τ-complexity τ), so no bound purely in terms of degree works; the conjecture asserts computation structure itself limits integer roots.

## Why does it matter?

A proof would yield explicit lower bounds: any polynomial with super-polynomially many integer roots (e.g., ∏_{i=1}^{m}(x − i), which has ~log m! … but more crucially multivariate versions) would require super-polynomial SLP size — giving lower bounds in the Blum–Shub–Smale (BSS) algebraic model of computation, and implying NP ≠ P over ℂ in Shub–Smale's program. It is one of the few plausible routes to lower bounds for explicit polynomials. It also connects to polynomial identity testing and univariate "fewnomial"-style real-root bounds. If it stays open, virtually all explicit lower bounds for arithmetic circuits over ℂ remain out of reach.

## What's already known?

- No nontrivial general bound is known: the best known upper bound on integer roots in terms of τ is essentially trivial (degree ≤ 2^τ roots).
- **Chen–Christandl–Sagert (2018, ~SIAM J. Computing 2022):** The conjecture holds (with a matching (τ+1)^2-style bound, verify exact exponent) for *sums of powers of monomials* — i.e., polynomials ∑ cᵢ x^{aᵢ} with bounded straight-line complexity of the exponents and coefficients. This is the largest known class.
- **Tavenas:** bounds on the number of real roots of sparse polynomials via fewnomial-type results, in terms of sparsity rather than τ.
- **Pila / height-based bounds** (e.g., via Descartes, Fewnomials): relate integer roots to coefficient structure, but coefficients of SLPs can have enormous bit size, so these give nothing in terms of τ.
- Known lower bounds on the number of roots achievable: polynomials with τ-complexity O(m) having ~m² integer roots exist (products like ∏(x−i) have small τ if the i's have small τ), suggesting at least quadratic root counts are possible — a polynomial bound must accommodate this.
- The conjecture is known to imply lower bounds against constant-free arithmetic circuits (Bürgisser's book, Chap. 8-adjacent material, verify chapter).

## What would count as solving it?

- **Full solution:** a proof that |{integer roots of f}| ≤ (τ(f)+1)^C for all nonzero f, for some absolute constant C.
- **Partial progress worth publishing:** (a) any bound sub-2^τ for general constant-free SLPs; (b) extension of the Chen–Christandl–Sagert class (e.g., to sums of products of powers, or depth-3/depth-4 circuits); (c) a lower bound construction showing the optimal C ≥ some constant (e.g., polynomials of τ-complexity O(m) with Ω(m^k) integer roots for k ≥ 3, if it exists).
- Criterion a referee accepts: a rigorous bound valid for *all* SLP-computable polynomials in the stated class, with explicit C.

## How to start

1. Read Shub–Smale (1995) §on the τ-conjecture (it appears with the "α" theory of addition chains), then Bürgisser's *Completeness and Reduction in Algebraic Complexity Theory* for the framing of τ-type conjectures.
2. Read Chen–Christandl–Sagert carefully — its method (Descartes' rule + "same support ⇒ few roots" arguments with exponent complexity) is the state of the art; identify exactly where it fails beyond sums of powers of monomials.
3. Try depth-3 (ΣΠΣ) or ΣΠΣ circuits over ℤ[x] with unit constants: does the conjecture hold there? Exponent vectors of products interact multiplicatively; control may be possible via S-unit/linear-forms-in-logs tools.
4. Main obstacle: multiplication nodes create polynomials with huge coefficient heights and interleaved supports; no known real-root-counting tool (Descartes, Khovanskii fewnomials) is τ-aware.

## Key references

- M. Shub, S. Smale, "On the intractability of Hilbert's Nullstellensatz and an algebraic version of 'NP ≠ P ≠ co-NP'", Bull. AMS 33 (1995) — defines the τ-conjecture within the BSS/algebraic NP ≠ P program.
- P. Bürgisser, *Completeness and Reduction in Algebraic Complexity Theory*, Springer 2000 — situates τ-type conjectures, including relations to lower bounds and degeneracy of the constant-free model.
- X. Chen, M. Christandl, D. Sauermann (note: correct author list is Chen–Christandl–Sauermann; "Sagert" appears in later variants — verify), "On the Shub–Smale τ-conjecture for sums of powers of monomials", SIAM/related venue (2018/2022, verify) — proves the conjecture for sums of powers of monomials with exponents of bounded straight-line complexity.
- A. Khovanskii, *Fewnomials*, AMS 1991 — real-root bounds for sparse polynomials, the toolbox behind partial results.
- S. Tavenas, "On the intersection between sparse polynomials", / real-root bounds for structured polynomials (verify exact paper) — sharpened fewnomial-type counts.

## Warnings

- The constant-free model matters: allowing arbitrary integer constants makes the conjecture false as stated in some formulations (constants of huge τ encode many roots cheaply) — pin down which convention you use; Shub–Smale's version forbids constants other than the variable (and sometimes 1).
- Don't attempt bounds via degree: degree is exponentially larger than τ; the conjecture is genuinely about computation.
- Descartes-based arguments fail because SLP coefficients have doubly-exponential bit lengths; bounds in terms of coefficient height are useless here.
- The multivariate/two-variable analogue (conjectured by Shub–Smale for real zero-sets) is strictly harder; stick to univariate integer roots.
- Author attribution of the sums-of-powers result varies across citations (Chen–Christandl–Sauermann vs. "Sagert") — verify before citing.

---
*`ALGO-000047` · unverified*

## Acceptance guidance

- **Full solution:** a proof that |{integer roots of f}| ≤ (τ(f)+1)^C for all nonzero f, for some absolute constant C.
- **Partial progress worth publishing:** (a) any bound sub-2^τ for general constant-free SLPs; (b) extension of the Chen–Christandl–Sagert class (e.g., to sums of products of powers, or depth-3/depth-4 circuits); (c) a lower bound construction showing the optimal C ≥ some constant (e.g., polynomials of τ-complexity O(m) with Ω(m^k) integer roots for k ≥ 3, if it exists).
- Criterion a referee accepts: a rigorous bound valid for *all* SLP-computable polynomials in the stated class, with explicit C.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/b0f3ec9b-2d48-4846-bfca-da38fd7bcbea?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000047.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000047)
