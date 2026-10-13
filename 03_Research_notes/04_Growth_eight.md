# Growth-eight reductions and open cases

These notes retain their original dates and hypotheses. Later status
pointers distinguish superseded checkpoints from the current report.
Individual source files and linked records are preserved in
[research_notes_sources.zip](research_notes_sources.zip).

## Contents

- [growth12_research_2026-08-17](#source-research-notes-growth12-research-2026-08-17-md)
- [growth8_axis_classification_2026-08-22](#source-research-notes-growth8-axis-classification-2026-08-22-md)
- [growth8_case_ledger_2026-08-22](#source-research-notes-growth8-case-ledger-2026-08-22-md)
- [growth8_checker_pure_exclusion_2026-08-20](#source-research-notes-growth8-checker-pure-exclusion-2026-08-20-md)
- [growth8_diagonal_coordinate_residues_2026-08-23](#source-research-notes-growth8-diagonal-coordinate-residues-2026-08-23-md)
- [growth8_extremal_m4_exclusion_2026-08-22](#source-research-notes-growth8-extremal-m4-exclusion-2026-08-22-md)
- [growth8_m3_additive_boundary_2026-08-23](#source-research-notes-growth8-m3-additive-boundary-2026-08-23-md)
- [growth8_m4_mixed_rank_exclusion_2026-09-04](#source-research-notes-growth8-m4-mixed-rank-exclusion-2026-09-04-md)
- [growth8_m4_partial_rail_obstruction_2026-09-04](#source-research-notes-growth8-m4-partial-rail-obstruction-2026-09-04-md)
- [growth8_m4_pure_additive_normal_form_2026-09-04](#source-research-notes-growth8-m4-pure-additive-normal-form-2026-09-04-md)
- [growth8_mixed_checker_rank_2026-08-22](#source-research-notes-growth8-mixed-checker-rank-2026-08-22-md)
- [growth8_odd_skew_additive_2026-08-23](#source-research-notes-growth8-odd-skew-additive-2026-08-23-md)
- [growth8_primitive_diagonal_boundary_2026-08-23](#source-research-notes-growth8-primitive-diagonal-boundary-2026-08-23-md)
- [growth8_skew_rank_parity_2026-08-22](#source-research-notes-growth8-skew-rank-parity-2026-08-22-md)
- [m4_alternating_half_rail_exclusion_2026-09-06](#source-research-notes-m4-alternating-half-rail-exclusion-2026-09-06-md)
- [m4_full_rail_exclusion_2026-09-06](#source-research-notes-m4-full-rail-exclusion-2026-09-06-md)
- [m4_partial_rail_cap_order_2026-09-04](#source-research-notes-m4-partial-rail-cap-order-2026-09-04-md)
- [m4_partial_rail_progress_2026-09-07](#source-research-notes-m4-partial-rail-progress-2026-09-07-md)
- [rail_occupancy_scope_audit_2026-09-03](#source-research-notes-rail-occupancy-scope-audit-2026-09-03-md)

<a id="source-research-notes-growth12-research-2026-08-17-md"></a>

## growth12_research_2026-08-17

Source: `research-notes/growth12_research_2026-08-17.md`.

### Growth-twelve research log — 17 August 2026

Subsequent status: the unrestricted primitive-diagonal growth-four case is
excluded by the analytic reduction and computer-assisted affine classification
in [the top-boundary note](03_Growth_four.md#source-research-notes-primitive-g4-cap5-symbolic-2026-08-22-md). The
growth-eight cases remain open. The entries below preserve the earlier
checkpoint and its intermediate questions.

#### Active objective and status

The target is the universal periodic statement `g>=12`: every positive-growth
finite-support periodic highway, of any nonzero drift geometry, should gain at least
12 black cells per period.  Since the even-winding theorem gives
`g in 4*Z_{>0}`, it is enough to exclude `g=4` and `g=8`.

**Current status: open.**  The accepted diagonal theorem `W>=10` is an input, not a
solution.  It does not apply to axis or other non-diagonal drift.

#### Known barrier

The residue theorem restricts every growth-four drift to

```text
(+/-1,+/-1), (+/-2,0), (0,+/-2), (+/-2,+/-2),
```

but explicit heading-reset tours realize every skeleton while satisfying all
one-period alternation and signed-residue tests.  They fail only the stabilized
cross-period P3 order.  Therefore no incidence-only strengthening is being reused.

#### New final-wake block route for diagonal drift

For normalized diagonal drift `d=(m,-m)`, translation preserves `t=x+y` and shifts
the longitudinal coordinate by `m`.  After the ant's final exit from an untouched
far-ahead block, the settled black mask must therefore be periodic under
`x -> x+m`.  Its number of black cells in one `m`-column domain is exactly `g`, the
number of odd translation classes.

For `g<=8`, the residue bound gives `m<=4`.  Thus a relaxed block confined
to the full eleven-line strip of an exact `W=10` highway can be filtered by the
necessary conditions:

1. the final mask repeats with period `m` across at least two domains; and
2. its fundamental-domain weight is `g in {4,8}`.

`code/python/explore_width10_low_growth.py` performs this classification while
retaining the accepted once-entry restriction on extremal cells and allowing every
same-side exterior return.  This is presently a research diagnostic.  Even a
complete zero result would exclude only diagonal low-growth highways of transverse
width exactly ten.  Wider diagonal highways and all non-diagonal cases remain
outside this model.

##### Forward/reverse status (bounded evidence only)

The forward boundary search remains incomplete at every useful four- or
eight-column cap.  A separately written reverse search,
`code/python/explore_width10_g4_reverse.py`, starts from the sparse periodic
growth-four terminal masks and exactly undoes each ant turn.  A 100,000-segment
involution audit found no mismatch with the forward dynamics.  The proved
extremal, positive-even-fibre, and signed-residue filters leave 20 period-one and
61 period-two masks at `W=10` before the stronger additive filter below.

At two columns the forward and reverse searches both reach filtered period-one
growth-four masks, so the machinery has a positive local control.  At four columns
the reverse search reached 5,000,005 states with 2,808,260 still queued and no hit;
the forward search reached a 50,000,000-state cap and its two period-two
growth-four terminal events both failed the proved wake filters.  Neither run is
complete, so neither is an exclusion.  The same forward run already contains three
filtered growth-eight period-two terminals.  The local four-column relaxation
therefore cannot by itself exclude growth eight.

At eight columns the first filtered `g=12,m=2` mask is exactly the settled standard
period-104 wake, independently reconstructed from its twelve strand bases.  This is
a positive control, not evidence for uniqueness.

#### Full diagonal additive-weight audit

The complete local mod-four charge criterion gives more diagonal weights than the
subfamily used in P22.  For `d=(m,-m)`, put `r=x mod m` and `t=x+y`.  Every
drift-periodic weight obeys

```text
w[r,t] + w[r+1,t+1] + w[r,t+1] + w[r+1,t+2] = 0 (mod 4),
```

so two consecutive transverse rows determine the whole weight.  If
`A_t=sum_r w[r,t]`, the potential monodromy along the drift is
`A_t-A_(t+1)`.  Widget cancellation therefore gives the necessary wake equation

```text
sum_i w[x_i mod m, x_i+y_i] + A_p - A_(p+1) = 0 (mod 4),
```

where `p` is the transverse coordinate of the period-start ant.

`code/python/full_additive_wake_audit.py` enumerates all 16 weights for `m=1` and
all 256 for `m=2`.  All equations hold on the primitive-diagonal growth-four
near-model, the even-diagonal growth-four near-model, and the standard highway.
Thus these weights do **not** close growth four.  They do sharpen the even-diagonal
wake arithmetic: after shifting the common wake parity so its minimum transverse
line is zero, the four wake labels must satisfy

```text
sum_i (t_i/2) = 3 (mod 4),
```

which lifts the older `sum_i t_i = 2 (mod 4)` condition to a mod-eight condition.
At exact `W=10` it reduces the period-two target masks from 61 to 14; the analogous
primitive case reduces 20 to 10.  Valid static masks persist at every tested even
width, so this is a new pruning invariant rather than an all-width contradiction.

#### Tait-connectivity route: ruled out

A second attempted shortcut was to connect growth to transverse span through the
Tait graph of the settled wake.  It does not work.  The endpoint decomposition

```text
B_(n+1)-B_n = (S+n*d) + (A+(n+1)*d) - (A+n*d)
```

does not make the emitted strand representatives `S+n*d` a connected graph: the
moving widget can supply bridges which the negative widget term then deletes, and
individual strand representatives can be shifted by multiples of `d` without
changing the highway.  Even the canonical twelve-strand base set of the standard
highway is a four-component Tait forest, although a different, dynamically aligned
set of twelve edges is shed as a tree.

There are two independent sharp obstructions.  First, the exact-width-ten relaxed
dynamics reaches a period-one growth-four mask with base rows `{0,1,2,10}`; it
satisfies P22 and every additive mod-four wake equation, but its upper strand is a
different Tait component from the three lower strands.  Thus literal local
chronology plus both extrema does not force settled top-to-bottom connectivity.
Second, even if such connectivity were assumed, a Tait edge on an odd transverse
level advances the Tait-vertex transverse coordinate by two.  Connectivity would
therefore imply only `g >= W/2 + 2`, not `g >= W + 2`.  An eight-edge Tait tree
spanning `W=10` satisfies the growth, P22, and full additive moment conditions.

Consequently neither settled-wake connectivity nor a component-diameter bound can
prove `g>=12`.  Any viable next argument must retain the actual lifted-time P3
adjacency (or an equivalent cross-period chronological invariant); connectivity of
an arbitrarily chosen endpoint representative set is not invariant data.

#### Bounded nonlinear local-invariant audit

`code/python/local_pair_invariant_audit.py` tests whether the missing obstruction is
a small pair-correlation charge.  The first ansatz contains the global black count,
all black-pair counts with canonical displacement in `[-2,2]^2`, and a heading
correction with every algebraic-normal-form monomial of degree at most two in the
ant's `3x3` black neighbourhood.  A second search permits every coefficient to
depend on `(x mod 2,y mod 2)`, the most immediate coordinate-periodic refinement for
the axis `d=(2,0)` case.  Both expand every one-step identity exactly as a
multilinear Boolean polynomial, over `Z/2` and `Z/4`; no random states or finite
spatial box are used.

The exact linear/module audit has 197 unknown coefficients and reports only the
known constant and black-count/heading charges.  The 788-coefficient period-two
extension likewise has no solution with a nonzero pair coefficient over either
ring.  This closes one finite radius/degree/coordinate-period ansatz only.  It is
**not** a classification of arbitrary-range, higher-degree, or aperiodically
weighted invariants, and it supplies no growth exclusion.

#### Axis growth four: exact transition-system boundary

Normalize the saturated axis case to `d=(2,0)`.  P22 fixes its four odd classes
to

```text
(0,y0), (1,y0), (0,y1), (1,y1),     y1-y0 positive and even.
```

There is a useful proved mod-two normal form on the two-column quotient cylinder.
At every class, each ant visit uses one horizontal and one vertical incident edge,
so the boundary of each of the horizontal and vertical edge-parity chains is the
set of four odd classes.  The cylinder's vertical graph is a line in each residue;
therefore every vertical edge strictly between `y0` and `y1` occurs oddly in each
residue, and every other vertical edge occurs evenly.  On a non-wake row the two
parallel horizontal edge types have equal parity; on either wake row they have
opposite parity.  The sum of the wrap-edge parities is one because the lifted trace
has winding one.  Thus the quotient contains forced vertical wake intervals and
wake-row horizontal defects, plus an unbounded collection of optional horizontal
two-edge winding cycles.  Those optional cycles can themselves carry nonzero
quotient voltage, so the normal form does not select a unique winding component.
This is a structural reduction, not an exclusion.

`code/python/axis_g4_transition_audit.py` made the former sharp obstruction literal.  It
builds two square-lattice successor circuits with total voltage one and total turn
excess four.  With phases `0,...,7`, every translation class is in exact lifted-time
P3 order: two middle classes have word `RL`, and the four wake classes are singleton
`R`.  Cross-splicing the two circuits into the one-circuit word `RLRRLRRR` creates
exactly one P3 defect.  This isolated the single-tour issue that the rank-parity
theorem below now resolves without bounding the number of zero-voltage components.

The naive parity version is false.  The zero-voltage circuit `RRRRLLLL` is P3-valid
relative to the external drift `(2,0)`, has only even classes, and can be translated
to unused rows.  Appending it produces a P3-compatible three-circuit system with the
same growth and voltage.  Hence neither the parity nor the raw number of successor
circuits is controlled.  None of these multi-circuit objects is a periodic highway.

#### Axis growth four: proved all-period exclusion

The missing single-tour constraint has now been obtained as a permutation-sign
identity.  This is an **analytic theorem**, not a bounded search and not a
computer-assisted premise.

Normalize an axis-growth-four candidate to drift `d=(2,0)`, translate its period
start to the origin, and choose a phase whose arrival heading is vertical.  Write
`N=2M`.  In each quotient class `(x mod 2,y)`, order the event phases by decreasing
`x`, then increasing phase; this is exactly the stabilized P3 order.  If `r_i` is
the zero-based rank of event `i`, define

```text
K = sum(r_i : turn i is L)  (mod 2).
```

For **every** heading-reset one-tour word with endpoint `(2,0)`, independent of its
growth or of P3,

```text
K = 1 + N/4  (mod 2).                         (A)
```

Pair the moves into `M` horizontal-then-vertical macros.  The quotient has a
vertical-arrival vertex `Q_y` and a horizontal-arrival vertex `C_y` on every used
row.  At a vertex, sort occurrences by stable rank and let `a_r,b_r` be the positive
incoming/outgoing port bits.  If `I(a)` counts inversions `1...0`, then

```text
I(a) = A(n-1) + sum(r a_r) + binom(A,2)  (mod 2).
```

At `Q`, an `L` turn means `a!=b`; at `C` it means `a=b`.  Summing the resulting local
identities cancels every directed-edge binomial twice and cancels the linear terms
by vertical cut balance.  Thus

```text
K = sum_v (I(a_v)+I(b_v)) + sum_y binom(h_y,2),
```

where `h_y` is the horizontal multiplicity on row `y`.  Port-sorting factors the
one-cycle phase successor into the local permutations and an edge-block
permutation of parity `E`, so `sum_v(I(a_v)+I(b_v))+E=1`.  If `n_y` counts north
steps from row `y`, closed vertical flow gives

```text
h_y=n_{y-1}+n_y,
E=sum_y n_y + sum_y n_y n_{y+1},
sum_y binom(h_y,2)=sum_y n_y n_{y+1},
M=2 sum_y n_y.
```

Equation (A) follows.  Stable order is preserved inside every directed edge block:
with level `ell=(x-(x mod 2))/2` and key `tau=i-N*ell`, successor along a fixed
quotient edge adds a constant, including at the cyclic period seam.

For a P3-valid word every class is `R,L,R,L,...` in stable order, so every `L` has
odd rank and `K=#L (mod 2)`.  The residue theorem makes an axis `g=4` skeleton
occupy two rows, each with one class in each `x` residue; hence exactly two odd
classes have even checker parity.  If `u_j` is the horizontal macro step and `v_j`
its incoming vertical sign, the even-phase turn sign is `u_j v_j`, and

```text
M + 2 + 0 + 2
  = sum_j (1+u_j+v_j+u_j v_j)
  = sum_j (1+u_j)(1+v_j) = 0  (mod 4).
```

Therefore `N=2M` is divisible by eight.  P3 gives `K=#L=(N-4)/2=0 (mod 2)`, while
(A) gives `K=1`, a contradiction.  Quarter-turn rotations cover all axis directions.

`code/python/axis_rank_parity_audit.py` is a bounded regression for the proof
factorization, not a proof oracle. It checks all endpoint words through period 16.

**Promoted result:** no finite-support periodic highway of growth four has axis
drift, at any period.

#### Even-diagonal growth four: proved all-period exclusion

The same lifted-rank sign has a two-lane form that closes the even-diagonal family
analytically.  At `g=4`, the density bound reduces an even diagonal drift to
`d=(2,-2)` up to quarter-turn rotation.  Put

```text
t=x+y,  r=x mod 2,  ell=(x-r)/2,  tau=i-N*ell.
```

The translation classes are `(t,r)`, ordered by increasing `tau`.  Choose a
vertical-arrival phase at the origin, so vertical-arrival classes `Q` have even
`t` and horizontal-arrival classes `C` have odd `t`.  Define `K` as the sum modulo
two of the stable ranks of all `L` events.

At a class of multiplicity `m`, let `A,B` be its positive incoming/outgoing port
counts and `p=A+B mod 2`.  Positive means north/east at `Q` and east/north at `C`.
If `D=#R-#L`, P3 gives `D in {0,1}`.  The binary inversion identity from the axis
proof gives the following local correction after directed-edge binomials cancel:

```text
Q: p(D+1),       because D = m-2p (mod 4),
C: D(p+1),       because D = 2p-m (mod 4).
```

Let `E` be the edge-block permutation sign when blocks are ordered by
`(t,r,port)`, negative before positive.  Directed-edge blocks preserve `tau`
order, including the period seam, and the phase successor is one even cycle.  Thus

```text
K = 1 + E + L  (mod 2),
```

where `L` is the total local correction.

Write `w,e,s,n` for directed-block multiplicity parities.  Flow is

```text
w[t,r]+e[t,r] = s[t+1,r]+n[t-1,r]                 (Q, t even),
s[j,r]+n[j,r] = w[j+1,1-r]+e[j-1,1-r]             (C, j odd).
```

The residue theorem gives one of the two doubled perfect-matching matrices at
`g=4`.  Hence all four excess-one classes `O` have one checker parity, and each
lane contains two of them.  The needed two-lane lemma is

```text
E+L = sum_r binom(o_r,2)  (mod 2),
```

where `o_r` counts `O` in lane `r`.  It has a direct finite-support proof.

If `O` lies on `C`, every `Q` multiplicity is even.  Hence `w=e=:a` and
`s[j,r]=n[j-2,r]`; the two flow equations and finite support give
`a[t,r]=n[t-1,1-r]`.  Therefore `p=D` at `C`, while the two `Q` corrections on
each level cancel, so `L=0`.  Every bit `n[j,r]=1` contributes the four-edge
parity gadget

```text
G_C(j,r)={N[j,r],S[j+2,r],W[j+1,1-r],E[j+1,1-r]}.
```

Its source order `[N,W,E,S]` and target order `[W,S,N,E]` have odd relative sign.
Two gadgets have odd cross-inversion parity exactly when they are adjacent in the
same lane.  Thus

```text
E = sum n[j,r] + sum n[j,r]n[j+2,r].
```

In each lane this is the number of runs of ones modulo two.  If there are `k_r`
runs, their boundary has `o_r=2k_r` vertices, and
`k_r=binom(o_r,2) mod 2`.  If `O` lies on `Q`, the symmetric reduction uses
`s=n=:b`, `e[t,r]=b[t+1,r]`, and gadgets

```text
G_Q(j,r)={S[j,r],N[j,r],E[j-1,r],W[j+1,r]}.
```

Their source/target orders are `[E,S,N,W]` and `[S,W,E,N]`, with the same
self/cross table.  This proves the lemma in both cases.

For the doubled matching, `o_0=o_1=2`, so `E+L=0` and the one-tour sign gives
`K=1`.  P3 instead makes every `L` rank odd, hence `K=#L`.  Writing `N=2M`, the
horizontal displacement two forces `M` even; since `g=4`,

```text
#L=(N-4)/2=M-2=0 (mod 2).
```

Contradiction.  Quarter-turn rotations cover all even-diagonal signs.

`code/python/even_diagonal_rank_parity_audit.py` checks the local mod-four truth
tables, both gadget permutations, the complete nearby gadget cross table, and all
two-lane finite binary chains through a configurable length.  It is explicitly
labelled bounded evidence, not a proof oracle; the theorem is the displayed
finite-support argument.

**Promoted result:** no finite-support periodic highway of growth four has
even-diagonal drift, at any period. **Open at this checkpoint:** primitive-diagonal
growth four and all growth-eight cases. The later top-boundary result closes the
growth-four case; the target `g>=12` remains open.

<a id="source-research-notes-growth8-axis-classification-2026-08-22-md"></a>

## growth8_axis_classification_2026-08-22

Source: `research-notes/growth8_axis_classification_2026-08-22.md`.

### Axis growth-eight residue structure

There are two axis drift orbits at growth eight, represented by `(2,0)` and
`(4,0)`.  The signed residue theorem, including its exact-row clause for a zero
drift coordinate, determines their coarse wake structure.

#### Drift `(2,0)`

A translation class is labelled by `(x mod 2,y)`, so a fixed row contains at
most two odd classes.  The exact-row signed sum is `0 (mod 4)`.  A row containing
one odd class has signed sum `1` or `-1` and is impossible.  A row containing two
must contain both `x` residues; their checker signs are opposite.

There are eight odd classes, hence exactly four wake-bearing rows. Every such
row is checker-balanced and both `x` residues contain four classes.  P22 says that the
signed sum in either residue is `2 (mod 4)`, so the parities of the four rows split
three to one.  In particular, exactly four odd classes have even checker parity.

The kinematic congruence

```text
N/2 + a + b + A = 0  (mod 4)
```

now gives `N=4 (mod 8)`.  The two-column lifted-rank identity supplies an
independent check: P3 makes `K=#L=(N-8)/2` even, while the kinematic side is
`K=1+N/4`, again forcing `N/4` odd.

#### Drift `(4,0)`

P22 is saturated: each of the four `x` residues contains exactly two odd classes,
and the two in one residue have the same checker sign.  A fixed row contains at
most one class from each residue.  Its exact signed sum is zero modulo four, so a
nonempty row has either two classes of opposite checker sign or all four residues.
In the four-class case the two even and two odd `x` residues make the row
checker-balanced automatically.  Thus every occupied row is balanced and again
`A=4` globally.

With `(a,b)=(4,0)`, the same kinematic congruence gives

```text
N = 0  (mod 8).
```

The coordinate-fibre visit law adds unsigned information to both rows. At
`(2,0)`, each `x mod 2` residue and each of the four wake-bearing exact rows has
visit count two modulo four. At `(4,0)`, every `x mod 4` residue has visit count
zero modulo four, while the visit count of an exact row is congruent to the
number of odd classes on that row. These conditions are compatible with the
classifications above.

At `(2,0)` there is also an exact chronological reduction in
`axis_two_exit_cycles_2026-09-03.md`.  Every last-exit cycle has four vertices
on two adjacent rows and winds once forward; every first-departure cycle has
the same size and winds once backward.  One period decomposes into a last-exit
cycle and four actual closed return excursions.  The note also proves exact
lifetime identities at the trace extremes and restricts which extremes a
last-exit cycle can touch.

The first visits give a further all-period reduction.  There is necessarily
a row whose first vertical-arrival port is `SR` and whose first horizontal-
arrival port is `ER`.  Two coupled closed returns at this row have positive
lengths summing to `N`.  Their signed changes sum to the period's change,
with a correction of zero or two at one root class.  The same note proves
a six-physical-cell bound for heading-reversing returns with unchanged root
colour, but exhibits the inherited-colour cancellation that prevents counting
these cells directly as wake.

Quarter turns cover the other axis directions.  Neither orbit is excluded.
The two-class-per-row argument and the two-column rank identity cannot simply
be reused for `(4,0)`, whose quotient has four residue columns.

<a id="source-research-notes-growth8-case-ledger-2026-08-22-md"></a>

## growth8_case_ledger_2026-08-22

Source: `research-notes/growth8_case_ledger_2026-08-22.md`.

### Growth-eight case ledger

The continuations are dated checkpoints. Later entries supersede earlier
open-case statements; the latest positive-skew continuation is dated 4 October
2026. The earlier ledger below retains the chronology of the intermediate
reductions. No whole growth-eight drift orbit is closed.

#### Continuation: 21 September 2026

The upper `(1,2,2)` fat-cap profile at drift `(1,-3)` is now excluded at every period. The new hand proof uses the existing two-sided normal form: offset-five word B forces a same-cell first return with the wrong immediate successor; word A at the upper cap would require `0>=N+18`. It uses no period cutoff or bound on black lifetimes. See [odd_skew_upper_fat122_exclusion_2026-09-21.md](05_Negative_skew.md#source-research-notes-odd-skew-upper-fat122-exclusion-2026-09-21-md).

Consequently family A in the September 13 wake-family table is closed, including all its P, Q, R and single-ER continuations. The sole remaining recorded family with a lower `(1,2,2)` cap is B, with an upper `(1,2,3)` cap. Other lower-cap profiles remain separate; the entire `(1,-3)` drift orbit is still open. The historical progress entries below retain their original sequence and are superseded by this paragraph where they say family A or its continuations remain open.

The accompanying `verify_upper_fat122_exclusion.py` checks six explicit closed-walk certificates, their half-turns, and the exact integer clock sum. These are checks of the displayed proof certificates, not an end-to-end Lean formalization.

A further hand proof now removes the three `k=0` initial long-row bands at an upper `(1,2,3)` cap with non-wake inward levels three and four. The only possible initial bands are the short row `3:NR,NL`, or the long-row triples `(j,k,l)=(1,1,1),(1,2,0),(2,1,0)`. Family B satisfies these hypotheses. The excluded triples are `(1,0,2),(2,0,1),(3,0,0)`; the first two give upper-clock contradictions, and the third gives incompatible first returns. No wake assumption at level five or deeper, period cutoff, or lifetime bound is used. See [odd_skew_upper_fat123_four_band_reduction_2026-09-21.md](05_Negative_skew.md#source-research-notes-odd-skew-upper-fat123-four-band-reduction-2026-09-21-md). Its checker verifies fifteen closed first-return paths, one translated path, and the exact clock sums `N+10` and `N-2`, the latter positive for `N>=6`. All four retained initial bands remain unresolved. This narrows family B without closing it or the full drift orbit.

#### Continuation: 22 September 2026

Nine lower `(1,2,3)` initial bands are now excluded at every period; see the [combined prefix note](https://drive.google.com/file/d/1mfU0G9CA4g_AQ5sOMl6ni3LIZSCIonUR/view?usp=drivesdk), the separate notes for the [(1,0,2)](https://drive.google.com/file/d/1bZqZeOF4G8RBfFNCvwofZAnTFb7RH66G/view?usp=drivesdk), [(2,0,1)](https://drive.google.com/file/d/1LoaIRb_B3yTyx9DepJwZWnY8CijTNWA9/view?usp=drivesdk), and [(1,1,0)](https://drive.google.com/file/d/1yMnf8752AZVl3OIltWVAm-bisxwpJeWh/view?usp=drivesdk) exclusions, and their exact checkers. With `omega_3=0`, the `(j,k,l)=(1,0,2)` and `(2,0,1)` bands are impossible for either value of `omega_4`. With `omega_3=1`, the entire `(2,0,0)` and `(1,0,1)` bands are impossible for either value of `omega_4`, and `(1,1,0)` is impossible when `omega_4=0`. These remove nine of the twelve lower `(1,2,3)` initial bands in the September 12 normal form. The three remaining bands are `(1,1,1)` with `omega_3=0` and either `omega_4`, plus `(1,1,0)` with `omega_3=omega_4=1`.

At an upper `(1,2,3)` cap with the Family B non-wake offsets five, seven and eight, the retained `(j,k,l)=(2,1,0)` band requires offset six to be wake. In the Family B parameterization this means `r=m-1` (and hence `p+m` even). [Exact upper-prefix checking](https://drive.google.com/file/d/1_yk0wDnHvqU6iMipjClnuYBOtHfwaf70/view?usp=drivesdk) leaves 6,574 integer-clock-feasible prefixes through row ten in this wake-six band; the short band and the `(1,1,1)` and `(1,2,0)` bands also retain checked prefixes. At the lower end of Family B, [level nine is uniquely `(NR,SL)^4`](https://drive.google.com/file/d/1lTHvbL2tO77LIbpUmhiSomBXmmASbkoH/view?usp=drivesdk) for either surviving level-eight word; [exact clocks leave eight or seventeen row-ten words](https://drive.google.com/file/d/1QRIj2VcfNrZtDUEhFqokk_QKEfK_RGE5/view?usp=drivesdk). The three open lower `(1,2,3)` bands have [two `(1,1,1)` prefix frontiers](https://drive.google.com/file/d/1G3oo8l7FQ4fsxYN3iOF5TKxykwBTY4px/view?usp=drivesdk) and [one wake-three level-ten restriction](https://drive.google.com/file/d/1LEC5u2iTryEcVETVk_vs4azwPZLLQDOw/view?usp=drivesdk), each with surviving local prefixes. Other lower-cap profiles remain separate; the full `(1,-3)` orbit is not closed.

#### Continuation: 23 September 2026

The `(j,k,l)=(1,0,2)` exclusion for both values of `omega_4` has been reproduced independently of the 22 September checker. `odd_skew_lower_fat123_a0_102_exclusion_2026-09-22.md` and `code/python/verify_lower_fat123_a0_102_exclusion.py` enumerate without any P22 restriction or cycle extrapolation. Both bands still die at level nine (survivors `4,42,60,452,0` and `4,57,294,3112,0`). A Java explorer with an exact parametric clock (`code/java/StableWordFrontier.java`) and a raw-word reimplementation give the same counts; the latter exhausts about `7.5*10^11` alternating words at level nine.

A new lemma: an upper missing cap whose offsets `5-9,11,12` are non-wake is impossible at every period, with offset ten of either parity. The upper frontier is `2,1,1,2,3,2,5,4,6,0` at offsets three through twelve, and no P22 condition is used. P22 and the rank parity force exactly this schedule when the lower band is `(0,1,1,1,1)`, so **that band has no upper missing cap**. See `odd_skew_upper_missing_quiet_band_2026-09-23.md` and `code/python/verify_upper_missing_quiet_5_12_lemma.py`. The same note records a compression lemma: shifting all wakes above an empty twelve-level gap preserves P22, the rank parity and the moment modulo four. Schedule lists through width `2D+130` are therefore complete for prefixes of depth `D`.

The two cap pairs with a non-fat lower cap and an upper `(1,2,3)` cap are now classified by P22, rank and moment. Lower missing gives families M-I (`W=6m+4`, wakes `{0,1,4,6,6i+4,6k+2,6m+2,6m+4}`, `1<=i<k<=m-1`, `i+k` odd) and M-II (`W=6m+2`, wakes `{0,1,4,7,6k+2,6j+1,6m,6m+2}`, `1<=k<j<=m-1`, `j-k` even); width `0 mod 6` is impossible. Lower guard gives eight families A1, A2, B0-B3, C1, C2. See `lower_missing_upper_fat123_wake_families_2026-09-22.md` and `lower_guard_upper_fat123_wake_families_2026-09-22.md`. P22, rank and moment also force the upper cap of the lower band `(1,1,1,1,0)` to be `(1,2,3)`.

A stronger lemma: **every missing cap, lower or upper, has a wake at inward offset six**. With offset six non-wake and every other offset free, the lower frontier dies at level ten and the upper one at offset twelve, using no P22 condition. See `odd_skew_missing_cap_offset6_2026-09-23.md` and `code/python/verify_missing_cap_offset6_lemma.py`. **Family M-II is therefore impossible**, since level six is non-wake there. For the band `(0,0,1,1,1)` with an upper missing cap, only the upper schedules `{0,1,4,6}` and `{0,1,4,6,10}` through offset fourteen survive; explicit runs kill the other sixteen by offset twelve.

**Hand proofs (23 September, later).** The missing-cap lemmas and the `(1,0,2)` exclusion now have conceptual proofs that do not rest on enumeration.

- `odd_skew_missing_cap_offsets_five_six_2026-09-23.md` proves that every missing cap, lower or upper, has offset five non-wake and offset six wake. The upper-cap statement for offset five is new. The proof uses first returns and two lemmas: a square lemma, and a "two-west" Lemma M that forbids a row once `N_2` is forced right after `W_2`. The clock enters only through one strict inequality at each cap.
- `odd_skew_lower_fat123_a0_102_hand_proof_2026-09-23.md` proves that both `(1,0,2)` bands are impossible. It uses only alternation, ordinal matching and first returns, with no clock. Short closed walks force rows five through eight. A twelve-step return then makes every row-nine word contradictory.

Their walk and word certificates are `code/python/verify_missing_cap_hand_*.py`, `verify_missing_cap_lemma_m.py` and `verify_lower_fat123_a0_102_hand_walks.py`. Consequently the exclusion of family M-II and of the upper missing cap for band `(0,1,1,1,1)` are hand-proved as well.

#### Continuation: 24 September 2026

The upper fat `(1,2,3)` initial `210` band requires a wake at inward offset
five or six. If both are non-wake, exact finite-return and lifted-clock
frontiers eliminate wake-seven at offset seven and both choices at offset
eight, at every period. See [the near-wake note](https://drive.google.com/file/d/1mqGUbyKRnBkpw7SHLoS6uCcMnGJs1UrO/view?usp=drivesdk) and its standalone checker. In lower-missing M-I, upper offsets five and six are both non-wake, so its upper `210` band is impossible. The short, `111`, and `120` upper bands remain.

One of Family B's 25 lower row-ten words has no row-eleven continuation:
`ER EL WR WL WR WL WR WL` after row-eight B. A forced twelve-step,
zero-voltage first return from the sixth west departure on row eleven to its
first north arrival contradicts alternation in every possible count row.
The other 24 words retain exact-clock prefixes. See [the row-ten word
exclusion](https://drive.google.com/file/d/1Pr0_oqlGXC0fuK1QMtexZvIGwbNR1PAb/view?usp=drivesdk).
Across those remaining prefixes, [the lower row-twelve
restriction](https://drive.google.com/file/d/1u4Se35sf5lp4Kui8tQdmL_lcGCxRAHqb/view?usp=drivesdk)
requires at least one `ER` event. For every possible row-eleven prefix,
assuming zero `ER` makes an explicit four-step first return
`12:WL -> 11:SR -> 8:WR -> 9:NR -> 12:EL` force two consecutive
left turns. The checker verifies this path for all 1,150 row-eleven
adjacency prefixes and independently regenerates the 25 row-ten
candidates. The result needs no period or width cutoff. It does not
close Family B.

If Family B row twelve has exactly one `ER`, [a self-contained exact
frontier](https://drive.google.com/file/d/1PCdQeTFBSsCqEKyECAfBQT3n3DaYfRa7/view?usp=drivesdk)
leaves 21 necessary prefixes, all with row-twelve counts
`(ER,EL,WR,WL)=(1,7,9,3)`. They follow only four of the 24 retained
row-ten words. The verifier regenerates all 565 clock-feasible row-eleven
prefixes; at row twelve it checks 532 adjacency words, rejects 272 by
finite wrong returns and 239 by exact integer clocks. Other positive
`ER` counts are separate, and Family B remains open.

The 21 one-`ER` row-twelve prefixes [all have a necessary non-wake
row-thirteen extension](https://drive.google.com/file/d/1X7m7jU0zUGM5yFS-m_ijix0mTTx1i0Un/view?usp=drivesdk).
An exact unbounded integer-clock witness search checks 473 candidate
words and records one extension for each prefix. This rules out a quick
row-thirteen local exclusion in that branch; it does not establish a
highway, and the `ER>=2` row-twelve branch remains separate.

For the lower fat `(1,2,3)` band `(1,1,1,1,0)`, [the all-width wake-family
classification](https://drive.google.com/file/d/1hRowND4nJ_QMMs08Cki1Fw1GQV0za6EI/view?usp=drivesdk)
leaves four parameter families with an upper fat cap. Its width-twelve join
fails by center-row length, so `W>=16`. The upper `210` band survives the
near-wake rule only in the width-`0 mod 6` A edge family. The global wake
coupling removes ten of 104 lower level-nine prefixes; 94 remain.

For the lower fat band `(0,1,1,1,1)`, [two-cap exact frontier
checks](https://drive.google.com/file/d/128TVJGo0RowLD5iBfQlDzKEsk2rZIxHY/view?usp=drivesdk)
exclude all widths through sixteen, giving the necessary bound `W>=18`.
At width eighteen, P22, rank and moment leave four endpoint wake
placements; one fat-upper placement, `{0,2,4,12,14,15,16,18}`, has
disjoint lower and rotated-upper center-row port patterns and is also
excluded. The unique guard-upper placement
`{0,2,4,5,11,16,17,18}` is [excluded by an upper-cap first-return
frontier](https://drive.google.com/file/d/1VHCUx3kRku5yYJgykEAEqUIt2dOqXSRN/view?usp=drivesdk)
that dies at inward offset seven. Fat-upper placement A,
`{0,2,4,6,8,15,16,18}`, is [excluded by its center-row north-arrival
count](https://drive.google.com/file/d/1TBaTy4pFfcQJan7KqMCcO66ROp-7ncwT/view?usp=drivesdk):
the lower frontier requires 11 or 15 arrivals, while the upper frontier
requires exactly 3. The last fat-upper placement B,
`{0,2,4,7,8,10,16,18}`, is also [excluded by a two-cap
join](https://drive.google.com/file/d/1Yy5-XBpZX721pyTniG_Z25gSDOCQP0qn/view?usp=drivesdk):
all 3,520 compatible depth-eight pairs have a witnessed wrong finite
first return before the center row is filled. An independent ordinal-flow
audit reproduces the pairs and contradictions. Thus **all width-eighteen
placements are excluded and `W>=20`** for this lower band. These checks
impose no period cutoff; larger widths remain open.

For the lower fat band `(0,0,1,1,1)` with an upper missing cap,
[P22, rank, moment and the missing-cap offset theorem](https://drive.google.com/file/d/1sshbEJqo670iEmb6o1olPxGxsXQ0Tf9s/view?usp=drivesdk)
leave exactly `W=6m+4` and wakes
`{0,2,6i+2,6j,W-6,W-4,W-1,W}` with `1<=i<j<=m-1` and `i+j`
even. Thus `W>=28`. This is an all-width necessary family, with
surviving wake sets and no stable-word exclusion yet.

An [upper-guard hand lemma](https://drive.google.com/file/d/1a5R7alNlckbtMRDtDnH2EhOVaZW_a2__/view?usp=drivesdk)
excludes wake at inward offset seven after quiet offsets three through
six. The [extended hand proof](https://drive.google.com/file/d/1NRR2rj5_3D3dZkCGmvfNnEHiiYgkF3T3/view?usp=drivesdk)
also excludes non-wake offset seven: 686 exact alternating words leave
only five adjacency-compatible candidates, all with explicit wrong
finite first returns. Thus an upper guard must wake at least one of
offsets three through six. One exact clock identity is needed at row
five; the standard-library certificates use no solver. This lemma needs
no P22, rank, moment, width or period bound. Of the six minimum-width
(`W=20`) guard placements above lower band `(0,0,1,1,1)`, the earlier
wake-seven part excludes three and the stronger lemma excludes a fourth,
`{0,2,7,8,11,18,19,20}`. Two remain at that width; see the
[static corollary](https://drive.google.com/file/d/15Hndl63paAeZ4gF86ytr3k5VPCyfOc8s/view?usp=drivesdk)
and the extended hand proof.

For lower fat band `(0,0,1,1,1)` with an upper guard, the [complete
all-width static classification](https://drive.google.com/file/d/1B_struDCAvKFRDcc5xk1_9I_LiGF4mFz/view?usp=drivesdk)
uses P22, rank, moment and the guard near-wake lemma. Exactly nine
indexed wake families remain. Its finite audit matches the formulas
through width 160, with 11,478 static placements; the algebra gives
the all-width scope. The minimum width is twenty, with precisely the
two placements above. This static classification alone does not exclude
their stable words; the later prefix proof below does.

For lower fat band `(0,1,1,1,1)` and an upper guard, [all-width P22,
rank and moment algebra](https://drive.google.com/file/d/1jT4qX6Q6sKYcr-4J6sW59GNjrM4iKew4/view?usp=drivesdk)
leaves six indexed wake families. The two extra wakes have upper inward
offsets either `(6i+4,6j+4)` or `(6i+1,6j+1)`, with the parity of
`m+i+j` fixed by `W=6m+r`. The stronger guard lemma excludes every
odd-offset family and every even-offset family with `i>=1`. Only even
`i=0` remains: inward wakes four and `6j+4`, `j>=1`, with the moment
parity still required. This cap pair remains open.

At the minimum M-I width `W=22`, the unique wake set is
`{0,1,4,6,10,14,20,22}`. Its upper long `111` band is now
[excluded by a two-cap join](https://drive.google.com/file/d/1xVbCczz0H4Xg4hOI_Abz12_kGCKj1E5K/view?usp=drivesdk):
all 6,948 count-compatible pairs of 302 lower center words and 104 upper
depth-ten prefixes have witnessed wrong finite first returns. Its upper
`120` band is also [excluded by a full-width
join](https://drive.google.com/file/d/1schnV0sFbm66PBuBEZe1sedTNVzwQj8q/view?usp=drivesdk).
The count-filtered upper frontier has 1,800 depth-ten prefixes. Among
133,597 center-count pairs, 133,485 have wrong finite returns and 107
fail relaxed upper clocks. Each of the last five complete row systems
has a replayable twelve-step zero-voltage cycle, checked independently
without a solver. The last width-22 upper short band is now [excluded by
an exhaustive two-cap join](https://drive.google.com/file/d/17fiKl8r5p_d4eW2DOZHAx3ZYqATzJPkk/view?usp=drivesdk).
It leaves 24,240 upper depth-ten prefixes and 1,868,917 center-word
pairs; 1,865,618 have wrong finite returns, 3,141 fail a relaxed upper
clock, and each of the remaining 158 complete row systems has an
independently replayed wrong finite return. Thus M-I requires `W>=28`;
its upper short, `111`, and `120` bands remain open at larger widths.
No period cutoff is imposed.

Three more [upper-guard early-wake prefix
exclusions](https://drive.google.com/file/d/1OcmCPHokRudyLIjnbWGaM1NmwAWkrhT0/view?usp=drivesdk)
now hold at every period. With upper guard rows `0:WR,1:NR,2:WR`, the
patterns `(wake3,quiet4)`, `(quiet3,4,wake5,quiet6,7)`, and
`(quiet3,4,5,wake6,7)` all have empty finite frontiers. Direct raw-word
enumeration gives, respectively, 8, 376, and 992 witnessed wrong first
returns on their terminal rows; the third pattern also uses one explicit
row-five clock identity `2-N>=5`. The first two remove entire all-width
`r2_fibre2_odd_top` and `r2_fibre0_odd_top` families for lower fat band
`(0,0,1,1,1)` with an upper guard. The third removes the
`r4_odd_pair_singleton_near` subfamily with its top odd wake at `W-7`.
Thus the two remaining `W=20` placements are excluded, so that cap pair
requires `W>=22`; of its two static `W=22` placements, only
`{0,2,10,12,18,20,21,22}` survives these local checks. Seven classified
parameter families still have unresolved placements at larger widths.

For the last lower fat `(1,2,3)` band `(1,1,1,1,0)`, a [two-cap width-sixteen
join](https://drive.google.com/file/d/1lSx7-6sLMGRjDoxC5A4L3KnG7_18gZER/view?usp=drivesdk)
excludes its unique `W=16` placement `{0,2,3,4,6,12,14,16}`. Exact
integer-clock frontiers leave 45 lower center prefixes and 1,263 rotated
upper prefixes. Of 2,880 center-count pairs, 2,440 fail a cross-cut
directional count and all 440 balanced pairs have an explicit wrong finite
first return. Together with the earlier `W=12` join, this band now
requires `W>=18`; wider placements remain open.

At `W=18`, the A(1,1) placement `{0,2,3,4,6,8,16,18}` is
[excluded by center-row count
incompatibility](https://drive.google.com/file/d/1amzPL8wb4A8d0k4ldogAgL0cvPpH4_yx/view?usp=drivesdk).
The lower frontier has 48 center states with four count signatures.
The upper frontier has 191 inward-seven states; all 965 possible
inward-eight count options lead to 6,296 inward-nine count options,
none matching a rotated lower signature. Upper row-eight and row-nine
word constraints are omitted in this screen, making it a sound
superset. The other `W=18` placement A(2,2),
`{0,2,3,4,12,14,16,18}`, is also [excluded by an exact two-cap
join](https://drive.google.com/file/d/1PA-n9i3XGMTFSzXAatJLko9vWX25WRcu/view?usp=drivesdk).
The verifier regenerates both cap frontiers from fixed seeds and joins
62 full nineteen-row systems. All 62 balance every directed-edge count
and have an explicit finite wrong first return; a separate
standard-library checker replays every path. With both `W=18`
placements excluded, this cap pair requires `W>=20`. The unique
static `W=20` wake placement is `{0,2,3,4,6,16,18,20}` and remains open.

For lower fat `(0,1,1,1,1)` with an upper guard, the unique static
`W=20` placement `{0,2,4,10,16,18,19,20}` is also
[excluded](https://drive.google.com/file/d/1iVIqAXErMCjiy2GOrULzewOTfWu2uOab/view?usp=drivesdk).
The exact two-cap frontiers yield 76 lower and 124 upper prefixes. A
full-strip count model leaves 31 compatible count-signature pairs, each
with exactly one possible middle-row count pattern. Across 8,254 cap
word pairs, finite-return checking leaves 1,890 row-nine and 7,331
row-ten words. Row eleven has just one adjacency word; its complete
21-row system contains a replayed 56-step zero-voltage wrong return to
row-zero event zero. A separate standard-library checker validates the
word system and path. This guard-cap pair now needs `W>=22`; the same
lower band with a fat upper cap still has open `W=20` placements.

The remaining lower fat `(0,0,1,1,1)` / upper-guard width-22 placement
`{0,2,10,12,18,20,21,22}` is now [excluded by an exact two-cap
join](https://drive.google.com/file/d/1bb2-b6HH45VsDqBFWeSdgkBsIRvjYCTK/view?usp=drivesdk).
The verifier regenerates 2,182 lower and 1,409 upper count-compatible
depth-ten prefixes, then 3,395 lower center prefixes. Of 1,723,256
center-word pairs, 1,722,896 have explicit wrong finite returns and 149
fail a relaxed upper clock. After 25 full-width count rejections, all
455 complete 23-row systems have wrong finite returns. Ten stored paths
pass a separate ordinal-flow replay. The earlier upper-guard prefix
lemma excludes the other width-22 placement and both width-20
placements. There is no static width-24 placement, so this cap pair
requires `W>=26`; its wider schedules remain open.

Open cases in the `(1,-3)` orbit after this continuation:

| Lower cap | Upper cap | Status |
|---|---|---|
| `(1,2,3)` band `(0,0,1,1,1)` | M, G, `(1,2,3)` | open; upper M requires `W>=28` and one wake family; upper G requires `W>=26`, with three static placements at that width |
| `(1,2,3)` band `(0,1,1,1,1)` | G, `(1,2,3)` | open; whole band `W>=20`; guard pair `W>=22`, only even-offset `i=0` family remains |
| `(1,2,3)` band `(1,1,1,1,0)` | `(1,2,3)` only | open; `W>=20`, unique `W=20` static placement `{0,2,3,4,6,16,18,20}`; upper `210` only in A edge |
| `(1,2,2)` family B | `(1,2,3)` | open; 24 lower row-ten words remain, row twelve needs `ER`; all 21 necessary `ER=1` prefixes continue to row thirteen, and `ER>=2` remains open |
| missing, family M-I | `(1,2,3)` | open; `W>=28`; upper `210` excluded throughout, all three other bands excluded at `W=22`; M-II excluded |
| guard, eight families | `(1,2,3)` | open |

Level-by-level search from either cap explodes in each open case. Rows can grow without any known bound, because fully free ports (`WR` at even levels, `SL` at odd levels) stay unconstrained until later rows are built. The whole `(1,-3)` orbit is not closed.

#### Continuation: 30 September 2026 — literal positive skew (1,3)

The new [positive-skew cap reduction](06_Positive_skew.md#source-research-notes-positive-skew-cap-reduction-2026-09-30-md)
works directly at drift `(1,3)` with transverse coordinate `t=3x-y`.
It does not transfer the `(1,-3)` cap lemmas by reflection. At every positive
period and width, the missing `(1,1,0)` profile is impossible at either cap,
and the guard `(1,1,1)` profile is impossible at the lower cap. These have
hand proofs using ordinal directed-edge matching, physical first returns,
and, for the lower guard, one lifted-clock inequality using only `N>0`.
The upper guard remains open: reversing the drift changes that inequality.

The lower `(1,2,2)` cap has a rigid prefix through level seven, independently
of the eight-wake budget and P22. In particular `omega_3=0`, `omega_4=1`,
with rows three and four `WR,WL,ER,WL` and `SR,SL,SR`. The full eight
templates are given in the note. This rigidity is computer-assisted: a
complete raw alternating-word verifier with unbounded integer `N>0` and
strict row order leaves `4,14,15,48,8` states at levels three through seven.
It uses no width, lifetime or period cutoff, period congruence, four-step
gap, or P22 filter. The independent verifier
`code/python/verify_positive_skew_cap_reduction.py` was freshly run to PASS;
its missing and lower-guard frontiers end in zero states. The result is
`results/positive_skew_cap_reduction_missing_guard_thin_audit.json`.

At a lower `(1,2,3)` cap, the third-level short word `WR,EL`, and both long
words with ER after the second WR, contradict `N>0` by direct integer-clock
arguments. A complete finite-domain check then excludes ER-first words
through level seven without P22, a growth budget or a bound on N. A separate
physical-coordinate word generator and Z3 clock independently reproduce
all domains and rejections. Only the ER-between-WR word remains, with
three possible row-four bands: `SR,SL,SR,SL` when `(omega_3,omega_4)=(0,0)`,
that word followed by NR when the bits are `(0,1)`, and `SR,SL,SR` when
the bits are `(1,1)`. The independent check retains 41 necessary local
prefixes through level seven and was freshly rerun successfully.

The three row-four bands of the middle lower-fat word now also have a
separate [hand proof](06_Positive_skew.md#source-research-notes-positive-skew-fat123-middle-hand-rigidity-2026-09-30-md)
from exact timing and physical first returns, audited independently of the
finite search. The ER-first branch exclusion remains computer-assisted.

At growth eight, the last `(omega_3,omega_4)=(1,1)` lower-fat band cannot
meet an upper guard. A new hand argument exhausts the three even width
residues: P22 makes `W=0,2 mod6` impossible with the one remaining wake;
at `W=4 mod6` that wake cannot repair the fixed odd rank. This closes
that entire cap pair at all widths and periods, not the lower band with
other upper caps or the whole orbit.

Both lower fat profiles retain necessary local continuations. The remaining
cap pairs are lower `(1,2,2)` or `(1,2,3)` against upper guard, `(1,2,2)`,
or `(1,2,3)`. **The whole `(1,3)` drift orbit remains open.** These results
do not close the separate `(1,-3)` orbit or assert existence of any candidate.

The [positive-skew two-cap count and word join](06_Positive_skew.md#source-research-notes-positive-skew-width16-exclusion-2026-09-30-md)
now excludes all transverse widths through sixteen, so every remaining
growth-eight candidate has `W>=18`. Counts are unbounded nonnegative
integers, and no upper bound on period or lifetimes is imposed. The
complete prefix-count model is unsatisfiable for even `W=2..14`.
At `W=16`, 6,604 cap count-signature pairs leave exactly three full-strip
count structures. Their 38 cap-word pairs all have explicit wrong physical
first returns before reaching the central row. Independent geometric count
and physical-word implementations reproduce all counts and exclusions.
The width lower bound does not exclude the larger-width families.

Two further all-width hand exclusions follow from P22 and rank. Lower
`(1,2,3)` band C (wake three/four) cannot meet an upper `(1,2,3)` cap with
wake inward offset three. Lower band B (quiet three, wake four) cannot
meet an upper `(1,2,3)` cap with quiet offset three and wake offset four.
The first gives a fibre-sign or parity contradiction with the one remaining
wake; the second leaves a fixed odd rank that the two forced same-fibre
residual wakes cannot change. The complete modulo-twelve regression checks
all unbounded residue shadows and passes. See sections 10--11 of the cap
reduction note. Band C also has quiet lower levels five and seven by P22.

The remaining positive-skew families are lower thin, or lower fat bands
A/B/C, against the upper possibilities in that note. Every remaining
family retains unbounded arithmetic shadows. Exact continuation checks
retain 25,278 lower-thin prefixes through level nine and 1,453 upper-guard
prefixes through inward offset nine after all-width arithmetic schedule
restriction. All 5,552 emitted upper-schedule rejection certificates were
independently replayed. These local survivor domains do not establish
highways and do not close `(1,3)`.

Lower fat band C with an upper `(1,2,3)` cap also requires quiet lower
level eight. Assuming wake eight, P22 eliminates `W=2,4 mod6`; for
`W=0 mod6`, rank forces the only residual wake to be level six, but its
moment is three instead of one. The hand proof and complete residue-order
regression are section 12 of the cap reduction note. Of 225 complete local
band-C prefixes through eight, this removes the 118 wake-eight prefixes
from that cap pair; 107 quiet-eight prefixes remain. The upper `(1,2,2)`
case is separate.

The remaining lower band-C / upper `(1,2,3)` cap pair has a complete
[seven-family endpoint classification](06_Positive_skew.md#source-research-notes-positive-skew-fatc-fat123-wake-families-2026-09-30-md).
With quiet upper offset four, its two residual wakes are one of four
two-parameter families; with wake offset four, its one residual wake
belongs to one of three one-parameter families, with the width parameter
and parity included. The hand derivation exhausts fibre/sign possibilities,
rank and the moment. A direct-coordinate audit matches every accepted
placement through width 120 and all 23 independent unbounded examples.
Each family has arbitrarily large endpoint realizations; chronological
realizability and exclusion remain separate.

#### Continuation: 1 October 2026 — smaller positive-skew obstructions

The [lower-fat ER-first exclusion](06_Positive_skew.md#source-research-notes-positive-skew-fat123-er-first-hand-exclusion-2026-10-01-md)
now has a hand proof at every growth, width and positive period. Ten
zero-voltage physical returns force prefixes on rows five and six,
then four east-arrival turns on seven. Both turns at the third east
arrival on five contradict physical next-visit order or directed
arrival ordinals. The twelve-step EL contradiction passes through a
different copy of row four at step six; its first physical return is
step twelve. A small fresh path/alternation checker and independent
structural audit verify the proof. The prior large finite-domain
certificate remains a separate regression.

The [band-C wake reduction](06_Positive_skew.md#source-research-notes-positive-skew-bandc-schedule-reduction-2026-10-01-md)
uses the fact that growth-eight P22 admits no two disjoint opposite-sign
pairs. Band C has exactly two full fibre sign patterns. Its upper
offset three is quiet with either remaining upper cap. Upper offset
five is also quiet, using a small independently replayed local lemma
for upper `(1,2,2)`. With upper `(1,2,3)`, only four extra wake schedules
through offset nine remain: `{}`, `{4}`, `{4,8}`, `{7}`. The saved
complete upper domain through seven shrinks conditionally from 13,707
to 1,892 prefixes; the reduced domain and source hash are saved in
`results/positive_skew_bandC_upperF123_depth7_pruned_2026-10-01.json`.

For [lower thin bits111 / upper (1,2,2)](06_Positive_skew.md#source-research-notes-positive-skew-tight-thin-reductions-2026-10-01-md),
the exact endpoint family has `W=6m+4`, residual wakes `6q-2,6p-1`,
`2<=q<=p<=m`, and even `m+p+q`. The whole unbounded subfamily
`q<p=m` is now excluded. It forces an isolated upper offset-five wake,
but quiet offsets three/four and wake five require wake six by the
small local lemma. Surviving parameters have `p<=m-1`, or `q=p=m`
with even `m>=4`. Root freshly reran the compact formula audit and
independently replayed all 1,374 physical and two clock rejections.

The [upper-guard local proof](06_Positive_skew.md#source-research-notes-positive-skew-upper-guard-small-hand-obstructions-2026-10-01-md)
also replaces a larger schedule search for the lower-thin / upper-G
pair: the four arithmetic schedules containing upper offset three or
five are excluded by small hand arguments through seven. A fresh
standard-library raw checker examines 574 extensions, and root
separately replays all 566 physical rejections and the single `2+N`
clock contradiction. This arithmetic consequence is restricted to
that lower cap; upper G remains possible in other unresolved branches.

These results restrict entire unbounded subfamilies and shorten
subsequent searches. They do not bound the remaining widths, join the
bulk chronological histories, construct a highway, or close `(1,3)`.
**The whole positive-skew growth-eight orbit remains open.**

#### Further continuation: 1 October 2026 — the entire thin111 member is excluded

The [lower-thin rigidity theorem](06_Positive_skew.md#source-research-notes-positive-skew-lower-thin-hand-rigidity-2026-10-01-md)
now has a full hand proof at every growth, width and positive period.
It exhausts the third/fourth-row forms, uses zero-voltage physical
first returns and two inequalities with N>0 in the lower clock, and
forces all eight c/e/f templates through seven. Root's structural
review, a separate adversarial audit and the fresh fifteen-walk,
eight-template, thirty-two-ordinal-path checker found no gap.
The older large finite certificate remains a regression.

At growth eight the [entire lower-thin 111 wake member](06_Positive_skew.md#source-research-notes-positive-skew-lower-thin-111-exclusion-2026-10-01-md)
is now excluded for every upper cap, width and period. Its fixed signs
force uniform positive fibre zero, uniform negative fibre one, and
the mixed four-class fibre two. The upper extremum has `W=4 mod6`;
upper G and F123 then violate those fixed fibre signs. Upper F122
leaves exactly the family `W=6m+4`, residual wakes `6q-2,6p-1`,
`2<=q<=p<=m`, and even `m+p+q`. Every such shadow has quiet upper
offsets three, four, seven and eight. Offsets five and six wake
exactly when `p=m` and `q=m`, respectively.

The previous isolated-five lemma eliminates `q<p=m`. New weak local
lemmas eliminate both remaining parameter branches: upper F122
quiet offsets three through seven force wake eight, and upper F122
with quiet three/four and wake five/six also forces wake eight.
Each is a complete finite raw-word domain with unbounded `N>=1`,
strict order, no P22/growth/gap-four/period-residue filters,
and no exploratory frontier imports. Root independently replayed
all 10,336 physical-return rejections and eight clock UNSAT systems,
and separately rejected all 2,540 terminal row-eight raw words.

This argument does not depend on the previous width-sixteen exclusion:
eight wakes plus quiet lower levels one/two/three give `W>=10`, and
the exact residual bounds give `W>=16`. The saturated arithmetic
`W=16` case is covered
by the same quiet-eight obstruction. Thus no small-width exception
or coordinate cutoff remains in the 111 exclusion.

All 179 lower-thin 111 prefixes among the 25,278 saved complete
depth-nine prefixes are removed. The 25,099 remaining necessary
prefixes, source hash and theorem reference are saved in
`results/positive_skew_lower_thin_depth9_without111_2026-10-01.json`.
Seven lower-thin wake templates and the fat bands remain unresolved;
the whole `(1,3)` growth-eight orbit remains **open**.

#### Further continuation: 1 October 2026 — upper-six obstruction and tighter remaining thin families

A new checked local obstruction excludes an upper F122 cap with quiet
offsets three/four/five, wake six, and quiet seven through twelve.
Its complete weak-clock necessary domain has 43 prefixes through
eleven and none through twelve. Root independently regenerated every
emitted candidate, recomputed all count-vector domains/raw-word totals,
replayed all 18,561 physical first-return rejections and verified all
10,933 rejected unbounded integer-clock systems. The argument has no
growth assumption or visit/width/period ceiling; the upper clock uses
`+N`, `N>=1`, and strict stable order only.

Combined with P22, rank and moment, this proves that lower band C
with upper F122, quiet upper four and wake upper six must also have
wake upper eight. The remaining endpoint shadow is exactly
`W=6m`, `O={0,2,3,4,6p+2,W-8,W-6,W}`, `m>=4`,
`1<=p<=m-3`, and odd `m+p`. The next residual upper distance is
sixteen modulo twelve, at least sixteen; all upper offsets nine
through fifteen are quiet. See the
[local obstruction and arithmetic proof](06_Positive_skew.md#source-research-notes-positive-skew-bandc-upper6-wake8-reduction-2026-10-01-md).
This excludes the quiet-eight branch, not the whole cap pair.

The [remaining-thin upper reductions](06_Positive_skew.md#source-research-notes-positive-skew-remaining-thin-upper-reductions-2026-10-01-md)
also show that upper F122 quiet three/four with wake five allows
only lower bits 000 or 010, with `W=2 mod6`; its forced wake six/eight
and quiet seven exclude every lower member having wake five or seven
under that upper schedule. Two exact compact endpoint families remain.
For upper quiet three through seven, forced wake eight gives five
exact endpoint families for lower 011/101/110. The complete unbounded
residue DP for all seven remaining lower members has 6,264 accepted
arithmetic residue templates after these local restrictions, versus
20,676 before. These are residue words, not periods or trajectories.
The independent original-coordinate audit checked 1,504,375 candidate
sets at widths ten through 180 and matched every compact formula.

A still stronger [upper-F122 obstruction](06_Positive_skew.md#source-research-notes-positive-skew-upper-thin-quiet34-requires-quiet5-2026-10-01-md)
now says that quiet upper three and four require quiet upper five,
at every growth, width and positive period. The unique wake-five/six
prefix through seven fails at eight for both possible wake bits:
the same SWNE physical first return skips an intervening stable event.
The new exhaustive terminal check rejects all 170 quiet-eight and
202 wake-eight raw words and independently replays every return.
The first-seven-row classification remains computer-assisted;
the terminal obstruction has a hand proof. This excludes both of
the just-classified lower-thin 000/010 upper-wake56 families. The
6,264 residue-template count above describes the intermediate stage;
six additional residue templates for that upper schedule are now removed.

Another complete raw [upper-F122 lemma](06_Positive_skew.md#source-research-notes-positive-skew-upper-thin-quiet6-requires-quiet7-2026-10-01-md)
excludes quiet three through six with wake seven, for either bit eight,
at every growth/width/positive period. The independent generator
exhausts 6,286 words, geometrically replays all 6,255 physical rejects,
and rederives six rejected weak integer-clock systems. Combining it
with band-C fibre signs excludes the **entire C/F122 upper-wake-seven
branch**. C/F122 now has quiet upper seven, and quiet upper four
always requires wake eight. Its quiet-four/quiet-six shadows are four
exact unbounded endpoint families; the quiet-four/wake-six shadow is
the single family above. None is asserted physically realizable.

Applying both stronger local lemmas to the complete remaining-thin
residue DP leaves 5,222 necessary arithmetic residue templates. The
new report, preserving the intermediate report, is
`results/positive_skew_remaining_thin_upperF122_residues_2026-10-01.json`.
Its per-lower-bit counts are 4,238 / 252 / 342 / 10 / 338 / 14 / 28
for 000 / 001 / 010 / 011 / 100 / 101 / 110. The just-excluded
quiet-six/wake-seven cap removes a further 1,036 residue templates.
These counts measure the exact finite residue alphabet, not a
percentage of the full orbit or a number of hypothetical highways.

For band C/upper F123, the empty extra-wake schedule narrows from
112 upper prefixes at seven to 36 at eight and 28 at nine. Independent
non-frontier code regenerated all 2,187 emitted candidates, replayed
2,123 physical rejections and verified the survivors' upper clocks.
The extra-wake-seven schedule has complete survivor counts
17,5,12,78 through eight/nine/ten/eleven; twelve remains incomplete
and has a saved feasible necessary sample, so no exclusion follows.
The separate lower negative-wake-nine domain retains 966 prefixes;
all 194 physical and 2,331 clock rejections were independently checked,
but its quiet-ten extension is explicitly incomplete.

Seven lower-thin members, lower fat bands A/B/C and arbitrary-width
coupled chronology remain unresolved. The full `(1,3)` growth-eight
orbit remains **open**.

#### Further continuation: 1 October 2026 — thin101/110 upper-six cap families closed

The [new all-width exclusion](06_Positive_skew.md#source-research-notes-positive-skew-thin101-110-upper6-exclusion-2026-10-01-md)
removes lower-thin bits 101 and 110 against upper F122 whose wake
offsets through eight are exactly `{0,6}`. P22, rank and moment leave
three exact endpoint families. The previous quiet-twelve upper-six
obstruction forces nearby upper wakes eleven (101), nine (110 at
width four modulo six), or ten with either choice at twelve (110 at
width two modulo six). Every resulting local schedule is now excluded
by a complete weak-clock domain through twelve.

Four independent audits recomputed all exact count-vector/raw-word
domains, regenerated every emitted candidate without the frontier
engine, geometrically replayed all 83,376 physical rejections and
independently proved all 51,064 integer-clock contradictions.
Z3 checks of all 735 distinct clock signatures passed. The clocks
use the upper sign `+N`, integer `N>=1` unbounded above, and strict
stable order only. The growth-eight consequence is therefore not a
bounded period or visit search. All four terminal domains were
completed; the initial unsaturated time-limited stage was explicitly
incomplete and was superseded by a complete run.

The current remaining-thin/F122 arithmetic residue package has
5,210 templates after deleting these twelve templates. The report is
`results/positive_skew_remaining_thin_upperF122_residues_2026-10-01_d.json`.
Lower101 retains ten and lower110 twenty arithmetic residue templates
against their other F122 schedules; their F123 cap families remain
open. Upper G was already excluded for both by the all-width endpoint
classification. Neither whole lower member nor the whole `(1,3)`
orbit is claimed closed. Seven lower-thin members and the remaining
fat-band cap pairs still require coupled chronology at arbitrary width.

#### Further continuation: 1 October 2026 — thin110 upper-fat wake-five family closed

The [upper-F123 local exclusion](06_Positive_skew.md#source-research-notes-positive-skew-upper-fat-quiet34-wake5-exclusion-2026-10-01-md)
proves that quiet offsets three/four and wake five require wake six or
seven. Both choices at eight were exhaustively checked with integer
`N>=1` unbounded above, upper-clock sign `+N`, and strict stable order.
The independent audit regenerated every emitted candidate, rederived
351 exact count vectors and 533,498 raw words, replayed all 158 physical
rejections and proved all 34 rejected clocks in Z3. All checks passed.

For lower-thin110 at growth eight, P22, moment and rank force
`W=6m+4` and wake set `{0,4,5,6,6p+5,W-5,W-2,W}` with
`1<=p<=m-3` and odd `m-p`. Its only residual upper wake is at distance
`6(m-p)-1>=17`, forcing offsets six/seven quiet and contradicting the
local theorem. This excludes the whole cap family for every width and
period. Lower110 against its other caps and the whole `(1,3)` orbit
remain open. The separate all-quiet upper-fat and upper-thin wakes-four/six
explorations have incomplete deeper stages and provide no exclusions.

#### Further continuation: 2 October 2026 — another generic upper-thin exclusion

The [upper-F122 wakes-three/four theorem](06_Positive_skew.md#source-research-notes-positive-skew-upper-thin-wake34-quiet567-exclusion-2026-10-02-md)
excludes quiet offsets five/six/seven for both choices at eight and nine.
The independent all-raw implementation covers 66 count vectors and
5,025 alternating words, with 5,006 physical rejects and one direct
unbounded integer-clock contradiction. At eight, the unique prefixes
for its two bits differ only by a final NR. The terminal hand argument
uses two verified zero-copy returns: north departure three is followed
by east arrival one, and north departure four by east arrival four.
These force adjacent first/fourth east arrivals, skipping two ordinal
arrivals, which is impossible. Initial prefix completeness remains
computer-assisted; the terminal argument enumerates no row-nine words.

For lower-thin110 at growth eight, upper wakes three/four force
`W=6m+2`, residual `6r+5`, `1<=r<=m-2`, and even `m-r`. Its upper
distance is `9+12h`, so upper five through eight are quiet and the
whole all-width cap family is excluded. The generic theorem also
applies to every other lower cap. It removes another 96 thin/F122
arithmetic residue templates, leaving 5,114. A separate global upper
depth-seven filter retains 14,399 of the original 14,412 necessary
prefixes after the four proved generic wake-pattern exclusions.

The [width-eighteen joined proof](06_Positive_skew.md#source-research-notes-positive-skew-thin101-width18-exclusion-2026-10-02-md)
excludes the whole lower-thin101 member at that width. The freshly
audited weak upper seed has 99 prefixes; all 567 joining count vectors
are accounted for, and all 427 emitted words fail by 424 physical
returns or three independently reconstructed original-gauge clocks.
No visit or period ceiling is imposed. Arbitrary widths remain open.

Aggregate counts alone cannot close the saturated thin101/F123
wake-seven/eight family: a separately verified quiet six-row pump
preserves its count state and zero net displacement, producing
counts-only models at every `W=6m>=24`. The saved
`work_positive_skew_thin101_coupling_hand_20261002/coupling_findings.md`
records the exact bridge displacement requirements and the pump.
This is evidence that ordinal/physical/clock coupling is needed, not
a highway construction. The entire `(1,3)` orbit remains **open**.

For the remaining lower011/F123 wake-six family, the
[completed upper-fat rigidity calculation](06_Positive_skew.md#source-research-notes-positive-skew-upper-fat-wake6-rigidity-2026-10-02-md)
reduces all early words through seven to three under the forced quiet
schedule through ten. Its 415 necessary continuations were independently
regenerated; 46,862 physical and 32,929 clock rejections were verified,
with 668 distinct clock signatures checked by Z3. Quiet eleven remains
incomplete and nonempty, so that family is not excluded. All 415 also
pass an independently checked shared event-count period floor; the small
earlier period witnesses are not upper bounds. The full orbit remains open.

#### Further continuation: 3 October 2026 — quiet-bridge chronology

The [quiet-bridge note](06_Positive_skew.md#source-research-notes-positive-skew-quiet-bridge-chronology-2026-10-03-md)
proves a new hand restriction after lower-thin101, conditioned on row
eight `SR SL` and quiet nine/eleven. Three physical `WNES` returns
force `SR10` to be three or four, for either bit at ten. Its horizontal
transfer is therefore `8+omega10` or `4+omega10`. This excludes the
previously exhibited count pump, whose row-ten choice was five. The
aggregate count pump was valid count data; it fails stable chronology.
At width 24, exact two-cap cut counts and displacement additionally
exclude this row-eight variant in the saturated upper-F123 wakes-seven/
eight family. A further complete independently audited fixed-period join
excludes all other quiet row-eight words at that same width, with no
survivors after row twelve. Thus the saturated thin101/F123 wakes-seven/
eight cap family is closed at width 24, and its remaining possible widths
are at least 30. Other cap families and arbitrary widths remain open.

The lower-thin110 / upper-F122 wakes-four/seven quiet band has been
independently checked through upper row twelve with the necessary
shared-period floor `N>=max(62,assigned upper events+34)`, `N=2 mod4`,
and gap four. All 262 count vectors and 38,960 emitted candidates were
regenerated: 12,377 physical rejects, 24,507 clock rejects, and 2,076
necessary survivors. Every survivor passed an original-variable Z3
clock check. Quiet thirteen remains incomplete; this family is open.

Two independently proved earlier checks use translated excursion order
and wrong physical returns through one new-row visit. Together they
reduce the completed row-twelve emissions to 18,470 while retaining all
2,076 survivors. They improve the exact continuation without imposing
a period or visit ceiling. The width-22 lower011 join also has an audited
count domain and complete row-eight join, but its later stages are still
in progress. The entire literal `(1,3)` growth-eight orbit and all ten
drift orbits remain **OPEN**; no arithmetic completion count changed.

#### Further continuation: 4 October 2026 — width-22 thin011 join excluded

The [complete finite join](06_Positive_skew.md#source-research-notes-positive-skew-thin011-width22-exclusion-2026-10-04-md)
excludes lower-thin011 / upper-F123 wake six at width 22, with wake set
`{0,4,6,7,8,16,20,22}`. Independent checks cover all 1,518 parents,
617,021 emitted row-nine words, 135,293 reached row-ten words, 234,821
finite existence domains, and 113,976 imported or new clock rejections.
Exact full counts determine periods 210, 226, or 242, with no arbitrary
period or visit ceiling. The sole terminal clock rejection has two
independent hand contradictions valid for every period. Fresh root hash
checks bind both complete audits to the final sources.

This supersedes the preceding entry's statement that the later width-22
stages are still in progress. The cap family's remaining possible widths
start at 28. Arbitrary widths, other cap families, the full literal `(1,3)`
orbit, and all ten drift orbits remain **OPEN**. The arithmetic template
counts have not changed, and the paper artifacts are unchanged.

#### Earlier ledger and chronological record

This note fixes the finite case split before any further all-period argument is
attempted.  It uses only heading reset, the strand-density bound, the signed
mod-four residue theorem, and the kinematic period congruence.  Chronology, line
parity, and the lifted-rank conditions can only remove rows from this ledger.

Scope correction, 3 September 2026: no whole drift orbit is currently certified
closed here. The earlier `(4,-4)` closure assumed full occupancy of both rails,
which extremal singleton visits do not establish. That proof excludes the
full-rail subfamily. The `(3,-3)` six-rail refinements have the same extra
hypothesis; see `rail_occupancy_scope_audit_2026-09-03.md`.

The 4 September first-entry argument gives the uniform period bound
`N>=6 max(|a|,|b|)+2(|a|+|b|)`. At diagonal drift `(m,-m)`, growth eight
requires `N>=10m+4`; for `m=4`, the period congruence strengthens this to
`N>=48`. The argument also identifies exact integer detour charges summing
to two. Four-step waits have charge one and eight-step waits have charge
zero. See `first_entry_detour_charges_2026-09-04.md`. These lower bounds
do not close an orbit or replace the existing finite-period records.

There is now an explicit infinite family of partial-rail `(4,-4)` boundary
placements passing the rank sign and every drift-periodic additive mod-four
endpoint charge. It is relaxed data, not a family of ant traces. See
`growth8_m4_partial_rail_obstruction_2026-09-04.md`; an exclusion must use
conditions beyond those tests.

The mixed `4+4` arrival-axis split at `(4,-4)` is excluded by the four-lane
rank sign. The remaining branch is pure-horizontal `8+0`. Its complete
additive endpoint condition is the single labelled-height congruence in
`growth8_m4_pure_additive_normal_form_2026-09-04.md`. These are all-period
reductions, but the pure branch and hence the whole orbit remain open.

#### Drift orbits

Write the drift as `d=(a,b)`.  A heading-reset period has even length, so
`a+b` is even and `a,b` have the same parity.  At growth eight the density
bound gives

```text
max(|a|,|b|) <= 4.
```

There are 40 nonzero vectors satisfying these two conditions.  Quarter turns,
which are symmetries of Langton's rule, divide them into ten orbits.  One choice
of representatives is

```text
(1,-1)   (2,0)    (2,-2)   (1,3)    (1,-3)
(3,-3)   (4,0)    (2,4)    (2,-4)   (4,-4).
```

Reflections are not used: they reverse the chirality of the rule and do not
identify two cases in this problem.

#### Coarse residue data

Let `A` be the number of the eight odd translation classes whose strand bases
have even checkerboard parity.  For every nonzero coordinate of the drift, P22
requires the signed sum in each coordinate residue to be `2 (mod 4)`.  The
resulting possibilities are:

| drift representative | unsigned counts in the `x` residues | unsigned counts in the `y` residues | possible `A` | possible `N mod 8` |
|---|---|---|---|---|
| `(1,-1)` | `8` | `8` | `1,3,5,7` | `2,6` |
| `(2,0)` | `2+6` or `4+4` | — | `0,2,4,6,8` | `0,4` |
| `(2,-2)` | `2+6` or `4+4` on both axes | same | `0,2,4,6,8` | `0,4` |
| `(1,3)` | `8` | a permutation of `4+2+2` | `1,3,5,7` | `2,6` |
| `(1,-3)` | `8` | a permutation of `4+2+2` | `1,3,5,7` | `2,6` |
| `(3,-3)` | a permutation of `4+2+2` | a permutation of `4+2+2` | `1,3,5,7` | `2,6` |
| `(4,0)` | `2+2+2+2` | — | `0,2,4,6,8` | `0,4` |
| `(2,4)` | `2+6` | `2+2+2+2` | `2,6` | `0` |
| `(2,-4)` | `2+6` | `2+2+2+2` | `2,6` | `0` |
| `(4,-4)` | `2+2+2+2` | `2+2+2+2` | `0,4,8` | `0` |

Rows and residue labels may of course be permuted by translating the coordinate
origin.  The table records only margins, not the unbounded transverse positions
of the translation classes.

The final column follows from the already proved congruence

```text
N/2 + a + b + A = 0  (mod 4).
```

For example, every odd-coordinate orbit can occur only at period `2` or `6`
modulo eight, while the three density-saturated magnitude-four cases with two
nonzero coordinates can occur only at period zero modulo eight.

The table deliberately stops at the coarse arithmetic layer.  Restoring P3 and
the exact-row part of P22 sharpens both axis rows.  At `(2,0)` there are exactly
four wake-bearing rows, each containing both residues, and `N=4 (mod 8)`.  At `(4,0)`
every occupied row is checker-balanced and `N=0 (mod 8)`.  The proofs are in
`growth8_axis_classification_2026-08-22.md`.

At `(2,0)`, exit-cycle chronology now reduces every last-exit cycle to four
vertices on two adjacent rows, with directions `E,N,E,S`; every first-departure
cycle has directions `W,N,W,S`.  A complete period is the last-exit cycle plus
four actual closed return excursions.  Their wake contribution is not yet
bounded strongly enough to exclude growth eight.  See
`axis_two_exit_cycles_2026-09-03.md` and `cylinder_exit_cycles_2026-09-03.md`.

For a normalized diagonal drift `(m,-m)`, extremal rigidity supplies a second
refinement.  If `alpha,beta` count odd classes on horizontal- and vertical-arrival
levels, then

```text
alpha+beta=8,       alpha=beta=m (mod 2),       alpha>=2.
```

Each rail contains at least one visited singleton, giving the last inequality.
Full occupancy of all `m` lanes has not been proved. Combining the displayed
conditions with the coarse P22 checker counts leaves the ordered splits

```text
m=1: (3,5), (5,3), (7,1)
m=2: (2,6), (4,4), (6,2), (8,0)
m=3: (3,5), (5,3), (7,1)
m=4: (4,4), (8,0).
```

For `m=2`, the `(8,0)` line is the checker-pure subfamily already excluded,
leaving the three mixed lines. The rank argument below excludes only the
full-rail part of the `m=4` row.

The following `(3,-3)` refinement assumes both rails are full. Their six
horizontal singleton classes and the wake-type parity law then force the
`7+1` checker split. Partial-rail candidates are not covered by this refinement.

The orientation of the `7+1` split is fixed. Choose phase zero at a vertical
arrival and translate that cell to the origin. Even transverse levels are then
even-checker and vertical-arrival. The six rail classes and the remaining
horizontal class lie on odd levels, while the one vertical class lies on an even
level. Hence `A=1`, and the period congruence sharpens the `(3,-3)` row to

```text
N=6  (mod 8).
```

This full-rail subfamily cannot contribute a period-58 candidate. The whole
orbit still has both coarse period classes, two and six modulo eight.

The `(3,-3)` placement is sharper than its checker split.  The two rails already
put two horizontal odd classes in every `x mod 3` residue.  The remaining
horizontal class and the one vertical class have opposite checker signs, so P22
forces them into the same `x` residue.  Applying the `y mod 3` clause puts them in
the same `y` residue as well.  If their levels are `h` and `v`, this says

```text
r_h=r_v,       h=v  (mod 3).
```

The three-lane rank sign is compatible with these conditions; it does not remove
the row.

The full additive mod-four family does give one more restriction.  Normalize the
rail levels to `1` and `W+1`, put the two extra classes in lane zero, and set
`k=(v-h)/3`.  Then

```text
k=W+1  (mod 4).
N>=4W+12|k|+2.
```

This rules out transverse width four but not the drift orbit: compatible
placements exist at every even width from six onward. Since `k` is odd, the
period bound is at least `4W+14`. The derivation and audit are in
`growth8_m3_additive_boundary_2026-08-23.md` and
`../code/python/growth8_m3_boundary_audit.py`.

The two odd skew rows also have one additive condition beyond P22.  For
`d=(1,3s)`, set `j=y mod 3` and `n=x-s floor(y/3)` on each odd class.  After
normalizing the period-start checker parity, every candidate satisfies

```text
sum_O (-1)^(n+j)n = 2-s  (mod 4).
```

Together with the three `y mod 3` residue equations, this exhausts the
drift-periodic zero-four-corner weights for these two orbits.  Static placements
still survive in both chiralities.  Their unique quotient parity flows also give
an even-interlacing condition among the three residue fibres.  In the first full
bounded window, 824 of 1,944 additive survivors meet it in each chirality.  See
`growth8_odd_skew_additive_2026-08-23.md`.

There is also a chronological cap restriction for `(1,-3)`.  Normalize a lower
missing-level cap to multiplicities `(1,1,0)` on levels zero through two.  Its
proved wake levels are `0,1,4`.  Exact same-cell returns, together with P22,
now force

```text
omega_6+omega_7 >= 1.
```

Thus this cap contributes at least four wake classes among levels zero through
seven.  The proof uses order-preserving edge matching, not a bounded search;
see `odd_skew_excursions_and_domino_transfer_2026-08-31.md`.  An upper guard
would make both levels six and seven non-wake by P22 and the rank theorem, so
the lower-missing/upper-guard cap pair is excluded at every period.  The direct
proof, including hand proofs of the missing/missing and guard/guard boundary
exclusions, is in `odd_skew_missing_guard_exclusion_2026-09-03.md`.  The reverse
guard/missing orientation was reduced to two necessary wake families in
`odd_skew_guard_missing_families_2026-09-03.md`. The September 9 record
`odd_skew_guard_missing_complete_exclusion_2026-09-09.md` excludes both
families by finite exact local chronology checks without a period or width
cutoff. Thus every remaining candidate has a fat cap, with profile
`(1,2,2)` or `(1,2,3)`, at one or both ends.

The hand argument in `odd_skew_lower_fat_cap_normal_form_2026-09-12.md`
restricts a lower fat cap to fourteen possible five-level stable bands:
two with profile `(1,2,2)` and twelve with profile `(1,2,3)`. In the former,
level three is non-wake and the next two rows are

```text
3: SR,SL,NR,SL
4: WR,WL,ER,WL,WR,EL,[WR]^omega_4.
```

This two-band restriction also holds at an upper `(1,2,2)` cap after a
half-turn of the heading labels. Every lower `(1,2,2)` band requires the
black lifetime on level two to be at least `N+14`; eight of the twelve
lower `(1,2,3)` bands also require a lifetime longer than one period.
These are all-period necessary conditions. No general upper bound on
those lifetimes has been proved, and the drift orbit remains open.

There is a further all-period exclusion inside the lower `(1,2,2)` branch.
If levels four, five, and six are non-wake, a four-visit level six is
impossible: exact returns force a skipped stable visit by level nine,
regardless of the subsequent wake indicators. The remaining eight-visit
level-six row has only four possible stable orders. The hand proof and
the four orders are in `odd_skew_fat122_even_band_2026-09-12.md`.

For a lower `(1,2,3)` cap with a wake on level three, P22 gives a separate
global exclusion: the upper cap cannot be missing, and upper offset three
must be non-wake. All lower levels `5 mod 6`, including level five, must
also be non-wake. The pair argument is included in the normal-form note.

The even-band reduction has since been completed at the next inward
returns: every lower `(1,2,2)` cap must satisfy `omega_4+omega_5>=1`.
When both levels are non-wake, all eight-visit level-six orders fail
exact returns. The remaining five-visit wake row leads to a forced
six-step path of displacement `(1,-3)` between stable events in the
wrong order for `N>=6`. The proof is
`odd_skew_fat122_early_wake_2026-09-12.md`.

For the early wake pattern `(omega_4,omega_5)=(0,1)`, the level-six row
with two `ER` ports forces the wakes `0,5,6,8` and no other wake through
level eight. P22 then excludes both a missing and a guard upper cap;
the upper cap must be fat. An upper `(1,2,3)` cap in this subfamily
requires `W=4 mod 6`. See
`odd_skew_fat122_three_visit_six_2026-09-12.md` for the direct return proof.

The two-sided return argument in
`odd_skew_fat122_two_sided_wake_2026-09-13.md` proves the weaker but
orientation-independent bound `omega_4+omega_5+omega_6>=1` at either
`(1,2,2)` cap. Combining it with P22, rank interlacing, and the additive
moment reduces the lower `0,5,6,8` branch to three necessary wake
families. Their upper caps are respectively `(1,2,2)`, `(1,2,3)`, and
`(1,2,2)`, with a forced upper wake at offset four, two, and five.
Their minimum widths are `26`, `28`, and `22`. In the last family,
upper offset six cannot be the three-visit row: it has six or seven
visits according to its wake indicator. The parameter families and
proof are in `odd_skew_fat122_three_visit_wake_families_2026-09-13.md`.
The subsequent theorem in `odd_skew_fat122_rigid_five_wake_2026-09-13.md`
excludes the six- and seven-visit offset-six rows whenever offsets four
and five have wake indicators `(0,1)`, at either cap. Thus the
three-visit row and the wake pattern `0,5,6,8` are forced throughout
this branch. Applying the theorem at the upper cap excludes family C,
whose wake placement forbids upper offset eight. Families A and B
remain open. Together with the lower early-wake bound, they now cover
every lower `(1,2,2)` cap with level four non-wake. This does not close
the drift orbit or the fat-cap branches with level four wake.

For `omega_4=1` at a `(1,2,2)` cap, the single-`ER` offset-six row
has only words T and U when `omega_5=0`, or word V when `omega_5=1`.
Zero-displacement returns exclude the other prefix groups at either
cap. A lifted-time comparison between the third and fourth east
arrivals on offset eight excludes all these words at the lower cap.
Together with the earlier wake-five result, this proves that every
lower `(1,2,2)` cap has exactly two `ER` ports on offset six. Its
full count row is `(2,1,b-c+e,1+b-c)`, where
`(b,c,e)=(omega_4,omega_5,omega_6)`. The proof is in
`odd_skew_fat122_four_wake_single_er_2026-09-13.md`; no wake
assumptions beyond offset six are used. The sparse two-`ER` lower
continuations and the upper single-`ER` words remain open.
The same delayed-departure comparison also forces the last east
arrival on lower offset six to be `ER`: its east-arrival subsequence
is `ER,EL,ER` or `EL,ER,ER`.

The later reduction in `odd_skew_fat122_five_lower_bands_2026-09-13.md`
forces the last `ER` to be the second south departure on level six.
Consequently every lower `(1,2,2)` cap uses the level-five word starting
`SR,SL`, and its level-six word starts `ER,EL,ER`, with both stable
gaps exactly four. The remaining west-arrival tail is determined by
`(b,c,e)`. This leaves five necessary bands through level six: one for
`(b,c,e)=(0,1,1)`, and two choices of `e` for each of `(b,c)=(1,0)`
and `(1,1)`. When `b=1`, the fourth west departure on level seven is
`SR` followed immediately by `SL`. These are lower-cap restrictions;
the sparse continuations and the rest of the drift orbit remain open.

The four-visit band `(b,c,e)=(1,1,0)` is subsequently excluded in
`odd_skew_fat122_adjacent_wakes_force_six_2026-09-13.md`. Its single
west departure on level nine cannot satisfy the return order for
either turn at the last east arrival on level eight. Thus lower
wakes at both levels four and five force a wake at six, leaving
four necessary bands through level six. The exclusion uses no
conditions on the later wakes or on the period.

For the remaining lower bands with `b=1`, level seven has west
departure sequence `SR,SR,NL,SR,SR`. Its first six stable events
are `SR,SL,SR,NL,SR,SL`; the remaining `k=1-c+e` north right turns
are split before and after the last west departure. When
`(c,e)=(0,1)`, both cannot precede it. When `(c,e)=(1,1)` and the
single north right turn precedes it, levels seven and eight are
forced non-wake and wake respectively, and level eight has only
two possible fifteen-visit words. The all-period proofs are in
`odd_skew_fat122_seventh_level_2026-09-13.md`. These continuations
are still open.

The band `(b,c,e)=(1,0,0)` is excluded in
`odd_skew_fat122_four_only_forces_six_2026-09-13.md`. Both possible
orders of the remaining north arrival on level seven lead to
return contradictions, the longer argument ending at level eleven.
Together with the adjacent-wake exclusion, this forces `omega_6=1`
at every lower `(1,2,2)` cap. The remaining early triples are
`(0,1,1)`, `(1,0,1)`, and `(1,1,1)`; those continuations and the
rest of the drift orbit remain open.

For `(b,c,e)=(1,0,1)`,
`odd_skew_fat122_four_six_wake_order_2026-09-14.md` excludes
the level-seven order with one remaining north right turn on
each side of the last west departure. Both north right turns
must follow it. The surviving level-eight tail, from its third
east arrival, is

```text
ER,EL,WR,WL,ER,EL,WR,WL,(WR,WL)^(1-f),[WR]^g,
f=omega_7, g=omega_8.
```

The same hand-return argument forces `f=0` or `(f,g)=(1,1)`.
It excludes the alternative tail with the eighth south departure
before the last east arrival, but does not close this wake band.
The other early triples and the rest of the orbit remain open.

The surviving tail is subsequently excluded in
`odd_skew_fat122_four_six_band_exclusion_2026-09-14.md`.
A sixteen-step first return fixes the required west departure
on level eleven; this forces a twelve-step first return on
level eight with two right-turn endpoints. Thus the whole
lower band `(b,c,e)=(1,0,1)` is impossible. Every lower
`(1,2,2)` cap now has `omega_5=omega_6=1`, leaving only
the early triples `(0,1,1)` and `(1,1,1)`. These and the
other cap profiles remain open in the `(1,-3)` orbit.

The band `(b,c,e)=(1,1,1)` is also excluded, in
`odd_skew_fat122_adjacent_wake_band_exclusion_2026-09-14.md`.
The north-right-before-last-west order contradicts two lifted
clocks; the north-right-after-last-west order forces a third
west departure on level nine, where only two exist. Therefore
every lower `(1,2,2)` cap has the rigid early triple
`(omega_4,omega_5,omega_6)=(0,1,1)`. Its two previously
recorded wake families A and B are the only remaining cases
with this lower cap. They and the other cap profiles remain
open; the full `(1,-3)` orbit is not excluded.

The upper single-`ER` part of family A is reduced further in
`odd_skew_upper_a_single_er_reduction_2026-09-14.md`. A
zero-displacement left/left return excludes words T and V at
either `(1,2,2)` cap. Under family A's non-wake conditions at
upper offsets seven and eight, word U requires a wake at offset
six (`p=m-1`) and the fixed offset-seven word

```text
SR,SL,NR,NL,NR,SL,NR,NL,NR,NL,SR,SL.
```

The remaining U order and the upper two-`ER` branches are not
excluded. Family B and the other cap profiles also remain open.

For that last U order,
`odd_skew_upper_a_u_forced_tail_2026-09-14.md` excludes a
left turn at the fifth east arrival on offset eight and forces
the endings `ER,EL` on eight, `SR,NL,SR,SL` on nine,
`ER,WL,WR,EL` on ten, and `NL,NR,SL` on eleven. The final
four visits on six have successive gaps exactly four. These
are additional first-return restrictions, not an exclusion of
U or of family A.

`odd_skew_upper_a_u_eighth_words_2026-09-14.md` further
forces the second east arrival on eight to be `EL`, leaving
one ten-visit word and four fourteen-visit words there. In
the fourteen-visit alternatives, the fifth west departure on
nine is `NL`. A comparison of two upper-orientation clocks
forces the last east arrival `H` on twelve to be `EL`; twelve
ends at `H`, or with `H=EL,WR,WL`. These restrictions still
leave the U branch open.

The five offset-eight possibilities reduce to B0 alone in
`odd_skew_upper_a_u_unique_eighth_word_2026-09-14.md`:

```text
WR,WL,ER,WL,WR,EL,WR,EL,WR,EL,WR,WL,ER,EL.
```

The third south departure must precede the third east
arrival, excluding A, B2, and B3. A first-north-arrival
obstruction excludes B1. The remaining B0 word requires
`D1=SR,D2=NL` on nine; its middle departures and the
higher continuation remain open. This does not close U,
family A, or the whole orbit.

The remaining B0 word is excluded in
`odd_skew_upper_a_single_er_exclusion_2026-09-14.md`.
The three possible initial words on ten either force a
skipped return through the first west departures on eleven,
or force the first event on eight to be later than an event
on six which it must precede. This closes the entire upper
single-`ER` branch of family A. Its upper offset six must
now have two `ER` ports. The two-`ER` branches of A,
family B, and the other cap profiles in `(1,-3)` remain open.

The remaining two-`ER` words for family A are reduced in
`odd_skew_upper_a_two_er_normal_form_2026-09-15.md`.
Only the following three pairings through offsets five and
six survive the square-return constraints:

```text
5 A: SR,SL,NR,NL,NR,SL,NR,SL
6 P: ER,EL,ER,WL,WR,WL,[WR]^e;

5 B: NR,SL,SR,NL,NR,SL,NR,SL
6 Q: WR,WL,ER,EL,ER,WL,[WR]^e;
6 R: ER,WL,ER,WL,WR,EL,[WR]^e.
```

Here `e=omega_6` is still zero or one in each form. The
hand derivation excludes seven of thirteen initial local
combinations, leaving these six necessary bands. None of
the three forms, family B, or the full orbit is excluded
by this reduction.

Form R is narrowed in
`odd_skew_upper_a_r_requires_wake_six_2026-09-15.md`:
its `e=0` band is impossible, so R requires `h=1`
and `p=m-1`. With `e=1`, only the following two
offset-seven orders survive:

```text
M: SR,SL,SR,NL,NR,SL,SR,SL,NR,SL,SR,SL;
N: SR,SL,SR,NL,NR,NL,SR,SL.
```

The same note fixes the tail on eight in M and its full
fourteen-visit word in N. Those continuations and both
values of `e` in P and Q remain open. This removes one
complete local band, not form R or the whole orbit.

The M continuation of form R is excluded in
`odd_skew_upper_a_r_middle_exclusion_2026-09-15.md`.
A left/left first return forces the second east arrival
on ten to turn right; in M its resulting square skips
two intervening east arrivals. Only N remains for R.
For N, the eighteen-visit word on nine is fixed, ten
ends `WL,ER,WL,WR,EL`, and eleven ends `NL,NR,SL`.
The last east arrival on twelve is `EL`. These are
further restrictions, not an exclusion of N, P, Q,
family B, or the whole orbit.

The first east arrival on ten is narrowed in
`odd_skew_upper_a_n_first_east_reduction_2026-09-15.md`.
An equal-voltage comparison gives
`tau(S3)-tau(F1)>=16`, where `S3` is the third south
departure on ten. Thus `F1=ER` can only be the first
or second south departure; `F1=EL` can have only zero,
one, or two south departures before it. This leaves
five words on ten, excluding eight of thirteen initial
placements within N. The left-turn word L0, with no
earlier south departure, is then excluded: a forced
square gives `tau(E2)-tau(F1)=12`, while the required
visit order gives a lower bound of twenty. This leaves
four words, R1, R2, L1, and L2. In L1, the second west
departure on eleven must be `NL`; eleven begins
`SR,SL,NR,NL,NR`, and twelve begins `WR,WL,ER`.
The four surviving words, N, and the whole orbit remain
open.

Their west departures on eleven are further restricted in
`odd_skew_upper_a_n_third_west_corridor_2026-09-15.md`.
If the third west departure is `NL`, its predecessor
`U` on ten follows a fixed twelve-step path to `E2`
on eight, with no intervening visit to ten. Hence `U`
must be the last event on ten before `E2`. This forces
the third west departure to be `SR` in R2; in L1 its
only possible north predecessor is the fourth `WR`
on ten. The second west departure is `SR` in both R1
and R2, and the two initial words on eleven for R2 are
fixed. L1 requires `tau(I)-tau(E1)>=16` in either turn
case for its third west departure. These restrictions
leave all four words on ten open.

Form R is now completely excluded at the upper cap of
family A in `odd_skew_upper_a_r_exclusion_2026-09-15.md`.
In its sole remaining continuation N, the upper clock
puts the sixth and seventh west departures on eleven
after all north arrivals except the two fixed final ones.
Its ending is forced to be `SR,SL,SR,NL,NR,SL`.
The corresponding return paths force consecutive east
right turns `G10,G11` on twelve with no possible left
turn between them. Taking `G10=EL` instead gives an
eight-step right/right first return on five. This closes
N uniformly, including all four words R1, R2, L1, and
L2 on ten. With the earlier zero-wake and M exclusions,
both values of `omega_6` in upper form R are closed.
The remaining upper two-`ER` forms in family A are P
and Q, each with `omega_6=0,1`; family B and the other
cap profiles in `(1,-3)` remain open.

Form Q is narrowed in
`odd_skew_upper_a_q_requires_wake_six_2026-09-15.md`.
Its `omega_6=0` band is excluded: the last west
departure on nine would force an additional one. Thus
Q requires `h=1`, or `p=m-1`. Its third north arrival
on seven cannot precede the fourth west departure,
because the resulting eight-step first return skips
two stable visits. Four words on seven remain: either
of two prefixes, with that north arrival between the
last two west departures or after both. The last east
arrival on eight is `EL` in all four. Upper form R
is closed; P with either value of `omega_6`, Q with
`omega_6=1`, family B, and the other cap profiles
remain open.

The full offset-eight words for Q are classified in
`odd_skew_upper_a_q_eighth_word_forms_2026-09-15.md`.
There are four prefixes through the third east arrival:
one with `E2=ER` and three with `E2=EL`. The former
forces `D2=SR` on nine; the latter force `D2=NL` and
`WR` immediately before `E2` on eight. Four suffixes
remain in the middle placement and two in the after
placement, giving sixteen and eight formal words.
Where `E5=ER,E6=EL` are consecutive, the final west
pair on nine is `SR,NL`, and an adjacent `ER,EL`
pair on ten is fixed. This classifies the next row but
does not exclude another complete Q word.

The middle placement with `E5=ER` is excluded in
`odd_skew_upper_a_q_middle_right_exclusion_2026-09-15.md`.
The west departure on eleven feeding the fifth south
departure on eight must be `SR`; its twenty-step first
return forces the next west departure to be `NL`.
For suffix `M_R1` this gives a left/left square. For
`M_R0`, a further skipped-return argument forces an
east pair on twelve whose source time contradicts the
order on eight. This closes both suffixes for all four
prefixes. The middle placement now requires the pair
`E4=ER,E5=EL`. Q has sixteen formal words on eight
remaining: eight middle and eight after words. The
whole Q form and the `(1,-3)` orbit remain open.

Both remaining middle suffixes in Q require `D3=NL`
on nine, by
`odd_skew_upper_a_q_middle_third_west_2026-09-15.md`.
An `SR` there forces `F4=ER,F5=EL,F6=ER` on ten.
In `M_L0` there is no south departure left for `F6`;
in `M_L1` the forced final pair `F6=ER,F7=EL`
contradicts the last west-departure square on eleven.
Thus the `WR` immediately before `E6` on eight
supplies `D3=NL`. The final west departure on nine
is `SR` in `M_L0`; three endings remain in `M_L1`.
The same note also excludes `F5=EL` in `M_L0`:
it would require a north arrival on eleven between
two consecutive north departures on ten. This forces
the ending `WL,F5=ER,F6=EL,WR,F7=EL` on ten.
Neither entire suffix, Q, nor the orbit is excluded
by these further restrictions.

The `M_L0` continuation is reduced to two higher-row
endings in `odd_skew_upper_a_q_ml0_two_tails_2026-09-15.md`.
Its last three west departures on eleven occur after
the north arrival from `F6`, leaving only the north
arrivals from `X,F7` available. If the final west
departure is `NL`, eleven ends `NL,SR,NL` and twelve
ends `ER,EL,WR,EL,WR,EL`. If it is `SR`, eleven
ends `SR,NL,NR,SL,SR,SL`, with the corresponding
ten-event ending on twelve fixed in the note.
The earlier split at `F4` is not yet excluded, and
neither higher-row ending closes `M_L0` or Q.

The entire `M_L0` suffix is now excluded in
`odd_skew_upper_a_q_ml0_exclusion_2026-09-15.md`.
The west departure on eleven feeding `L7=WL` has
no possible turn. An `SR` source forces a square
return from `L7` to the next west arrival `b=WR`
that skips `E4,E5`. An `NL` source instead requires
`WR` immediately before `F6=EL`, where the established
predecessor is `F5=ER`. This closes both higher-row
endings simultaneously, for all four prefixes.
Q now has only `M_L1` in the middle placement and
`A_0,A_1` in the after placement: twelve formal
offset-eight words. Q, P, family B, and the other
cap profiles in `(1,-3)` remain open.

The last west-departure order in `M_L1` is narrowed in
`odd_skew_upper_a_q_ml1_last_west_orders_2026-09-15.md`.
If `D4=SR`, it cannot follow the last north arrival
from `c`: either turn at `F5` would violate one of
the last-square constraints on eleven. It must precede
that north arrival, leaving two six-event endings on
ten. If `D4=NL`, the last four east arrivals on ten
are all `EL`. All remaining alternatives share the
ending `SR,SL,SR,NL,NR,SL` on eleven. This closes
one of the three possible orders on nine, not the
entire `M_L1` suffix or Q.

The remaining `D4=SR` alternatives in `M_L1` are
further constrained in
`odd_skew_upper_a_q_ml1_right_west_return_constraints_2026-09-15.md`.
Three late east arrivals on twelve are forced to be
`EL`, with the arrival feeding the penultimate south
visit on eleven fixed as `ER`. In the `F5=ER` branch,
a return on thirteen forces `F4=ER` and the consecutive
triple `F4=ER,WL,F5=ER` with gaps four and four.
In the `F5=EL` branch, a right turn at the west
departure on thirteen feeding ten's last south departure
would give an eight-step left/left return; it is therefore
`NL`. Both whole branches and the `D4=NL` alternative
remain open.

The primitive-diagonal row has a complete additive condition as well. Normalize
the guard rails to transverse levels `1` and `W+1` and identify each odd class
with its level `t=x+y`. Then

```text
sum_O (-1)^t t = 3  (mod 4).
```

The one-lane parity flow is unique and has `E+L=|O|/2=0 (mod 2)`, exactly the
sign required by P3 at growth eight. The moment removes half of the normalized
placements in every tested width but leaves all three possible horizontal/vertical
wake splits. See `growth8_primitive_diagonal_boundary_2026-08-23.md`.

The coordinate reversal count gives a further condition shared by all ten rows.
For drift `(a,b)`, use coordinate residues modulo a nonzero component and exact
coordinate lines for a zero component. If `nu_F` is the number of period events
in one such fibre and `Omega_F` is the number of odd classes there, then

```text
nu^x_F-Omega^x_F = 2*[a != 0]  (mod 4),
nu^y_F-Omega^y_F = 2*[b != 0]  (mod 4).
```

Thus the `(3,-3)` coordinate visit counts are `2+0+0 mod 4`, with the `2` in
the four-class residue. At `(2,0)`, both `x` residues and all four wake-bearing rows
have visit count two modulo four. At `(4,0)`, every `x` residue has visit count
zero modulo four, while an exact row has the same visit-count residue as its
odd-class count. Every coordinate residue at `(2,4)`, `(2,-4)`, and `(4,-4)`
has visit count zero modulo four. The complete line-congruence system remains
feasible on every bounded `(3,-3)` additive placement tested, so this is another
restriction rather than a second orbit exclusion. See
`growth8_diagonal_coordinate_residues_2026-08-23.md`.

#### The `(2,-2)` row after the rank theorem

In this row the checker parity is fixed by the `2 x 2` residue cell.  Up to
translations of the residue labels, P22 leaves three joint count types:

```text
[2 0]    [2 0]    [3 1]
[0 6],   [4 2],   [1 3].
```

The first is checker-pure.  Its checker-swapped version is the same type after
translation, and the all-period checker-pure theorem excludes it.  The remaining
types have checker splits `4+4` and `6+2`.  The mixed rank theorem requires
odd interlacing in the `4+4` case and even interlacing in the `6+2` case.  The
independent four-corner weight from the mixed-checker note also fixes

```text
sum_Q floor(t/2)-sum_C floor(t/2)-q_1 = 1  (mod 4).
```

After the displayed normalization, the raw `Q-C` moment is `3 mod 4` for the
`4+4` matrix and `0 mod 4` for the `6+2` matrix.  Neither combined condition is
presently contradictory.

#### The two saturated skew rows after the rank theorem

For `(2,4)` and `(2,-4)`, P22 leaves a unique `2 x 4` count type up to
translation: one doubled residue cell lies in one `x mod 2` lane, and the other
three doubled cells lie in the other lane.  In the transverse coordinate
`t=2x-y` or `t=2x+y`, let `T_0,T_1,T_3` be the three endpoint pairs in the
six-class lane, and let `T_A` be the pair in the minority lane.  Writing
`S_A=sum_(t in T_A)t/4` and `S_j=sum_(t in T_j)(t-j)/4`, an additional
four-corner weight gives

```text
S_A-S_0+S_1+S_3 = -s  (mod 4)       for d=(2,4s).
```

The unique parity flow and the one-tour sign also require

```text
sum_{i<j} #{(u,v) in T_i x T_j : u<v} = 1  (mod 2).
```

Placements satisfying both conditions remain, so this removes no residue row.
They are nevertheless all-period restrictions for both chiral orbits.
See `growth8_skew_rank_parity_2026-08-22.md`.

#### The full-rail part of `(4,-4)` is removed

Assume each horizontal guard rail has all four residue lanes visited.
Extremal-line rigidity then supplies four singleton odd classes on each, so the two
rails account for the entire wake.  The induced four-lane parity flow is unique,
its edge/local rank correction is even, and the one-tour sign contradicts P3.
Thus this full-rail subfamily is impossible at every period. A hypothetical
`(4,-4)` highway must leave at least one rail lane unvisited. The whole orbit
is not excluded. See `growth8_extremal_m4_exclusion_2026-08-22.md` and the
scope audit named above.

#### Reproduction and boundary

Run

```text
python code/python/growth8_residue_case_ledger.py \
  --output results/growth8_residue_case_ledger.json
```

The script constructs all 40 drift vectors, verifies that the displayed quarter-
turn orbits are disjoint and exhaustive, and enumerates every distribution of
eight bases among the available coordinate-residue/checker categories.  It then
checks P22 directly and recomputes the possible period residues.  The output has
`all_checks_passed=true`.

```text
growth8_residue_case_ledger.py
cd889d9ec6d2f18fcf18f90e135a0d5b3abb45c81df868472e6b6e397661b600

growth8_residue_case_ledger.json
f7ec95164ce1a08f6378459130424e449c8490164773d3404391b372567db35f
```

This is a complete ledger for the stated arithmetic inputs, not a list of actual
highways. The subsequent rank argument removes the full-rail `(4,-4)` subfamily,
but this enumeration by itself does not impose P3 order. All ten drift orbits
retain unresolved cases.

<a id="source-research-notes-growth8-checker-pure-exclusion-2026-08-20-md"></a>

## growth8_checker_pure_exclusion_2026-08-20

Source: `research-notes/growth8_checker_pure_exclusion_2026-08-20.md`.

### A checker-pure growth-eight exclusion at drift `(2,-2)`

#### Status

This note proves an **analytic all-period conditional exclusion**:

> Let a finite-support periodic highway have growth `g=8` and drift in the
> quarter-turn orbit of `(2,-2)`.  Its eight odd translation classes cannot all
> have the same checkerboard parity.

Equivalently, the checker-pure subfamily of the minimal even-diagonal growth-eight
case is impossible.  This does not exclude mixed-checker wakes, the other
growth-eight drift geometries, or primitive-diagonal growth four.  In particular,
it is not a proof of `g>=12`.

The proof reuses the cardinality-free two-lane rank lemma proved for the
even-diagonal growth-four theorem.  No bounded period, bounded transverse width,
or finite search enters the argument.

#### Two-lane rank lemma

Normalize the drift to `d=(2,-2)`, put

```text
t=x+y,   r=x mod 2,   ell=(x-r)/2,   tau=i-N*ell,
```

and order every translation class `(t,r)` by increasing `tau`.  Let `K` be the
sum modulo two of the zero-based stable ranks of all left turns.  Write `Q` for
the even-`t` vertical-arrival classes and `C` for the odd-`t`
horizontal-arrival classes.

For a class `v`, let `D_v=#R-#L`.  Exact periodic realisability gives
`D_v in {0,1}`; let `O={v:D_v=1}` and let `o_r` count the members of `O` in lane
`r`.  The two-lane edge-block calculation in the paper proves the following
statement whenever all of `O` lies on `Q` or all of `O` lies on `C`:

Since `chi(x,y)=(-1)^(x+y)=(-1)^t`, checker-pure is exactly the hypothesis
`O subset Q` or `O subset C` (for the chosen vertical-arrival phase).

```text
K = 1 + E + L                                  (mod 2),
E + L = sum_r binom(o_r,2)                     (mod 2).       (1)
```

Here `E` is the edge-block permutation sign and `L` is the sum of the local
binary-inversion corrections.  The proof of (1) is independent of `|O|`.  In one
lane the relevant finite binary edge chain splits into `k_r` runs.  Its boundary
contains `o_r=2k_r` odd classes, while its edge/local sign is `k_r`; hence

```text
k_r = binom(2k_r,2) = binom(o_r,2)             (mod 2).
```

Summing the two lanes gives (1).  Pairwise gadget inversions suffice for an
arbitrary finite chain because inversion parity is quadratic in the mod-two edge
indicators; overlapping gadgets combine by symmetric difference.

#### Application at growth eight

Assume for contradiction that all eight odd classes have one checker sign.  The
endpoint decomposition has one canonical strand base for each odd class, and
translation by `(2,-2)` preserves checker parity.  The signed residue theorem,
applied in each `x mod 2` lane, therefore gives

```text
+/- o_r = 2                                    (mod 4).
```

The sign is common to all eight classes, and either choice gives
`o_r=2 (mod 4)`.  Since `o_0+o_1=8`, necessarily

```text
{o_0,o_1}={2,6}.
```

Consequently

```text
E+L = binom(2,2)+binom(6,2) = 1+15 = 0         (mod 2),
```

and the one-cycle sign in (1) gives `K=1`.

On the other hand, exact stable alternation places every left turn at an odd
zero-based rank, so `K=#L (mod 2)`.  Write `N=2M`.  Heading reset makes exactly
`M` moves horizontal, and horizontal displacement two forces `M` to be even.
At growth eight,

```text
#L=(N-8)/2=M-4 = 0                             (mod 2).
```

Thus `K=0`, contradicting `K=1`.  Quarter-turn rotations cover all four sign
choices with `|d_x|=|d_y|=2`.

#### Audit and the remaining case

The existing regression

```text
python code/python/even_diagonal_rank_parity_audit.py
```

checks the local correction truth tables, both parity gadgets, their complete
pairwise interaction table in a representative window, and finite two-lane chains.
The additional arithmetic and cardinality check is

```text
python code/python/growth8_checker_pure_audit.py
```

Both programs are bounded regressions of the displayed algebra, not proof oracles.
The proof is the finite-support run decomposition and parity argument above.

The unresolved `(2,-2), g=8` family is therefore **mixed checker** and remains
open, as do the other growth-eight drift geometries.

<a id="source-research-notes-growth8-diagonal-coordinate-residues-2026-08-23-md"></a>

## growth8_diagonal_coordinate_residues_2026-08-23

Source: `research-notes/growth8_diagonal_coordinate_residues_2026-08-23.md`.

### Coordinate-fibre visit counts

Let a finite-support periodic highway have nonzero drift `d=(a,b)`. An `x`
fibre means a residue class modulo `|a|` when `a` is nonzero, and an exact
column when `a=0`. Define `y` fibres in the same way. For a fibre `F`, write
`nu_F` for the number of period events it contains and `Omega_F` for the number
of odd translation classes there. Then

```text
nu^x_F-Omega^x_F = 2*[a != 0]  (mod 4),
nu^y_F-Omega^y_F = 2*[b != 0]  (mod 4).                (1)
```

Thus the difference is two in every residue fibre associated with a nonzero
drift component and zero on every exact coordinate line associated with a zero
component. This is an all-period consequence of the coordinate reversal count
and the trace criterion.

#### Derivation

Put `ell_i=1` when phase `i` is a left turn and zero otherwise. A vertical step
after phase `i` has equal flanking turns with parity indicator

```text
1+ell_i+ell_(i+1).
```

Fix one `x` fibre. Summing over its vertical steps gives

```text
rho^x_F = V_F+L^x_F  (mod 2),                           (2)
```

because every turn event in the fibre is an endpoint of exactly one vertical
step. The one-dimensional reversal count gives

```text
rho^x_F = H_F+epsilon_a  (mod 2),                       (3)
```

where `epsilon_a=1` if `a` is nonzero and `0` otherwise. For a nonzero
component, the coordinate walk makes one net passage around the residue quotient
modulo two. When `a=0`, the walk has zero net passage across each exact column.
A horizontal landing and the following vertical departure meet at the same
horizontal-arrival event, so `V_F=H_F` exactly. Equations (2)--(3) therefore say

```text
L^x_F = epsilon_a  (mod 2).                             (4)
```

The row argument is identical, with the two axes exchanged.

The finite-support trace criterion supplies the mod-four form. A translation
class of multiplicity `n` has stable word `RLRL...`, and so contributes
`floor(n/2)` left turns. Summing over one fibre gives

```text
L^x_F=(nu^x_F-Omega^x_F)/2,
L^y_F=(nu^y_F-Omega^y_F)/2.
```

Combining these identities with (4) proves (1). The start-with-`R` part of the
trace criterion is essential in this last step.

#### Growth-eight consequences

The law applies to all ten representatives in the growth-eight ledger.

- At `(1,-1)`, the single fibre on either axis has eight odd classes, recovering
  `N=2 (mod 4)`.
- At `(2,0)`, each `x` residue contains four odd classes and therefore has visit
  count two modulo four. Each of the four wake-bearing rows contains two odd classes
  and also has visit count two modulo four.
- At `(2,-2)`, a coordinate residue containing two or six odd classes has visit
  count zero modulo four; one containing four has visit count two. This holds
  independently on both axes.
- At `(1,3)` and `(1,-3)`, the lone `x` fibre has visit count two modulo four.
  The three `y` fibres have visit counts `2+0+0`, with the `2` in the four-class
  fibre.
- At `(3,-3)`, the `4+2+2` margins give visit counts `2+0+0` on both axes.
  Under the additional full-rail hypothesis, the transverse cut residues give
  `N>=4W+12|k|+2`, where `k=(v-h)/3`, and hence `N>=4W+14`.
- At `(4,0)`, every `x` residue has visit count zero modulo four. On each exact
  row the visit count is congruent modulo four to the number of odd classes on
  that row.
- At `(2,4)` and `(2,-4)`, every coordinate residue on both axes has visit count
  zero modulo four.
- At `(4,-4)`, every coordinate residue has visit count zero modulo four. This
  does not strengthen the period congruence to modulo sixteen: summing four
  quantities divisible by four gives only a multiple of four. The
  full-rail subfamily is excluded by the independent rank argument; the
  whole orbit remains open.

These congruences do not close another orbit. After writing each class
multiplicity as its odd-class indicator plus twice a binary variable, the full
transverse, longitudinal, column, and row system remains feasible on all 185
additive `(3,-3)` boundary placements through width thirty. The recorded
width-ten, period-64 `(4,-4)` arithmetic skeleton also remains feasible, with
binary-system nullity 24.

Scope correction, 3 September 2026: the 185 `(3,-3)` placements assume full
rail occupancy. Extremal singleton visits do not prove that hypothesis.
The coordinate-fibre law (1) is unaffected; the conditional period bound is
qualified in `rail_occupancy_scope_audit_2026-09-03.md`.

#### Audit

```text
python code/python/growth8_diagonal_coordinate_residue_audit.py \
  --output results/growth8_diagonal_coordinate_residue_audit.json
```

The kinematic part enumerates all 10,702 heading-resetting turn words of period
at most fourteen having nonzero drift. It checks both reversal identities and
the predicted left-turn parity in every residue fibre or exact coordinate line,
with no failures. This enumeration is a regression for the all-period counting
proof, not its premise.

The direct finite-support control is the standard period-104 highway. Each of
its two `x` residues, and each of its two `y` residues, contains 52 events, six
odd classes, and 23 left turns. The program also checks the period bound on all
185 additive `(3,-3)` placements through width thirty and solves the combined
binary congruence systems described above.

```text
growth8_diagonal_coordinate_residue_audit.py
79b1c6d8df03c193bf5583c3ea41e6a1231fff2efedb9005b5d857ee52970435

test_growth8_diagonal_coordinate_residue_audit.py
e7282d395a00951cc6d6f84d84a5f8fd102fb8d0f979318179cf854ba8ae53e4

growth8_diagonal_coordinate_residue_audit.json
21af23a91f774f2b581b07ec7d4a3f34aef0981605c44554e81ccf0aaaf874a3
```

<a id="source-research-notes-growth8-extremal-m4-exclusion-2026-08-22-md"></a>

## growth8_extremal_m4_exclusion_2026-08-22

Source: `research-notes/growth8_extremal_m4_exclusion_2026-08-22.md`.

### The full-rail growth-eight subfamily at drift `(4,-4)` is impossible

#### Statement

No finite-support periodic highway with growth eight and drift in the quarter-turn
orbit of `(4,-4)` visits all four residue lanes on both extremal lines.

Scope correction, 3 September 2026: full rail occupancy is an additional
hypothesis, not a consequence of extremal singleton visits. The earlier
whole-orbit claim is withdrawn; see `rail_occupancy_scope_audit_2026-09-03.md`.

This is an analytic all-period subfamily exclusion. The bounded audit named at the end
checks the block algebra but is not used as a finite search over periods or widths.

#### The wake is exactly the two guard rails

Normalize the drift to `d=(4,-4)` and put `t=x+y`, `r=x mod 4`.  Let `alpha` and
`beta` count odd translation classes on horizontal- and vertical-arrival levels.
The extremal-line theorem says that both guard rails are horizontal and that each
visited class there is a singleton. Under the full-occupancy hypothesis, each
rail contributes `m=4` odd classes, one in every lane. Since the total
growth is eight,

```text
alpha=8,       beta=0.
```

There are no other odd classes.  If the rail levels are `1` and `W+1`, then `W`
is even and the excess-one boundary is

```text
D[1,r]=D[W+1,r]=1       for r=0,1,2,3,
D[t,r]=0                at every interior vertex.
```

The period congruence also shows that `N=0 (mod 8)`: all eight odd classes have
one checker sign, so the number `A` on the even checker is either zero or eight,
and `N/2+4-4+A=0 (mod 4)`.

#### The parity flow

Reduce every directed edge multiplicity modulo two.  A horizontal-arrival vertex
has vertical outgoing blocks `S,N`; a vertical-arrival vertex has horizontal
blocks `W,E`.  At each vertex, both the incoming and outgoing parity sums equal
`D[t,r]`.  This reduction loses no sign information: block-pair inversions are
products of multiplicities modulo two, and the local formulas use only their
parities and `D`.

At the bottom rail the exterior block is zero, so the inward block is one in all
four lanes.  Incoming parity then makes the corresponding block at level two one.
Because the level-two boundary is zero, its other outgoing block is also one.
Repeating these two steps forces both blocks at every interior vertex and the
single inward block at the top rail.  This is the unique finite parity flow.

The local rank correction vanishes.  At an interior vertex the positive incoming
and outgoing parities are both one, while `D=0`; at a rail vertex they differ and
`D=1`.  Substitution in the two local formulas

```text
vertical-arrival:    p(D+1),
horizontal-arrival:  D(p+1)
```

gives zero in every case.

#### The edge-block sign

Order blocks by `(t,r,port)`, negative port before positive port, at source and
target.  For the full parity flow just described, a direct count of reversed block
pairs for general lane count `m` gives

```text
E_count = m^2 W + m^2(W-1) + (m-1)W.
```

The first term counts adjacent-level reversals.  The second combines the two-level
and same-level mixed-port reversals; the last comes from the two cyclic lane shifts
on each interior vertical-arrival level.  Since `W` is even,

```text
E = E_count = m  (mod 2).
```

Here `m=4`, so `E=0`, and the local term is also zero.  The port-sorting
factorisation of the one-cycle phase successor therefore gives

```text
K = 1+E+L = 1  (mod 2).
```

Exact P3 alternation gives the opposite answer: every left turn has odd stable
rank, and

```text
K = #L = (N-8)/2 = 0  (mod 2)
```

because `N=0 (mod 8)`.  This contradiction proves the statement.

#### Audit

```text
python code/python/growth8_extremal_m4_rank_audit.py \
  --output results/growth8_extremal_m4_rank_audit.json
```

The audit constructs the finite GF(2) flow system for every modulus through eight
and every even width through twenty.  In all 80 systems the solution is unique and
is the full block set.  It then compares the direct inversion count with the closed
formula above and checks every local correction.  These are bounded regressions of
the displayed induction and count, not an exhaustion of possible highways.
The program sets the rail boundary to one in every lane; it does not prove
that a highway must have this boundary.

```text
growth8_extremal_m4_rank_audit.py
e1f2a1e12b4ec36a6380537da1076f868c6d716e5d0cd41d042b77e6f5761fc9

growth8_extremal_m4_rank_audit.json
ad33827ca50272365198b7a93f3ad120d0e5b98f00c7f9d50352352b328fdcf9
```

<a id="source-research-notes-growth8-m3-additive-boundary-2026-08-23-md"></a>

## growth8_m3_additive_boundary_2026-08-23

Source: `research-notes/growth8_m3_additive_boundary_2026-08-23.md`.

### The additive condition for full rails at drift `(3,-3)`

#### Result

Suppose a finite-support periodic highway has growth eight and drift in the
quarter-turn orbit of `(3,-3)`, and assume all three residue lanes are visited
on each extremal line. Normalize the transverse coordinate to
`t=x+y`, and put the lower and upper guard rails at levels `b` and `b+W`.
Extremal rigidity makes `W` even.  If the period-start ant is on level `p`, then
`b-p` is odd: the start heading is vertical, while the rail arrivals are
horizontal.

The two rails contain six of the eight odd translation classes.  The residue
theorem puts the remaining horizontal class and the remaining vertical class in
the same `x mod 3` lane and the same `y mod 3` residue.  After translating the
lane labels, write them as `(0,h)` and `(0,v)`.  Here `h` is odd, `v` is even,
and

```text
k=(v-h)/3
```

is an odd integer.  Every such highway must satisfy

```text
k = W+1  (mod 4).                                      (1)
N = 6    (mod 8).
N >= 4W+12|k|+2.                                       (6)
```

Scope correction, 3 September 2026: extremal rigidity proves singleton
visits, not full rail occupancy. Everything below that uses the six rail
classes has the additional full-occupancy hypothesis. See
`rail_occupancy_scope_audit_2026-09-03.md`.

In this subfamily, `W=4` is impossible, while `W=6` remains arithmetically
possible. Since `k` is odd, the second inequality gives `N>=4W+14`. These are
all-period restrictions on the full-rail subfamily, not on the whole orbit.

#### The complete additive family on the forced boundary

Write a drift-periodic mod-four weight as `w[r,t]`, where `r=x mod 3` and the lane
index is read modulo three.  The zero four-corner condition is

```text
w[r,t]+w[r+1,t+1]+w[r,t+1]+w[r+1,t+2]=0  (mod 4).       (2)
```

Thus two consecutive transverse rows determine the whole weight.  Let

```text
A_t=sum_(r=0)^2 w[r,t],       S=A_0+A_1.
```

Summing (2) over the lanes shows that `(-1)^t A_t` is an arithmetic progression.
After translating the transverse origin so that `p` is even and `b` is odd,

```text
A_b+A_(b+W)+A_p-A_(p+1)
    =[2(b-p)+W-1]S.                                     (3)
```

The same recurrence, now followed in lane zero for three transverse steps, gives

```text
w[0,h]+w[0,h+3k]=-kS                                   (4)
```

whenever `h` and `k` are odd.  The endpoint charge consists of the two rail sums,
the two extra classes, and the north-heading monodromy `A_p-A_(p+1)`.  Equations
(3)--(4) reduce it to

```text
[2(b-p)+W-1-k]S.                                        (5)
```

The two initial rows in (2) are arbitrary, so `S` can be any residue modulo four.
Since `b-p` is odd, the coefficient in (5) is `W+1-k` modulo four.  Consequently
every drift-periodic zero-four-corner weight obeys its endpoint equation if and
only if (1) holds.  On this forced boundary, there is no second condition hidden
elsewhere in the additive mod-four family.

One convenient generator makes (1) visible without the recurrence calculation:

```text
w(x,y)=(-1)^(x+y)(floor(x/3)+floor(y/3))  (mod 4).
```

It is periodic under `(x,y)->(x+3,y-3)`, has zero four-corner sum, and its
north-heading potential has monodromy one.  Its value on the eight odd classes is

```text
sum_O w = 2-W+k  (mod 4).
```

Here the last display uses the harmless rail normalization `b=1`.  Charge
conservation, `sum_O w+1=0`, is exactly (1), independently of the start level.

#### The period class

Choose phase zero to be a vertical arrival and translate its cell to the origin.
The origin is then even in the checkerboard colouring, and a class is even-checker
exactly when its arrival axis is vertical. The two rails supply six horizontal
classes, and the extra class at level `h` is horizontal as well. The class at
level `v` is the only vertical one. Thus the number `A` of even-checker odd
classes is one. The kinematic congruence

```text
N/2+3-3+A = 0  (mod 4)
```

therefore gives `N=6 (mod 8)`. In particular, this orbit cannot occur at period
58 in the full-rail subfamily. This does not remove that period class from
the whole drift orbit by a hand argument.

#### Period cost of separating the two extra classes

The transverse line law turns the separation `|v-h|=3|k|` into a period lower
bound. Normalize the rails to levels `1` and `W+1`, and let `f_t` be the number
of upward crossings of the cut between levels `t` and `t+1`. If `G_t` is the
number of odd classes at levels at most `t`, then

```text
f_t = (-1)^(t+1) G_t  (mod 4).                          (7)
```

There are three rail classes below both extra levels, four between them, and five
above them. Hence the `3|k|` cuts between `h` and `v` have `f_t=0 mod 4` and so
`f_t>=4`. On the other `W-3|k|` cuts, the least positive representatives
alternate between one and three. Their combined count is odd, begins and ends
with three, and has sum `2(W-3|k|)+1`. Therefore

```text
sum_(t=1)^W f_t >= 2W+6|k|+1.
```

The transverse walk crosses every cut equally often in both directions, so
`N=2 sum_t f_t`. This proves (6). Equality in this counting bound takes every
cut at its least positive representative; it does not assert that those counts
form a single ant tour.

#### Why this does not close the orbit

There are normalized placements satisfying (1) at every even width from six
onward.  When `W=2 mod 4`, take `(h,v)=(5,2)`, so `k=-1`; when `W=0 mod 4`, take
`(h,v)=(3,6)`, so `k=1`.  The first choices occur at widths six and eight.

Since `N=6 (mod 8)`, the number of left turns `(N-8)/2` is odd. The lifted-rank
factorization therefore asks for parity-flow sign zero. The direct audit finds
sign zero on all 185 additive survivors through
width thirty.  That computation is a regression for compatibility, not an
all-width proof.  It shows why the new congruence cannot be presented as a rank
contradiction. The coordinate-residue audit also checks (6) on the same 185
placements. At widths `6,8,10` the least possible periods are respectively
`38,46,54`; at width twelve the least is `62`.

#### Audit

```text
python code/python/growth8_m3_boundary_audit.py \
  --output results/growth8_m3_boundary_audit.json
```

The default run tests 370 normalized boundary placements.  It evaluates the six
coordinate generators of the full `4^6` additive family, checks their equivalence
to (1), verifies the explicit weight and its monodromy, and solves the finite
three-lane parity flow for every additive survivor. It also checks that every
normalized boundary has one even-checker odd class and period residue six. Its result is
`all_checks_passed=true`.

All these placements already include all three lanes on both rails. The
audit does not test partial-rail boundaries or establish their impossibility.

```text
growth8_m3_boundary_audit.py
78c8db53226a7c62ae22ea984bcc98c8b034e148e41b9f0e931addd9cccca1ce

test_growth8_m3_boundary_audit.py
414e290d60dd1c31d506fd5e51d0da2f29a5c88ede6e7691644462c293f803a4

growth8_m3_boundary_audit.json
6f0b1bf3767f568e407f59dde64706fc1a7ccdfca0b886b6921e3ca2e95d80f9
```

<a id="source-research-notes-growth8-m4-mixed-rank-exclusion-2026-09-04-md"></a>

## growth8_m4_mixed_rank_exclusion_2026-09-04

Source: `research-notes/growth8_m4_mixed_rank_exclusion_2026-09-04.md`.

### The mixed wake at drift `(4,-4)` is impossible

Date: 2026-09-04.

#### Statement

No finite-support periodic highway of growth eight and drift `(4,-4)` has
four horizontal-arrival and four vertical-arrival odd translation classes.

The proof is an all-period rank calculation.  The finite checks used while
auditing the block signs are not part of the proof.

#### Residue shape of a mixed wake

Put \(t=x+y\) and \(r=x\pmod4\), with vertical-arrival classes `Q` on even
levels and horizontal-arrival classes `C` on odd levels.  The signed
coordinate-residue law is \(2\pmod4\) in every `x mod 4` and `y mod 4`
fibre.  Since there are eight wake classes, every one of the four fibres in
either coordinate contains exactly two wakes, and those two wakes have the
same checker sign.

In a `4+4` split, every coordinate residue is consequently incident either
to two `Q` wakes or to two `C` wakes.  Exactly two `x` residues and two `y`
residues are of type `Q`.

Let \(a\) and \(b\) count the even `x` and even `y` residues of type `Q`.
A `Q` wake has coordinate residues of the same parity, so degree balance
gives \(a=b\).  A `C` wake has residues of opposite parity; balancing its
even-`x` and odd-`y` ends gives \(2-a=b\).  Thus

\[
 a=b=1.
\]

The `Q` wake is therefore two doubled residue edges, one even-even and one
odd-odd.  The `C` wake is two more doubled edges, one even-odd and one
odd-even.  The two classes on any doubled edge have transverse levels
differing by a nonzero multiple of four.

#### Binary block equations

Reduce every directed edge-block multiplicity modulo two.  At a `C` class
write \(s_{j,r},n_{j,r}\) for its south and north blocks; at a `Q` class
write \(w_{t,r},e_{t,r}\) for its west and east blocks.  If
\(D^C,D^Q\) are the two wake indicators, flow conservation is equivalent to

\[
\begin{aligned}
 s_{j,r}&=n_{j,r}+D^C_{j,r},\\
 w_{t,r}&=e_{t,r}+D^Q_{t,r},\\
 n_{j,r}&=n_{j-2,r}+D^C_{j,r}+D^Q_{j-1,r},\\
 e_{t,r}&=e_{t-2,r-2}+D^Q_{t,r}+D^C_{t-1,r-1}.
\end{aligned}
\tag{1}
\]

The second coordinate is modulo four.  Zero boundary values below the wake
determine the finite solution uniquely.  For one doubled wake edge, (1)
gives one finite `x` interval and one finite `y` interval; call their union
a doubled-edge gadget.

Let

\[
 F(D)=E(D)+L(D)\pmod2,
\]

where \(E\) is the edge-block inversion parity and

\[
 L=\sum_Q p_v(D_v+1)+\sum_C D_v(p_v+1)
\tag{2}
\]

is the local rank correction.  Here \(p_v\) is the parity of the positive
incoming and outgoing blocks.  Since the solution of (1) is linear in
\(D\), \(F\) is a quadratic function of the wake indicator.

#### The four-gadget sign

The needed quadratic calculation is independent of the lengths and relative
heights of the four doubled-edge gadgets:

\[
 \boxed{F(D)=0.}
\tag{3}
\]

Here are the details that remove any bounded-placement assumption.  Translate
the even `x` and even `y` residues of type `Q` to zero.  If
\(\epsilon_x,\epsilon_y\in\{1,-1\}\) locate the odd `Q` residues, the four
doubled edges are

\[
\begin{array}{c|c}
Q&(0,0),\ (\epsilon_x,\epsilon_y)\\
C&(2,\epsilon_y+2),\ (\epsilon_x+2,2),
\end{array}
\tag{4}
\]

with residues read modulo four.  Substitute one pair of endpoints for each
row of (4) into (1).  Moving any one endpoint by four levels inserts one
four-level piece into each of its two coordinate intervals.  In the
source/target order `(level,lane,port)`, the new edge inversions against the
other three gadgets occur in equal pairs.  The remaining two inversions are
exactly the two changes in (2).  Hence \(F\) is unchanged.  Repeating this
move reduces arbitrary distinct endpoints to adjacent representatives.

For those representatives the source/target port table is

\[
\begin{array}{c|c|c|c}
(\epsilon_x,\epsilon_y)&F(Q_{00})+F(Q_{\epsilon_x\epsilon_y})
&F(C_{2,\epsilon_y+2})+F(C_{\epsilon_x+2,2})
&\text{six cross terms}\\ \hline
(1,1)&0&0&0\\
(1,-1)&0&0&0\\
(-1,1)&0&0&0\\
(-1,-1)&0&0&0
\end{array}
\tag{5}
\]

Each individual doubled-edge gadget has \(F=1\); this accounts for the
zeros in the middle columns, since each column contains two gadgets.  The
last column is obtained by pairing the possible reversed block pairs in
(1); equal-target-port pairs are included, as required by the negative-
before-positive convention.  Equations (4)--(5), together with the
four-level invariance, prove (3) for arbitrary endpoint heights.

#### Rank contradiction

The port-sorting factorisation gives

\[
 K\equiv1+E+L=1+F(D)\equiv1\pmod2.
\tag{6}
\]

On the other hand, the period congruence at drift `(4,-4)` is
\(N\equiv0\pmod8\).  Exact stable alternation puts every left turn at odd
stable rank, so

\[
 K\equiv\#L=\frac{N-8}{2}\equiv0\pmod2.
\tag{7}
\]

Equations (6)--(7) contradict one another.  Therefore the mixed `4+4`
arrival-axis split is impossible.

The remaining `(4,-4)` problem is the pure-horizontal `8+0` split.  Its
wake graph is still 2-regular, but its sign depends on the transverse labels,
not only on the number of graph components; no component-count shortcut is
being asserted here.

<a id="source-research-notes-growth8-m4-partial-rail-obstruction-2026-09-04-md"></a>

## growth8_m4_partial_rail_obstruction_2026-09-04

Source: `research-notes/growth8_m4_partial_rail_obstruction_2026-09-04.md`.

### Partial rails at drift (4,-4): a relaxed family

Date: 2026-09-04.

Subsequent status: [the alternating-half-rail argument](04_Growth_eight.md#source-research-notes-m4-alternating-half-rail-exclusion-2026-09-06-md)
excludes the explicit family below using additional visit-order information. Its
compatibility with the stated rank, residue, and additive tests remains valid.
The final discussion records the gap before that later argument.

#### Scope

This note gives an infinite family of **relaxed boundary and parity data, not P3 traces**. The family satisfies the coordinate-fibre wake congruences, the rank-sign obstruction, and every drift-periodic additive mod-four endpoint charge. The upper rail is only partially occupied. Consequently, the full-rail rank exclusion cannot be extended to the whole drift orbit using those conditions alone.

No legal chronological ordering, nonnegative integer edge flow, or actual period is constructed here. In particular, this does not establish existence of a growth-eight highway or close any remaining orbit. The distinction matters because extremal rigidity makes each *visited* rail class a singleton; it does not require every rail lane to be visited.

The rank formulas used below are those of the rank factorization in `paper/comprehensive_main.tex` and the conditional full-rail calculation in `growth8_extremal_m4_exclusion_2026-08-22.md`. The complete additive-weight equation is recorded in `growth12_research_2026-08-17.md`; the visit-residue law is in `growth8_diagonal_coordinate_residues_2026-08-23.md`. The calculations here are symbolic.

#### The boundary

Put

\[
d=(4,-4),\qquad t=x+y,\qquad r=x\pmod4.
\]

Use the phase convention that even levels contain vertical-arrival classes, denoted \(Q\), and odd levels contain horizontal-arrival classes, denoted \(C\). Let \(D_{t,r}\in\{0,1\}\) be the wake indicator. First take \(W=4L\), with \(L\ge1\), and set

\[
\begin{aligned}
D_{1,r}&=1 &&(r=0,1,2,3),\\
D_{3,r}&=1 &&(r=0,2),\\
D_{W+1,r}&=1 &&(r=1,3),
\end{aligned}
\]

with all other entries zero. The final family will have \(L=2j+1\), \(j\ge1\), so that \(W=8j+4\).

There are eight horizontal wake classes and no vertical wake classes. The lower rail has four occupied lanes and the upper rail has two. Each residue of \(x\) occurs twice. For \(y=t-r\pmod4\), the lower rail contributes all four residues once, the two level-three classes contribute residues \(3,1\), and the upper rail contributes residues \(0,2\). Thus each residue of \(y\) also occurs twice. All these wakes have the horizontal checker sign, so every coordinate fibre has signed wake sum \(-2\equiv2\pmod4\), as required by the coordinate-fibre wake congruence.

#### The finite edge-parity solution

All variables in this section lie in \(\mathbb F_2\). At an odd-level class \((j,r)\), write \(s_{j,r}\) and \(n_{j,r}\) for its south and north outgoing edge parities. At an even-level class \((t,r)\), write \(w_{t,r}\) and \(e_{t,r}\) for its west and east outgoing edge parities. Their targets are

\[
\begin{array}{c|c}
\text{edge}&\text{target}\\ \hline
S&(j-1,r)\\
N&(j+1,r)\\
W&(t-1,r-1)\\
E&(t+1,r+1).
\end{array}
\]

The zero vertical boundary gives

\[
w_{t,r}=e_{t,r}=a_{t,r},\qquad
n_{j,r}=b_{j,r},\qquad s_{j,r}=b_{j-2,r}.
\]

The two remaining boundary equations are

\[
b_{j,r}+b_{j-2,r}=D_{j,r},\qquad
a_{j-1,r-1}+a_{j+1,r+1}=D_{j,r}.
\tag{1}
\]

Vanishing below the strip determines the solution successively; vanishing above it can then be checked directly. Write

\[
\mathbf f=(1,1,1,1),\quad
\mathbf v=(1,0,1,0),\quad
\mathbf o=(0,1,0,1),\quad
n_* = W/2-1=2L-1.
\]

The solution is

\[
\begin{array}{c|c}
\text{levels}&\text{parity vector}\\ \hline
b_1&\mathbf f\\
b_3,b_5,\ldots,b_{W-1}&\mathbf o\\
a_2&\mathbf f\\
a_4,a_6,\ldots,a_W&\mathbf v.
\end{array}
\tag{2}
\]

All unlisted vectors vanish. There are \(n_*\) occurrences of each of the two repeated masks. Substitution into (1) verifies the lower boundary, level three, and the upper boundary separately. This is a finite parity flow; it is not an integer-flow or itinerary construction.

#### The local rank correction

Let \(p_v\) be the sum, modulo two, of the positive incoming and positive outgoing edge parities at a class. Here positive means north on vertical edges and east on horizontal edges. In the present coordinates,

\[
p_{Q(t,r)}=b_{t-1,r}+a_{t,r},\qquad
p_{C(j,r)}=a_{j-1,r-1}+b_{j,r}.
\]

The local rank correction is

\[
\Lambda=\sum_Q p_v(D_v+1)+\sum_C D_v(p_v+1)\pmod2.
\tag{3}
\]

At level two, every \(Q\)-value of \(p\) is zero. At each even level from four through \(W\), every \(Q\)-value is one, contributing four to (3). At every occupied horizontal boundary class, \(p=1\); the other horizontal classes have \(D=0\). Therefore

\[
\Lambda=0.
\tag{4}
\]

The individual interior vertical corrections need not vanish; their sum does.

#### The global edge inversions

Order source edge blocks lexicographically by level, then lane \(0,1,2,3\), then negative before positive. Use the corresponding order at targets, including the incoming port. Let \(E\) be the parity of the resulting edge-block permutation, weighted by the edge parities. An inversion can only involve equal source levels or source levels differing by one or two.

The adjacent-level contributions cancel in pairs. For each odd \(j\), the positive edges from \(C_j\) crossing the negative edges from \(Q_{j+1}\) contribute \(|b_j||a_{j+1}|\). The positive edges from \(Q_{j+1}\) crossing the negative edges from \(C_{j+2}\) contribute the same quantity. Here \(|\cdot|\) denotes the number of ones in a mask.

For the remaining horizontal-source terms,

\[
E_C=\sum_{j\text{ odd}}\left[
\binom{|b_j|}{2}+|b_j|
+\sum_{r<s}b_{j,r}b_{j-2,s}
\right]\pmod2.
\tag{5}
\]

The last sum is the same-level positive/negative crossing count. The first two terms count north edges from level \(j\) against south edges from level \(j+2\): their common target level has the reversed port order when the target lanes agree, so an inversion occurs for \(r\ge s\).

For vertical sources, put

\[
\rho_+(r)=r+1\pmod4,\qquad \rho_-(r)=r-1\pmod4,
\]

with values taken in \(\{0,1,2,3\}\). Then

\[
\begin{aligned}
E_Q=\sum_{t\text{ even}}\bigg[&
\binom{|a_t|}{2}
+a_{t,0}(|a_t|-a_{t,0})
+a_{t,3}(|a_t|-a_{t,3})\\
&+\sum_{r,s}a_{t,r}a_{t+2,s}
\mathbf1_{\rho_+(r)\ge\rho_-(s)}\bigg]\pmod2.
\end{aligned}
\tag{6}
\]

The binomial term is the same-level mixed-port count. The next two terms are the cyclic lane-order inversions: west edges wrap lane zero to lane three, and east edges wrap lane three to lane zero. The last term compares east edges from level \(t\) with west edges from level \(t+2\); equal target lanes again invert the two ports.

Equations (5) and (6) can be evaluated without a case search. In (5), the self-term for \(\mathbf f\) is \(6+4=10\), and the self-term for \(\mathbf o\) is \(1+2=3\). The \(\mathbf o,\mathbf f\) cross-term has two pairs, while each \(\mathbf o,\mathbf o\) cross-term has one. Thus

\[
E_C=n_*+(n_*-1)=1\pmod2.
\]

In (6), the self-term for \(\mathbf f\) is \(6+3+3=12\). The self-term for \(\mathbf v\) is \(1+1=2\). The separated-level \(\mathbf f\)-to-\(\mathbf v\) term has four pairs: one against target lane three and three against target lane one. A \(\mathbf v\)-to-\(\mathbf v\) term has three pairs. Consequently

\[
E_Q=n_*-1=0\pmod2,
\qquad E=E_C+E_Q=1.
\tag{7}
\]

For a pure-horizontal growth-eight trace the period congruence is \(N\equiv0\pmod8\), so the number of left turns would satisfy \(K=(N-8)/2\equiv0\pmod2\). The rank-sign condition is \(K\equiv1+E+\Lambda\). Equations (4) and (7) give precisely zero on its right-hand side. The rank condition therefore does not exclude this boundary family.

#### Every additive mod-four charge

Let \(w_{r,t}\in\mathbb Z/4\mathbb Z\) be any drift-periodic zero-four-corner weight. In these coordinates its defining equation is

\[
w_{r,t}+w_{r+1,t+1}+w_{r,t+1}+w_{r+1,t+2}=0.
\tag{8}
\]

Write \(w_t=(w_{r,t})_r\), and let \((Pz)_r=z_{r+1}\). Equation (8) is

\[
w_t+(I+P)w_{t+1}+Pw_{t+2}=0.
\tag{9}
\]

The two initial vectors \(w_0,w_1\) are arbitrary, and (9) determines the weight in both directions because \(P\) is invertible. Thus the following calculation treats the whole additive family, not a selected list of test weights.

Put \(A_t=\sum_r w_{r,t}\) and \(S=A_0+A_1\). If \(z_t=(-1)^t w_t\), then

\[
z_{t+1}-z_t=P^{-t}(-w_1-w_0).
\]

Summing four consecutive differences gives \(z_{t+4}=z_t-S\mathbf f\). In particular, at odd levels,

\[
w_{t+4}=w_t+S\mathbf f.
\tag{10}
\]

Define the even- and odd-lane sums

\[
V_t=w_{0,t}+w_{2,t},\qquad O_t=w_{1,t}+w_{3,t}.
\]

Equation (10) yields \(O_{W+1}=O_1+2LS\). Directly from (9),

\[
w_3=(P^{-1}+P^{-2})w_0+(I+P^{-1}+P^{-2})w_1,
\]

so that

\[
V_3=A_0+2V_1+O_1.
\tag{11}
\]

For completeness, the north-heading potential monodromy along \(d\) is

\[
M_N=A_0-A_1.
\tag{12}
\]

One way to obtain (12) is to join \((r,-r)\) to \((r+1,-r-1)\) by an east step and a south step. The two right-turn cocycle equations, together with \(F_S=F_N-2w\) at the endpoint, give

\[
F_N(r+1,-r-1)-F_N(r,-r)
=-w(r,-r)-w(r+1,-r)+2w(r+1,-r-1).
\]

Summing over four successive lanes gives (12). This is a potential calculation along a lattice path, not a proposed ant itinerary.

The use of levels zero and one does not require the trace to visit level zero. Summing (9) over lanes shows that \(A_p-A_{p+1}=A_0-A_1\) at every even level \(p\). Thus (12) is also the north-heading monodromy at an actual even-level starting class.

The total wake weight is \(A_1+V_3+O_{W+1}\). Its additive endpoint defect is therefore

\[
\begin{aligned}
\sum_{D=1}w+M_N
&=A_0+V_3+O_1+2LS\\
&=2(A_0+V_1+O_1)+2LS\\
&=2(L+1)S\pmod4.
\end{aligned}
\tag{13}
\]

Since \(S\) is arbitrary, every additive charge vanishes exactly when \(L\) is odd. Taking \(L=2j+1\), \(j\ge1\), gives the asserted widths

\[
W=8j+4\in\{12,20,28,\ldots\}.
\]

#### Coordinate-fibre visit residues

The local port congruences prescribe a class multiplicity \(m_v\), modulo four, by

\[
m_v\equiv D_v+2p_v\quad(Q),\qquad
m_v\equiv2p_v-D_v\quad(C).
\]

For this family, every horizontal wake has multiplicity residue one and every other horizontal class has residue zero. The vertical level-two classes have residue zero; every lane at each vertical level from four through \(W\) has residue two.

Each \(x\)-residue fibre, and likewise each \(y\)-residue fibre, consequently has total visit residue

\[
\nu_F\equiv2+2n_*=4L\equiv0\pmod4.
\]

Its unsigned wake count is \(\Omega_F=2\), so \(\nu_F-\Omega_F\equiv2\pmod4\), the required coordinate-fibre value for either nonzero drift component. Again, these are compatible multiplicity residues, not a realization by integer port counts.

#### What remains

The family passes the rank-sign test, the complete additive mod-four endpoint test, and the stated coordinate-fibre tests. Any exclusion of these placements must use an additional condition, such as integer-flow realizability, stable port order, or physical chronology. The full-rail argument does not supply that condition for a partially occupied upper rail.

<a id="source-research-notes-growth8-m4-pure-additive-normal-form-2026-09-04-md"></a>

## growth8_m4_pure_additive_normal_form_2026-09-04

Source: `research-notes/growth8_m4_pure_additive_normal_form_2026-09-04.md`.

### Additive normal form for the pure `(4,-4)` wake

Date: 2026-09-04.

#### Scope

Assume a growth-eight `(4,-4)` candidate has eight horizontal-arrival wake
classes and no vertical-arrival wake class.  This note reduces the complete
family of drift-periodic additive mod-four endpoint charges to one congruence
on the transverse wake heights.  It is a hand calculation and is not an
exclusion.

#### Residue parameters

Use \(t=x+y\), \(r=x\pmod4\), with the wake on odd levels.  Every `x` and
`y` residue contains exactly two wakes.  Let \(a\) be the number of wakes on
levels \(t\equiv1\pmod4\) in each even `x` residue, and let \(b\) be the
same number in each odd `x` residue.  The `y`-degree equations force the two
even residues to have the same count and likewise for the two odd residues,
so

\[
 a,b\in\{0,1,2\}.
\]

For a wake at level \(t\), put

\[
 h(t)=
 \begin{cases}
 (t-1)/4,&t\equiv1\pmod4,\\
 (t-3)/4,&t\equiv3\pmod4,
 \end{cases}
 \qquad Z=\sum_{D_{t,r}=1}h(t).
\tag{1}
\]

#### Complete additive condition

Every drift-periodic zero-four-corner endpoint charge vanishes if and only if

\[
 \boxed{Z\equiv a+b-1\pmod4.}
\tag{2}
\]

To prove this, let \(w_t=(w_{r,t})_r\) be an arbitrary quotient weight,
put \(A_t=\sum_rw_{r,t}\), and set \(S=A_0+A_1\).  The four-corner
recurrence gives

\[
 w_{t+4}=w_t+S\mathbf1
\tag{3}
\]

on odd levels.  Write \(U_e,U_o\) for the even- and odd-lane sums of
\(w_1\), and \(V_e,V_o\) for those of \(w_3\).  The first three recurrence
steps give

\[
 V_e=A_0+A_1+U_e,qquad V_o=A_0-2A_1-U_e.
\tag{4}
\]

The base-level part of the wake sum is therefore

\[
 aU_e+(2-a)V_e+bU_o+(2-b)V_o
 =-(a+b)A_0+(2-a+3b)A_1.
\tag{5}
\]

The height shifts in (3) add \(ZS\), and the north-heading monodromy is
\(A_0-A_1\).  The complete endpoint defect is consequently

\[
 (Z+1-a-b)A_0+(Z+1-a+3b)A_1.
\tag{6}
\]

The coefficients differ by \(4b\), while \(A_0,A_1\) are arbitrary.  This
proves (2), without selecting a finite basis of test weights.

The 2-regular wake graph splits into two checker blocks.  In either block,
the residue graph is a four-cycle when its parameter is one and is two
doubled edges when its parameter is zero or two.  Thus a `CP` graph has one
of \(a,b\) equal to one and the other equal to zero or two; (2) then makes
\(Z\) even.  The explicit partial-rail family has
\((a,b)=(1,2)\), \(Z=2L\), so (2) recovers \(L\) odd and
\(W=8j+4\).

The congruence leaves infinitely many labelled pure wake graphs.  Chronology,
not another additive weight of this family, is needed to finish the orbit.

<a id="source-research-notes-growth8-mixed-checker-rank-2026-08-22-md"></a>

## growth8_mixed_checker_rank_2026-08-22

Source: `research-notes/growth8_mixed_checker_rank_2026-08-22.md`.

### Mixed-checker rank parity at drift `(2,-2)`

#### Result and scope

Let a finite-support periodic trace have drift `(2,-2)`.  Write `t=x+y` and
`r=x mod 2`, and split the excess-one translation classes into

```text
Q = {t even},                 C = {t odd}.
```

Put

```text
q_r = |O intersect Q intersect {r}|,
c_r = |O intersect C intersect {r}|.
```

When the four counts have a common parity, denote it by `p`.  Define

```text
I = #{(c,q) in (O intersect C) x (O intersect Q): t(c)<t(q)}  (mod 2).
```

The two-lane rank factorisation has the following boundary form:

```text
E+L = sum_r [binom(q_r,2)+binom(c_r,2)] + I + p  (mod 2).       (1)
```

Here `E` is the directed-edge block sign and `L` is the sum of the local port
corrections.  Formula (1) holds for every finite parity flow, without a period or
width bound.

For growth eight, P22 gives

```text
q_r-c_r       = 2  (mod 4),
q_r-c_(1-r)   = 2  (mod 4).
```

Thus `q_0=q_1 (mod 4)` and `c_0=c_1 (mod 4)`.  The four binomial terms in (1)
cancel in pairs, and the one-tour sign reduces to

```text
I+p=1.                                                        (2)
```

This is an all-period necessary condition.  It recovers the checker-pure
exclusion and narrows the two mixed families as follows:

```text
checker split 2:6 or 6:2:    p=1 and I=0,
checker split 4:4:           p=0 and I=1.
```

#### A second additive charge

The same quotient has a useful mod-four charge which is independent of the
coordinate indicators used in P22.  Put

```text
w(x,y) = (-1)^(x+y) (floor(x/2)+floor(y/2))  (mod 4).
```

Its four-corner sum is zero, it is periodic under `(x,y) -> (x+2,y-2)`, and
the north-heading potential changes by `3` around the translation cycle.  The
usual charge-conservation argument therefore gives

```text
sum_(q in Q) floor(t(q)/2)
  - sum_(c in C) floor(t(c)/2) - q_1 = 1  (mod 4),             (3)
```

where `q_1` is the number of even-`t` classes in lane `r=1`.  In the normalized
`4:4` residue matrix this says that the raw `Q-C` moment is `3 mod 4`; in the
normalized `6:2` matrix it is `0 mod 4`.

Equations (2) and (3) are genuinely separate restrictions, but they do not yet
give an exclusion.  There are finite boundary placements satisfying both.  A
further argument must use more of the visit order than its sign and this one
additive moment.

#### Audit

`code/python/mixed_checker_rank_parity_audit.py` checks the local gadget table,
reconstructs every finite parity flow in a strip of width six, and verifies the
weight and monodromy identities above.  Its current run reports

```text
finite flows:            32768
mixed table checks:         53
additive-weight checks:    773
failures:                    0
```

The finite enumeration is a regression check.  The all-period statements are
the finite-support factorisation and the additive-charge calculation above.

Both alternatives survive the present residue, additive-weight, and aggregate
level filters.  Consequently (2) is not a complete exclusion of mixed-checker
wakes.

#### Proof of the boundary formula

First suppose all four lane counts are even.  Pair the `C` boundary in each lane
by a finite binary chain `alpha[j,r]`, and pair the `Q` boundary by a chain
`beta[j,r]`.  The centres `j` are odd.  The parity flow is the symmetric
difference of the two four-edge gadgets

```text
G_C(j,r)={N[j,r],S[j+2,r],W[j+1,1-r],E[j+1,1-r]},
G_Q(j,r)={S[j,r],N[j,r],E[j-1,r],W[j+1,r]}.
```

This decomposition is unique.  A finite zero-boundary flow has `w=e` on `Q` and
`s=n` on `C`; conservation then makes the remaining binary edge sequences
constant in the transverse direction.  Finite support forces those constants to
vanish.

The sign `E+L` is a quadratic function of the directed-edge parity bits.  Each
gadget has value one.  Two gadgets of the same type have cross value one exactly
when their centres are adjacent in the same lane.  The usual finite-run count
therefore gives

```text
sum_r binom(q_r,2)+sum_r binom(c_r,2).
```

For a mixed pair `G_C(j,r),G_Q(k,s)`, the cross value is independent of the lane
choices and is one exactly when `k-j` is `0` or `2`.  Hence the mixed contribution
is

```text
sum_(j,r,s) alpha[j,r](beta[j,s]+beta[j+2,s]).
```

The second factor is the `Q` boundary at level `j+1`; the sum over `r` in the
first factor is the parity of the number of `C` boundary points below that level.
The displayed sum is precisely `I`.  This proves (1) in the even sector.

If all four counts are odd, choose an even level `k` below the support and add

```text
H(k)={E[k,0],E[k,1],S[k+1,0],S[k+1,1]}.
```

Its boundary has one point of each type in each lane, and its value is one.  Being
below the original support, it has zero cross term with the original flow.  The
four binomial changes sum to zero, while `I` is unchanged.  Applying the even
formula after this toggle supplies the final `+p` in (1).

#### Growth-eight consequence

Port sorting factors the one-cycle phase successor as

```text
K=1+E+L  (mod 2),
```

where `K` is the sum of the stable ranks of all left turns.  Exact alternation
puts every left turn at odd zero-based rank, so `K=#L (mod 2)`.  Write the period
as `N=2M`.  There are `M` horizontal moves, and horizontal displacement two makes
`M` even.  At growth eight,

```text
#L=(N-8)/2=M-4=0  (mod 2).
```

Therefore `K=0`, whereas the factorisation gives `K=1+I+p`.  This proves (2).

The bounded regression is

```text
python code/python/mixed_checker_rank_parity_audit.py
```

It checks the complete mixed gadget table and every reconstructed finite parity
flow in a configurable strip.  The proof is the finite-support decomposition
above, not the bounded strip enumeration.

<a id="source-research-notes-growth8-odd-skew-additive-2026-08-23-md"></a>

## growth8_odd_skew_additive_2026-08-23

Source: `research-notes/growth8_odd_skew_additive_2026-08-23.md`.

### Additive and rank conditions at drift `(1,±3)`

#### Statement

Write the drift as `d=(1,3s)`, where `s` is `1` or `-1`, and translate the
configuration so that the period-start cell has even checker parity.  For an odd
translation class with base `(x,y)`, put

```text
j = y mod 3,       n = x-s floor(y/3).
```

Both quantities are constant under translation by `d`, apart from the fixed
choice of the residue representative `j`.  The checker sign is
`(-1)^(n+j)`.  Every finite-support growth-eight highway in either orbit must
satisfy

```text
sum_O (-1)^(n+j)n = 2-s  (mod 4).                       (1)
```

Thus the right side is `1` for `(1,3)` and `3` for `(1,-3)`.  This moment is
independent of the three P22 equations in the `y mod 3` residues.  Together,
those four equations exhaust the drift-periodic additive mod-four weights with
zero four-corner sum.

There is also a lifted-rank condition.  For each residue `j`, let `U_j` be the
set of its four or two longitudinal coordinates, ordered as follows:

```text
d=(1,3):       U_j={n},
d=(1,-3):      U_j={3n+j}.
```

For `i<j`, put

```text
I_ij=#{(u,v) in U_i x U_j : u<v}  (mod 2).
```

Every highway in either orbit must satisfy

```text
I_01+I_02+I_12=0  (mod 2).                               (2)
```

Conditions (1)--(2) narrow both orbits but do not exclude either one.

#### The remaining generator

If `w` is such a weight, write

```text
w(x,y)=(-1)^(x+y) f(x,y).
```

The four-corner equation says that the mixed difference of `f` vanishes, so
`f(x,y)=A(x)+B(y)`.  Drift periodicity then gives a constant `c` with

```text
A(x+1)-A(x)=c,       B(y+3s)-B(y)=-c.
```

After absorbing one constant into `B`, every solution has the form

```text
f(x,y)=c[x-s floor(y/3)]+beta_(y mod 3),                 (3)
```

where `c,beta_0,beta_1,beta_2` are arbitrary modulo four.  The three `beta`
generators are exactly the signed residue charges already used in P22.  The only
new generator is therefore

```text
w_s(x,y)=(-1)^(x+y)[x-s floor(y/3)].                    (4)
```

It is periodic under `(x,y)->(x+1,y+3s)`, and its four-corner sum is zero.
Integrating the north-heading potential along two northeast diagonals and one
reversed southeast diagonal for `s=1`, or along the reversed path for `s=-1`,
gives monodromy

```text
2+s  (mod 4).
```

Charge conservation is consequently

```text
sum_O w_s + 2+s = 0  (mod 4),
```

which is (1).  A residue generator with coefficient `beta_j` has monodromy
`2 beta_j`; its endpoint equation is the P22 signed sum in residue `j`.  This
proves the completeness assertion following (1).

#### The rank sign

Use the invariant transverse coordinate `t=3x-sy`.  At an even quotient vertex
the outgoing blocks are `W,E`, with targets `t-3,t+3`.  At an odd vertex they are
`S,N`, with targets `t+s,t-s`.  Reducing all block multiplicities modulo two,
the incoming and outgoing sums at a vertex both equal its odd-class indicator.

This finite flow is unique.  A nonzero zero-boundary flow with a least source
level would contain the block pointing below that level; the zero incoming sum at
its target would require a second block from a still lower source.

P22 gives an even number of endpoints in each `y mod 3` fibre.  Pair consecutive
endpoints in each fibre.  The unique flow is the symmetric difference of the four
resulting finite segments.  Comparing source and target port orders gives a short
interaction table:

- at `(1,3)`, every segment has self-sign zero;
- at `(1,-3)`, every segment has self-sign one, and the four self-signs cancel;
- two segments in the same residue fibre have zero cross term; and
- two segments in different fibres contribute the interlacing of their endpoint
  pairs in the ordering used to define `U_j`.

Summing the table gives

```text
E+L=I_01+I_02+I_12.                                    (5)
```

The checker count is odd in these two drift orbits, so the period congruence has
`N=2` or `6 (mod 8)`.  Hence `#L=(N-8)/2` is odd.  Exact P3 alternation gives
`K=#L=1`, while the one-tour port factorization is `K=1+E+L`.  Therefore
`E+L=0`, proving (2).

#### Compatibility

P22 forces the unsigned counts in the three `y` residues to be a permutation of
`4,2,2`.  The two-class residues have a common checker sign, while the four-class
residue has a `3+1` checker split.  These conditions leave unbounded freedom in
the longitudinal integers `n`.

The additive audit takes distinct `n` values from `[-5,5]`.  For each chirality it
finds 300,000 P22 configurations and 150,000 satisfying (1), split evenly among
the three possible positions of the four-class residue.  The exact half is a
useful check that the moment is independent, but the surviving 150,000 placements
make clear that it is not an exclusion.  A separate direct-flow audit on
`n in [-3,3]` checks all 1,944 additive survivors; 824 also satisfy (2) in each
chirality.

#### Audit

```text
python code/python/growth8_odd_skew_moment_audit.py \
  --output results/growth8_odd_skew_moment_audit.json
```

The program checks all 256 choices of the four coefficients in (3), their
four-corner sums, drift periodicity, and potential monodromy in both chiralities.
It then performs the bounded endpoint count above.  The output reports
`all_checks_passed=true`.

The lifted-rank regression is

```text
python code/python/growth8_odd_skew_rank_parity_audit.py \
  --output results/growth8_odd_skew_rank_parity_audit.json
```

It checks 420 segment self/cross interactions in each chirality, solves every
bounded parity flow directly, verifies uniqueness, and compares all 3,888 direct
signs with (5).

```text
growth8_odd_skew_moment_audit.py
a646c006962206d0b2f2292f4ac623e1d785a475931465b47c065c4ea922cd22

growth8_odd_skew_moment_audit.json
41af3e8d851150cf2fa7c520aafdfe79d6cdb93ab04c96bb0f1d9fdea6dea364

growth8_odd_skew_rank_parity_audit.py
8f089ffce4281679ef1578b327dde930097b76a776f92b27037e67a2bd4b9b31

growth8_odd_skew_rank_parity_audit.json
d0661aa367d11bdff6693fd63f310a3a20f2d3a1258f8e7e27c37d43927e6f92
```

<a id="source-research-notes-growth8-primitive-diagonal-boundary-2026-08-23-md"></a>

## growth8_primitive_diagonal_boundary_2026-08-23

Source: `research-notes/growth8_primitive_diagonal_boundary_2026-08-23.md`.

### The primitive-diagonal growth-eight boundary

#### Statement

Normalize the drift to `d=(1,-1)`, put `t=x+y`, and take the two guard rails to
have levels `1` and `W+1`. Let `O` be the set of the eight excess-one translation
classes, identified with their transverse levels. Every finite-support
growth-eight highway in this orbit satisfies

```text
sum_(t in O) (-1)^t t = 3  (mod 4).                    (1)
```

Together with the signed count from P22, this exhausts the drift-periodic
mod-four additive weights with zero four-corner sum. The quotient parity flow has
the closed rank sign

```text
E+L=|O|/2  (mod 2).                                    (2)
```

At growth eight the right side of (2) is zero, exactly as P3 requires. Thus (1)
is a new all-period restriction, but neither (1) nor (2) excludes the orbit.

#### The additive family

Write an arbitrary weight as

```text
w(x,y)=(-1)^(x+y) f(x,y).
```

The zero four-corner equation says that the mixed difference of `f` vanishes, so
`f=A(x)+B(y)`. Periodicity under `(x,y)->(x+1,y-1)` then gives a constant `c`
such that

```text
A(x+1)-A(x)=c,       B(y)-B(y-1)=c.
```

After moving a constant between `A` and `B`, every solution is

```text
f(x,y)=c(x+y)+beta.                                    (3)
```

The constant generator is the single P22 residue weight. Its north-heading
potential has monodromy `2 beta`. The remaining generator is

```text
w_1(x,y)=(-1)^(x+y)(x+y).
```

The start level is even after the rail normalization. Integrating the potential
along one southeast step gives monodromy one. Charge conservation is therefore

```text
sum_(t in O) (-1)^t t + 1 = 0  (mod 4),
```

which is (1). Equation (3) proves that there is no further condition in this
additive family.

#### The one-lane rank sign

The quotient has one vertex at every transverse level. At even levels the
outgoing blocks are `W,E`, and at odd levels they are `S,N`; in either case their
targets are the adjacent levels. Modulo two, both the incoming and outgoing sums
at a vertex equal its odd-class indicator.

The finite flow is unique. A nonzero zero-boundary flow with a least source has a
block pointing below that source, and its target then requires a block from a
still lower source. Pair the boundary levels consecutively. The flow is the
symmetric difference of the finite segments between the four endpoint pairs.
A direct comparison of source and target port orders gives self-sign one for
each segment and cross-sign zero for every pair of segments. Hence

```text
E+L=number of segments=|O|/2  (mod 2),
```

proving (2). The checker count is odd, so the period congruence makes
`#L=(N-8)/2` odd. Exact alternation gives `K=#L=1`, while the one-tour
factorization gives `K=1+E+L`. Both sides therefore ask for `E+L=0`; the rank
sign is compatible rather than contradictory.

#### Compatibility and audit

The horizontal/vertical wake split is one of `3+5`, `5+3`, or `7+1`, with the
two rail levels included among the horizontal classes. In the normalized window
between the rails, the audit enumerates every such placement at each even width
from ten through twenty. It finds 23,492 P22 placements and 11,746 satisfying
(1), exactly half at every width. All survivors have rank sign zero.

```text
python code/python/growth8_primitive_diagonal_boundary_audit.py \
  --output results/growth8_primitive_diagonal_boundary_audit.json
```

The program checks all sixteen weights in (3) over a representative lattice
window, including their potential monodromies. It also solves 238 bounded parity
systems directly, checks that each is unique, and compares every solution with
the segment construction and sign formula. These finite checks are regressions
for the displayed algebra; the all-period result is the classification and
finite-support segment proof above.

```text
growth8_primitive_diagonal_boundary_audit.py
302e1272de5cf556bab5738086e655171a1cdbaa5d84f80239da63d6453e5158

growth8_primitive_diagonal_boundary_audit.json
72c656636d0d6200a55613c5ffb84a6f8481c08ae0a9708def6675dcf8ffaf3a
```

<a id="source-research-notes-growth8-skew-rank-parity-2026-08-22-md"></a>

## growth8_skew_rank_parity_2026-08-22

Source: `research-notes/growth8_skew_rank_parity_2026-08-22.md`.

### Rank parity and an additive moment for the saturated skew drifts

This note treats the two growth-eight drift orbits represented by `(2,4)` and
`(2,-4)`.  It gives an all-period chronology condition, but not an exclusion.

#### Statement

Write the drift as `d=(2,4s)`, where `s` is `1` or `-1`, and use quotient
coordinates

```text
r = x mod 2,             t = 2x-sy.
```

The P22 residue matrix has one doubled `y mod 4` cell in one `r` lane and three
doubled cells in the other.  Translate the origin so that the two-class lane is
`r=0`, its cell has `y=0 mod 4`, and the six-class lane is `r=1`.  In the
`t` coordinate the four doubled fibres are then

```text
A: r=0, t=0 mod 4,
B_0,B_1,B_3: r=1, t=0,1,3 mod 4.
```

Let `T_j` be the two transverse levels occupied by the odd classes in `B_j`.
For two of these three fibres put

```text
I_ij = #{(u,v) in T_i x T_j : u<v}  (mod 2).
```

Every finite-support periodic highway in either skew orbit would satisfy

```text
I_01 + I_03 + I_13 = 1  (mod 2).                         (1)
```

There is also a mod-four moment.  Write

```text
S_A = sum_(t in A) t/4,
S_j = sum_(t in T_j) (t-j)/4,       j=0,1,3.
```

Then

```text
S_A-S_0+S_1+S_3 = -s  (mod 4).                           (2)
```

The definition is insensitive to which member of a pair is written first:
reversing the inequality replaces a count by `4-count`, which has the same
parity.  It is also preserved when the transverse orientation is reversed by a
quarter turn.

#### Why the boundary has this form

At `|b|=4`, the density inequality is saturated.  P22 therefore puts exactly two
odd classes in each `y mod 4` residue, with the same checker sign.  Both classes
must lie in one `x mod 2` lane.  The `x` margins are `2+6`, so one `y` residue is
assigned to the minority lane and the other three to the majority lane.  This is
the unique `2 x 4` count matrix up to translation.  The four cells are doubled,
which is why every set `T_j` has two elements congruent modulo four.

The checker split is `2+6`, and the period congruence gives

```text
N = 0  (mod 8).                                           (3)
```

#### The extra additive weight

The moment (2) does not come from the separate `x`- and `y`-residue indicators
used in P22.  Consider instead

```text
w_s(x,y)=(-1)^(x+y) [floor(x/2)-s floor(y/4)]  (mod 4).
```

It has zero four-corner sum and is periodic under `(x,y)->(x+2,y+4s)`.
Integrating the north-heading potential along three northeast diagonals and one
reversed southeast diagonal when `s=1` (and the reversed path when `s=-1`) gives
monodromy `3 mod 4`.  Conservation over one period is therefore

```text
sum_(o in O) w_s(o) + 3 = 0  (mod 4).
```

For `t=j+4k`, the values on the four normalized fibres are

```text
             A       B_0       B_1       B_3
s=1          k       -k        k         k+1
s=-1         k       1-k       k-1       k
```

Each fibre has two points.  Summing the appropriate row gives exactly (2).

#### The finite parity flow

Checker parity at `(r,t)` is `r+t mod 2`.  At an even vertex the ant arrives
vertically and its outgoing blocks are `W,E`; at an odd vertex the outgoing
blocks are `S,N`.  In the quotient the targets are

```text
E_r(t) -> (1-r,t+2),       W_r(t) -> (1-r,t-2),
N_r(t) -> (r,t-s),         S_r(t) -> (r,t+s).
```

Reduce all block multiplicities modulo two.  At each vertex the incoming and
outgoing sums both equal its odd-class indicator.  The finite solution is unique.
Indeed, a nonzero zero-boundary solution would have a block with least transverse
source level.  The paired outgoing block points lower; the required paired input
at its target comes from a still lower source.  This contradicts minimality.

Existence can be read off from four elementary chains.  For a doubled even vertex
at levels `u` and `u+4`, the six-block segment is

```text
E_r(u), W_r(u+4),
S_r(u+1), N_r(u+1), S_r(u+3), N_r(u+3).                 (3)
```

The only doubled odd vertex is `B_0`.  Its segment contains both horizontal
blocks and both vertical blocks at `(0,u+2)` and `(1,u+2)`, together with the
vertical block directed into the interval at `(1,u)` and the opposite block at
`(1,u+4)`.  Thus the endpoint blocks are `S_1(u),N_1(u+4)` when `s=1`, and
`N_1(u),S_1(u+4)` when `s=-1`.  Concatenating consecutive segments from `u` to
`v-4` gives the unique chain between any two endpoints `u<v` in one fibre.

#### The sign

Let `E` be the directed-block permutation sign and `L` the usual sum of local
port corrections.  Both are functions of the parity flow.  Comparing the source
and target orders of the blocks in (3) and in the odd-vertex segment gives the
following finite table.

- At drift `(2,4)`, a segment has zero self-sign.  Distinct segments interact
  only when they belong to two different majority-lane fibres and their chain
  indices differ by zero or minus one.
- At drift `(2,-4)`, every segment has self-sign one and consecutive segments in
  the same chain interact once.  A complete chain therefore has sign one,
  independently of its length.  There are four chains, so these four signs
  cancel.  The cross-chain table is the same as for `(2,4)`.

Summing the two nonzero relative positions over two finite chains telescopes to
the interlacing of their endpoint pairs.  The minority chain has zero cross term.
Consequently, in both chiralities,

```text
E+L = I_01 + I_03 + I_13  (mod 2).                       (4)
```

Put `ell=(x-r)/2` and `tau=i-N*ell`.  Along any one directed quotient block,
successor changes `tau` by a constant, including at the period seam.  Port sorting
therefore factors the one-cycle phase successor as `K=1+E+L`, where `K` is the
sum of the stable ranks of the left turns.  Exact P3 alternation puts every left
turn at odd rank, so `K=#L`.  By (3),

```text
#L = (N-8)/2 = 0  (mod 2).
```

Substitution in (4) proves (1).

#### Audit

The regression solves the finite GF(2) block system directly in both
chiralities, without inserting the chain solution.  It then computes `E+L` from
the block orders and local formulas and compares it with (4).  It separately
checks the four-corner weight, drift periodicity, potential monodromy, and (2).
The default run makes 148 segment self/cross checks, 1,446 additive-weight checks,
and 2,592 full boundary comparisons.  In each chirality, 184 of the 1,296 tested
placements satisfy both (1) and (2), so the combined result is still a restriction
rather than an exclusion.

```text
python code/python/growth8_skew_rank_parity_audit.py \
  --output results/growth8_skew_rank_parity_audit.json
```

```text
growth8_skew_rank_parity_audit.py
0efe7fe308bfcfabc521df8ab3050046c2982e8da548a8940b8bbab2060e139f

growth8_skew_rank_parity_audit.json
b852ac903b41e310ec995bc31a0b906a2d727881fbdc3b71e73923044973b1ca
```

<a id="source-research-notes-m4-alternating-half-rail-exclusion-2026-09-06-md"></a>

## m4_alternating_half_rail_exclusion_2026-09-06

Source: `research-notes/m4_alternating_half_rail_exclusion_2026-09-06.md`.

### An alternating upper half rail forces a nearby wake

Date: 2026-09-06. New research result derived from the project's September 4 cap-order note.

**Status:** a hand proof, with independently checked finite certificates as corroboration. This excludes the displayed September 4 partial-rail family at every period and every allowed width. It does **not** close the entire growth-eight drift orbit of `(-4,4)` (equivalently, after a half-turn, `(4,-4)`). This result has not been formalized in Lean or externally reviewed.

#### 1. Statement and scope

Use drift `d=(4,-4)`, transverse coordinate `t=x+y`, and horizontal arrivals on odd levels. Suppose the actual upper rail is `t=H`, its odd `x mod 4` classes are singleton `ER` events, and its even classes are absent. Then the next three inward levels cannot all be non-wake.

Here a wake class has an odd-length stable visit word; a non-wake class has an even-length word, possibly empty. P3 supplies first-white, alternating stable words at sufficiently far future physical copies.

In the **pure horizontal-wake branch**, the first and third inward levels are vertical-arrival levels and already have no wake. The theorem therefore says:

\[
\boxed{\text{An alternating upper half rail requires a wake on }t=H-2.}
\]

No condition on the fourth inward level, no lower-rail occupancy, and no bound on the period or rail separation is used.

In particular, the September 4 family has wakes at `t=1` in all four lanes, at `t=3` in lanes 0 and 2, and at `t=W+1` in lanes 1 and 3, with `W=8j+4>=12`. Its top three inward levels are non-wake. **Every member of that family is excluded.** The earlier family-specific bound `N>=8W+40` is superseded by this exclusion.

#### 2. Physical cells and the existing cap normal form

For integer `x`, define

\[
T_x=(x,H-x),\quad U_x=(x,H-1-x),\quad
V_x=(x,H-2-x),\quad P_x=(x,H-3-x),\quad Z_x=(x,H-4-x).
\]

These are physical cells, not just quotient classes. For example, `Z_(x+4)=Z_x+d`. All closed paths below return to exactly the same integer coordinates; crossing a quotient seam cannot change their conclusions.

Port labels give incoming heading and turn. Their outgoing directions are

| Port | NR | NL | ER | EL | SR | SL | WR | WL |
|---|---|---|---|---|---|---|---|---|
| Outgoing | E | W | S | N | W | E | N | S |

The September 4 cap-order proof, under precisely these upper-rail and three non-wake hypotheses, gives the following complete stable words:

| Cell | Word |
|---|---|
| `U_x`, even x | `NR NL` |
| `U_x`, odd x | `SR NL` |
| `V_x`, even x | `ER EL WR WL` |
| `V_x`, odd x, type A | `ER EL ER WL` |
| `V_x`, odd x, type B | `ER WL ER EL` |

If `V_(x+1)` is A, an even `P_x` has one of

- E1: `SR NL NR NL NR SL`;
- E2: `NR NL SR NL NR SL`;
- E3: `NR SL SR NL NR NL`.

If `V_(x+1)` is B, its even predecessor instead has

- EB: `NR NL NR SL SR NL`.

At odd `P_x`, type A at `V_x` gives

- O1: `NR NL SR SL SR NL`;
- O2: `SR NL NR SL SR NL`.

Type B gives `NR SL SR NL SR NL`.

The source derives these lists using directed-edge counts and closed four- and eight-step returns, without assuming that every rail lane is occupied. The accompanying verifier also reconstructs the admissible cap words directly from the singleton upper rail, so its enumeration does not merely assume these interior tables.

#### 3. Eliminate B and E3

Fix even `x`. In either EB or E3, the first south arrival at `P_x` is `SL`, and that event feeds the unique `EL` arrival at `V_(x+1)`. Consequently the following physical four-step return is forced:

\[
V_x:\mathrm{ER}\to P_x:\mathrm{SL}\to
V_{x+1}:\mathrm{EL}\to U_{x+1}:\mathrm{NL}\to V_x:\mathrm{WL}.
\]

There is no intermediate visit to `V_x`. But its complete word is `ER EL WR WL`, requiring two visits between those endpoints. This is impossible.

Thus every odd `V` has type A, every even `P` has type E1 or E2, and every odd `P` has type O1 or O2. The rest of the proof handles all four local E/O combinations. It does not need any additional global time-cycle pruning.

#### 4. Two forced returns at the fourth inward level

Fix even `x`. At the physical cell `Z_x`, let `n_1,...,n_4` denote its north-departure events in chronological order, and let `w_1,...,w_4` denote its west-arrival events in chronological order. There are exactly four of each: the former feed the four north arrivals at `P_x`, and the latter come from the four west departures at `P_(x+1)`.

An event can belong to both lists: precisely a `WR` event. A north departure is `EL` or `WR`; a west arrival is `WR` or `WL`. Successive visits at this physical cell alternate turns, regardless of whether the class is a wake.

##### The short return

The first `NR` at `P_x` is fed by `n_k`, where `k=2` in E1 and `k=1` in E2. It forces

\[
Z_x:n_k\to P_x:\text{first NR}\to V_{x+1}:\text{first ER}
\to P_{x+1}:\text{first SR}\to Z_x:w_l.
\]

Here `l=2` in O1 and `l=1` in O2. This is a four-step first return, so `n_k` and `w_l` are consecutive visits with opposite turns.

##### The long return

The last north departure `n_4` feeds the second `NR` at `P_x`. All remaining steps in the following table are forced by the cap words and ordered matching on each physical directed edge:

| Step | Cell and event |
|---:|---|
| 0 | `Z_x:n_4` |
| 1 | `P_x:second NR` |
| 2 | `V_(x+1):EL` |
| 3 | `U_(x+1):NL` |
| 4 | `V_x:WL` |
| 5 | `P_x:SL` |
| 6 | `V_(x+1):second ER` |
| 7 | `P_(x+1):SL` |
| 8 | `V_(x+2):EL` |
| 9 | `U_(x+2):NR` |
| 10 | `T_(x+3):ER` |
| 11 | `U_(x+3):SR` |
| 12 | `V_(x+2):WR` |
| 13 | `U_(x+2):NL` |
| 14 | `V_(x+1):WL` |
| 15 | `P_(x+1):last SR` |
| 16 | `Z_x:w_3` |

No intermediate cell is `Z_x`; the two endpoints are consecutive visits. If `n_4` were `EL`, its opposite-turn return would be `WR`, creating a fifth north departure. Therefore

\[
n_4=\mathrm{WR},\qquad w_3=\mathrm{WL},\qquad
n_4\text{ is either }w_1\text{ or }w_2.
\]

#### 5. Exhaust the four E/O combinations

**O1, either E1 or E2 (`l=2`).** If `n_k` is `WR`, its consecutive return `w_2` is `WL`. Since `k<=2`, `n_4` must be later than `w_2`. If `n_k` is `EL`, its consecutive return is `w_2=WR=n_(k+1)`; again `k+1<=3`, so `n_4` is later than `w_2`. Both contradict `n_4` being `w_1` or `w_2`.

**E1 with O2 (`k=2,l=1`).** The starting `n_2` cannot be `WR`, because that would itself be a west arrival before `w_1`. Hence `n_2=EL` and its consecutive return is `w_1=WR=n_3`. Thus `n_4=WR` must be `w_2`. Between the right-turn events `n_3` and `n_4`, alternation requires a left turn. An `EL` would be another north departure between consecutive `n_3,n_4`; a `WL` would be another west arrival between consecutive `w_1,w_2`. Neither is possible.

**E2 with O2 (`k=1,l=1`).** The same first-arrival reasoning gives `n_1=EL`, `w_1=WR=n_2`, and then `n_4=WR=w_2`. In O2, `w_2` comes from the `NL` event in the second position at `P_(x+1)`. The following eight-step first return is consequently forced:

\[
P_{x+1}:\mathrm{NL}\to Z_x:\mathrm{WR}\to P_x:\text{second NR}
\to V_{x+1}:\mathrm{EL}\to U_{x+1}:\mathrm{NL}\to V_x:\mathrm{WL}
\to P_x:\mathrm{SL}\to V_{x+1}:\text{second ER}\to P_{x+1}:\mathrm{SL}.
\]

There is no intermediate visit to `P_(x+1)`. Its O2 word `SR NL NR SL SR NL` requires an `NR` visit between those `NL` and `SL` endpoints. Contradiction.

All cases are impossible, proving the theorem.

#### 6. Independent computational corroboration

Run from the accompanying code directory:

```bash
python verify_m4_cap_frontier.py --output m4_cap_audit_2026-09-06.json
```

The completed audit reports:

- 49 cap assignments from the September 4 tables; 15 survive the local and lifted-time checks through `P`.
- Reconstruction from the singleton rail gives respectively 1, 4, and 15 surviving assignments after the `U`, `V`, and `P` levels, exactly matching the surviving table assignments.
- At one even `Z` lane, every possible alternating count word is enumerated: 3,390 extensions for wake bit 0 and 4,080 for wake bit 1 across the 15 caps. All 7,470 extensions have contradictions.
- In total 7,807 rejection certificates are checked: 7,805 impossible physical returns and two positive time cycles of weight `24+N`.
- Positive controls pass for the known 104-step highway and its twofold and threefold repetitions, using quotient lane counts 2, 4, 6 and periods 104, 208, 312.

The extension count domains are finite by exact nonnegative port equations, not by an arbitrary visit-multiplicity cutoff. For a horizontal cell with north-departure total `A`, west-arrival total `B`, and wake bit `D`, writing `c=WR` gives

\[
(ER,EL,WR,WL)=(A+B+D-3c,A-c,c,B-c).
\]

The verifier independently enumerates all nonnegative count boxes and alternating words, and checks equality with the engine's domain. Here `A=B=4`.

The engine may use a large numerical period to *discover* a time cycle, but it accepts an all-period rejection only after checking the cycle's exact integer coefficient and positivity for every integer `N>=1`. Physical-return certificates use no period parameter at all. The independent checker reconstructs physical coordinates and edge ordinals using its own explicit routing table. None of these checks establishes that a surviving partial word is a realizable highway.

#### 7. Subsequent strengthening and what is still open

The full pure eight-wake branch remains open. Subsequent work in `m4_full_rail_exclusion_2026-09-06.md` strengthens this local result: a wake on `H-2` is required in one of the upper rail's occupied lanes. It also handles the other upper-rail masks when the lower rail is full, proving that neither extremal rail can be full. Both-partial-rail configurations remain. No percentage of completion is justified: the remaining cases are unbounded in period and separation.

The next useful target is to combine the forced nearby wake with the exact two-wakes-per-x/y-residue budget and the additive height congruence. Any further cap enumeration should track which wake configurations it actually exhausts and distinguish partial-word survivors from genuine periodic candidates.

#### Source notes

- [September 4 cap-order note](04_Growth_eight.md#source-research-notes-m4-partial-rail-cap-order-2026-09-04-md): source normal form and earlier period bound.
- [September 4 partial-rail family](04_Growth_eight.md#source-research-notes-growth8-m4-partial-rail-obstruction-2026-09-04-md): the family now excluded.
- [September 3 occupancy-scope audit](04_Growth_eight.md#source-research-notes-rail-occupancy-scope-audit-2026-09-03-md): why partial rails must be retained in the full orbital problem.
- [September 4 pure-wake additive normal form](04_Growth_eight.md#source-research-notes-growth8-m4-pure-additive-normal-form-2026-09-04-md): residual global additive condition.

<a id="source-research-notes-m4-full-rail-exclusion-2026-09-06-md"></a>

## m4_full_rail_exclusion_2026-09-06

Source: `research-notes/m4_full_rail_exclusion_2026-09-06.md`.

### Growth eight at diagonal drift four: neither extremal rail can be full

Date: 2026-09-06.

**Result:** in the remaining pure horizontal-wake branch of the growth-eight drift orbit `(-4,4)` / `(4,-4)`, neither extremal rail can occupy all four quotient lanes. Thus any remaining candidate must have **both rails partially occupied**.

This is an all-period reduction, not closure of the orbit. The proof combines exact finite local certificate proofs with a symbolic rank-sign calculation. It has not been formalized in Lean or externally reviewed. It uses the project's established P3, extremal singleton, coordinate-fibre, period, and rank-factorization results.

#### 1. Existing reductions and notation

Write `t=x+y`, `r=x mod 4`, and put horizontal-arrival classes on odd levels. The existing growth-eight reductions give:

- exactly eight wake classes, all horizontal in the remaining pure branch;
- exactly two wakes in every x-residue and every y-residue;
- period `N=0 mod 8`;
- each occupied class on an actual extremal rail is a singleton right-turn event;
- rail separation `W>=10`.

Upper-rail events are `ER`, lower-rail events are `WR`. We do not assume that all lanes on either rail are occupied. A wake class has odd stable multiplicity; a non-wake class has even multiplicity. P3 makes each stable word start with R and alternate turns at a physical cell sufficiently far in the future.

Assume for contradiction that the lower rail is full. Translate it to `t=1` and put the upper rail at `t=H`. Let `S` be the set of occupied upper lanes. The lower rail already supplies one wake in every x- and y-residue, so the other four wakes supply each residue exactly once.

The upper rail is nonempty. Up to a cyclic lane shift its mask is one of

| Occupancy | Lane set |
|---|---|
| One lane | `{0}` |
| Two adjacent lanes | `{0,1}` |
| Two alternating lanes | `{1,3}` |
| Three lanes | `{0,1,2}` |
| Four lanes | `{0,1,2,3}` |

These are all nonempty four-lane masks up to translation.

#### 2. Three exact local obstructions

Denote the four inward levels by `U=H-1`, `V=H-2`, `P=H-3`, and `Z=H-4`. In the pure branch `U` and `P` have no wake. The local statements below do not require any lower-rail hypothesis.

**L1 — one occupied upper lane.** If the upper rail is occupied only in lane 0, there must be a wake in lane 0 at `V`. This holds whatever the wake bits in the other three lanes at `V`.

**L2 — two adjacent occupied upper lanes.** If the upper rail occupies lanes 0 and 1, the entire `V` level cannot be non-wake. No restriction on wake at `Z` is needed.

**L3 — two alternating occupied upper lanes.** If the upper rail occupies lanes 1 and 3, `V` must contain a wake in lane 1 or 3. Wakes confined to lanes 0 and 2 do not suffice. No restriction on wake at `Z` is needed.

The separate note `m4_alternating_half_rail_exclusion_2026-09-06.md` gives a hand proof of the weaker form of L3 with no wakes anywhere at `V`; it already excludes the September 4 displayed family. The following complete finite certificate audits establish L1, L2, and the stronger L3.

##### Why the local enumeration is exhaustive

Start with just the singleton upper-rail words. At each successive level, counts entering from and exiting into the preceding level are fixed. All directed-edge occurrences are matched in their actual chronological order at physical neighboring cells.

For a horizontal-arrival cell, let `A` be its number of north departures, `B` its number of west arrivals, and `D` its wake bit. With `c=WR`, all possible count rows are exactly

\[
(ER,EL,WR,WL)=(A+B+D-3c,A-c,c,B-c),
\]

where all four entries are nonnegative. For a vertical-arrival cell, let `A` be its number of east departures, `B` its number of south arrivals, and `D` its wake bit. With `d=SL`, all possible rows are exactly

\[
(NR,NL,SR,SL)=(A-d,A+B-D-3d,B-d,d).
\]

For each row, enumerate every first-R alternating word with those port counts. Nonnegativity bounds `c` or `d`, hence the domain is finite without a visit-count or period cutoff.

A rejection certificate is a forced sequence of actual unit steps that first returns to the same physical cell but skips one or more required stable visits, returns to an earlier visit, or returns to the starting visit. Each is impossible. The validator independently reconstructs the physical coordinates, verifies the outgoing direction and the ordinal matching on every directed edge, checks that no intermediate point is the starting cell, and checks the inconsistent endpoint rank.

For these three lemmas the audit uses **only physical-return certificates**. It uses no numerical period, no time-cycle rejection, no wake-degree pruning, and no inherited interior word table. A separate nonnegative count-box enumeration and recursive word generator check equality with every domain used by the search.

##### Completed enumeration sizes

L1 exhausts all eight wake masks at `V` omitting lane 0. Each gives one `U` assignment, one surviving `V` assignment, and **zero `P` assignments**.

L2 starts from its rail and obtains 2 assignments at `U`, 7 at `V`, and 4 at `P`. At lane 2 of `Z`, all 1,992 words across both wake bits and all four caps are impossible. Enumerating the other `Z` lanes is unnecessary.

L3 exhausts the four `V` wake masks supported on the even lanes:

| Wake lanes at V | U assignments | V assignments | P assignments | Z lane 0 words, D=0 | Z lane 0 words, D=1 | Survivors |
|---|---:|---:|---:|---:|---:|---:|
| none | 1 | 4 | 16 | 3,616 | 4,352 | 0 |
| `{0}` | 1 | 4 | 16 | 7,584 | 9,088 | 0 |
| `{2}` | 1 | 4 | 16 | 7,584 | 9,088 | 0 |
| `{0,2}` | 1 | 4 | 16 | 18,176 | 21,792 | 0 |

The 16 `P` assignments in this physical-only audit include one assignment discarded by the older lifted-time audit, explaining the different count of 15 in the companion hand-proof audit. The 16-assignment audit excludes it directly at `Z` as well.

The known 104-step highway and its twofold and threefold repeats remain valid positive controls in lane quotients 2, 4, and 6.

#### 3. Eliminate upper occupancies one and two

With a full lower rail, an upper-occupied lane already has its two allowed wakes. L1 would require a third wake in that lane when the upper occupancy is one; contradiction.

L3 likewise requires a third wake in one of the occupied upper lanes when the occupancy is an alternating pair; contradiction.

For an adjacent pair `S={0,1}`, a wake on `V=H-2` cannot use lane 0 or 1 by the x-residue budget. It also cannot use lane 2 or 3: the y-residues there are respectively `H` and `H-1` modulo four, already occupied by the two upper wakes and by the full lower rail. Thus every `V` lane must be non-wake, contradicting L2.

Equivalently, the x/y budget allows `V` wakes only outside `S union (S+2)`. For an adjacent pair this union is all four lanes.

#### 4. Eliminate upper occupancy three by rank sign

Normalize the upper occupied lanes to `{0,1,2}`. The eighth wake must lie in lane 3, at some odd interior level `J`. Since the lower rail contributes every y-residue once and the upper rail contributes y-residues `H,H-1,H-2`, the remaining wake must have y-residue `H-3`. Therefore

\[
J\equiv H\pmod4,\qquad 1<J<H.
\]

Put `k=(H-J)/2`. Then `k` is positive and even.

##### Parity flow

Use the project's pure-horizontal parity recurrence. At odd level `j`, north-edge parity is `b_j` and south-edge parity is `b_(j-2)`. At even level `t`, east and west edge parities agree and are `a_t`. With the zero boundary below the strip,

\[
b_{j,r}=b_{j-2,r}+D_{j,r},\qquad
a_{j+1,r+1}=a_{j-1,r-1}+D_{j,r}
\quad\text{over }\mathbb F_2.
\]

Write `f=(1,1,1,1)` and let `m_i` be `f` with lane i removed. The unique finite flow is:

- `b_j=f` for odd `1<=j<J`, and `b_j=m_3` for odd `J<=j<H`;
- `a_t=f` for even `2<=t<J`;
- `a_(J+1+2i)=m_0` for even i and `m_2` for odd i, for `0<=i<k`;
- all other entries vanish.

This follows by substituting the lower full wake, the lane-3 wake at `J`, and the upper three wakes into the recurrence. The evenness of k makes the flow vanish above H.

##### Local correction

The rank correction is

\[
\Lambda=\sum_Q p_v(D_v+1)+\sum_C D_v(p_v+1)\pmod2,
\]

where `p_Q(t,r)=b_(t-1,r)+a_(t,r)` and `p_C(j,r)=a_(j-1,r-1)+b_(j,r)`.

Below J, every Q correction is zero. On each of the k intermediate even levels, `m_3` differs from `m_0` or `m_2` in exactly two places, so the sum of Q corrections is even. Every wake C class has `p=1`: this is immediate at the lower rail and the lone wake; at the upper rail the last a-mask is `m_2`, and its predecessor-lane values are one in lanes 0, 1, and 2. Therefore `Lambda=0`.

##### Edge inversion sign

Use source and target block order `(level,lane,negative-before-positive)`, as in the September 4 parity note. Its paired adjacent-level terms cancel. The horizontal-source contribution is

\[
E_C=\sum_j\left[\binom{|b_j|}{2}+|b_j|+
\sum_{r<s}b_{j,r}b_{j-2,s}\right]\pmod2.
\]

The self terms for f and `m_3` are respectively 10 and 6, both even. The transition `m_3` against f contributes 6. Each of the `k-1` subsequent `m_3`/`m_3` terms contributes 3. Hence `E_C=k-1=1 mod 2`.

For vertical sources, the self term of a mask a is

\[
G(a)=\binom{|a|}{2}+a_0(|a|-a_0)+a_3(|a|-a_3),
\]

and a successive-level term is

\[
B(a,b)=\sum_{r,s}a_rb_s\,\mathbf1_{(r+1\bmod4)\ge(s-1\bmod4)}.
\]

Here `G(f)=12`, `G(m_0)=5`, and `G(m_2)=7`. The k intermediate self terms sum to zero modulo two because k is even. The transition counts are

| Transition | B |
|---|---:|
| f to f | 10 |
| f to m_0 | 9 |
| m_0 to m_2 | 6 |
| m_2 to m_0 | 6 |

Thus `E_Q=1`, so `E=E_C+E_Q=0`. Together with `Lambda=0`, this gives `E+Lambda=0` for every permitted J and H.

##### Contradiction

The project's rank factorization requires `K=1+E+Lambda mod 2`, hence K odd. But stable alternation and growth eight give

\[
K\equiv\#L=(N-8)/2\equiv0\pmod2
\]

because `N=0 mod 8`. Contradiction. No height bound or finite placement search is used in this calculation.

#### 5. Finish the full-rail exclusion

If the upper rail is also full, all eight wakes lie on the two rails. The existing full/full rank proof gives `E=Lambda=0` and the same contradiction. It also follows from the preceding block formulas with every nonzero a- and b-mask equal to f: all self, transition, and local sums are even.

Every possible upper occupancy has now been excluded when the lower rail is full. A half-turn preserves Langton's rule and exchanges the two extremal rails. The local proofs use only physical returns, and the rank proof uses only parity flow and the same period congruence; both apply with either sign of the diagonal drift. Hence a full upper rail is excluded as well.

#### 6. Exact remaining boundary

The entire orbit is still open. What is now necessary in its pure branch is

\[
1\le |S_{\rm lower}|\le3,\qquad1\le |S_{\rm upper}|\le3.
\]

The new local conditions still apply to those partial rails. In particular, a singleton rail requires a same-lane wake two levels inward, and an alternating half rail requires such a wake in at least one occupied lane. Both rails can now consume the eight-wake budget through nearby interior wakes; proving that all remaining arrangements are impossible requires another argument.

No percentage or claim of being a fixed number of lemmas from closure is justified. The remaining periods and transverse separations are unbounded.

A concrete algebraically surviving placement is

\[
D=\{(1,0),(1,1),(1,2),(7,3),(9,3),(11,0),(11,1),(11,2)\}.
\]

Both rails occupy three lanes. Every x/y residue has degree two; the pure-wake additive parameters are `a=b=1`, `Z=9`, satisfying `Z=a+b-1 mod 4`; and direct parity-block evaluation gives `E=1`, `Lambda=0`, the permitted rank sign. This is **only relaxed wake data**: no chronological P3 word, finite seed, or actual highway has been constructed. It demonstrates why the algebraic tests do not by themselves finish the reduced problem.

**Update, September 7:** The displayed placement is now excluded by a complete two-ended local-word enumeration and independently checked middle-interface contradictions. This is an all-period exclusion of that specific placement, under the project's established reductions. See `m4_partial_rail_progress_2026-09-07.md` and `m4_two_ended_audit_2026-09-06.json`. The new continuation also forces at least six wakes onto the four boundary levels and classifies the remaining boundary-only patterns. The whole orbit remains open.

#### 7. Reproduction and research record

Run:

```bash
python verify_m4_full_rail_exclusion.py --output m4_full_rail_audit_2026-09-06.json
```

This recomputes the single-, adjacent-, and alternating-rail certificates, checks every local domain independently, checks the rank transition table, corroborates the rank calculation by direct edge-block sorting on finite examples, and includes rank-passing controls from the old relaxed family. The finite rank examples corroborate the symbolic proof; they are not substituted for it.

The three-lane local cap survey did retain partial-word assignments. They are not highways. The all-period rank contradiction above excludes their required global wake completion when the lower rail is full. This distinction prevented treating a surviving local relaxation as evidence against the new global reduction.

Sources:

- [September 4 cap-order note](04_Growth_eight.md#source-research-notes-m4-partial-rail-cap-order-2026-09-04-md).
- [September 4 partial-rail parity formulas and relaxed family](04_Growth_eight.md#source-research-notes-growth8-m4-partial-rail-obstruction-2026-09-04-md).
- [Mixed-wake exclusion and coordinate-fibre reduction](04_Growth_eight.md#source-research-notes-growth8-m4-mixed-rank-exclusion-2026-09-04-md).
- [Conditional full/full rank exclusion](04_Growth_eight.md#source-research-notes-growth8-extremal-m4-exclusion-2026-08-22-md).
- [Rail-occupancy scope audit](04_Growth_eight.md#source-research-notes-rail-occupancy-scope-audit-2026-09-03-md).

<a id="source-research-notes-m4-partial-rail-cap-order-2026-09-04-md"></a>

## m4_partial_rail_cap_order_2026-09-04

Source: `research-notes/m4_partial_rail_cap_order_2026-09-04.md`.

### Exact visit orders below an alternating half rail

The partial-rail family in `growth8_m4_partial_rail_obstruction_2026-09-04.md`
passes the residue and rank tests. Exact visit order removes some of the
count patterns that those tests allow. This note derives its upper-cap
normal form through three inward levels, using closed same-cell returns.
It does not exclude the family.

Subsequent status: [the alternating-half-rail argument](04_Growth_eight.md#source-research-notes-m4-alternating-half-rail-exclusion-2026-09-06-md)
excludes this explicit family. The normal forms and lower period bound derived
here remain necessary conditions; the final gap statement records the earlier
checkpoint. The whole growth-eight drift orbit remains open.

#### Hypotheses and physical cells

Normalize the drift to `(4,-4)`. Write `t=x+y`, with horizontal arrivals
on odd levels and vertical arrivals on even levels. Let the actual upper
rail be `t=W+1`, where `W` is even. Only its odd `x mod 4` lanes are
visited, each at a singleton ER event. Its even lanes are unvisited.

Assume the classes on the next three inward levels are non-wake. These
are exactly the upper-cap hypotheses in the displayed partial-rail family
when `W>=12`. Write the physical cells as

```text
T_x = (x,W+1-x),      U_x = (x,W-x),
V_x = (x,W-1-x),      P_x = (x,W-2-x).
```

All arguments use sufficiently far future copies, where P3 gives the actual
first-white, alternating visit order. The index `x` is an integer, not merely
a residue: `T_(x+4)=T_x+d`, and likewise on the other levels. This keeps
every return at the same physical cell even across a quotient seam.

Port labels give the incoming heading followed by the turn. Count vectors
on horizontal-arrival cells have order `(ER,EL,WR,WL)`; on vertical-arrival
cells they have order `(NR,NL,SR,SL)`.

#### The first inward level

At an even-indexed `U_x`, no arrival comes from above, and exactly one east
departure feeds `T_(x+1)`. Zero excess therefore gives `NR=NL=1` and no
other ports. At an odd-indexed `U_x`, the singleton `T_x` supplies one south
arrival, while east departures would reach an unvisited rail cell and are
forbidden. Zero excess gives `SR=NL=1`. Thus the complete stable words are

```text
U_x, x even: NR,NL
U_x, x odd:  SR,NL.
```

In particular, all four classes at this level have exactly two visits.

#### A four-step return fixes the even lanes of the next level

For even `x`, `V_x` has two west arrivals, from the two departures of
`U_(x+1)`, and two north departures, feeding `U_x`. If `c=WR`, then

```text
EL=WL=2-c,       ER=4-3c.
```

Nonnegativity leaves the count rows `(4,2,0,2)` and `(1,1,1,1)`. For odd
`x`, both totals are one, giving `EL=WL=1-c`, `ER=2-3c`; only the row
`(2,1,0,1)` remains.

Let `x` be even and let `A_x` be the first NR time at `U_x`. Its physical
predecessor is a north departure from `V_x` at time `A_x-1`. The following
path is forced:

```text
V_x -> U_x:NR -> T_(x+1):ER -> U_(x+1):SR -> V_x.
```

Its directions are `N,E,S,W`. It returns to `V_x` at time `A_x+3`, without
an intermediate visit to that cell. This endpoint is the first west arrival
there: the two west arrivals come from the same physical `U_(x+1)`, whose
order is SR,NL, and the displayed departure is its SR.

The starting north departure cannot be WR, since that would itself be an
earlier west arrival at `V_x`. It is EL. Consecutive same-cell visits have
opposite turns, so the endpoint is WR. This eliminates the eight-visit count
row. In the remaining four-visit row, EL,WR are consecutive; stable
alternation fixes the complete word:

```text
V_x, x even: ER,EL,WR,WL.
```

The WR at `A_x+3` immediately reaches `U_x` at `A_x+4`, its last NL visit.
Consequently the two visits to each even `U_x` are exactly four steps apart.

The odd lanes still have precisely two alternatives:

```text
A: ER,EL,ER,WL
B: ER,WL,ER,EL.
```

Both are retained below.

#### An eight-step return fixes the odd lanes one level farther in

For odd `x`, `P_x` has three south arrivals from `V_x` and two east
departures feeding `V_(x+1)`. With `a=SL`, zero excess gives

```text
(NR,NL,SR,SL) = (2-a,5-3a,3-a,a).
```

The possible count rows are `(2,5,3,0)` with ten visits and `(1,2,2,1)`
with six visits.

Put `A=A_(x+1)`. The last east departure `J` from `P_x` feeds the second
and last east arrival, EL, at `V_(x+1)`. It occurs at `A-2`. The cap words
just proved force this return:

| time | physical cell and port |
|---|---|
| `A-2` | `P_x:J` |
| `A-1` | `V_(x+1):EL` |
| `A` | `U_(x+1):NR` |
| `A+1` | `T_(x+2):ER` |
| `A+2` | `U_(x+2):SR` |
| `A+3` | `V_(x+1):WR` |
| `A+4` | `U_(x+1):NL` |
| `A+5` | `V_x:WL` |
| `A+6` | south arrival at `P_x` |

Its directions are `E,N,E,S,W,N,W,S`, with zero displacement. No intermediate
event lies on the `P` level. Its endpoints are therefore consecutive visits
to the same physical `P_x`, and their turns are opposite.

The ten-visit count row has no SL: both an east departure and a south arrival
would turn R, which is impossible here. In the six-visit row, if `J` were NR,
the earlier east departure would already have used the unique SL. The return
would require that same SL after `J`, another impossibility. Hence

```text
first east departure = NR,
last east departure J = SL,
return endpoint = SR,
```

with SL,SR consecutive in the stable word.

The six visits alternate R,L. If SL is in the second position, the earlier
NR must be first, giving `NR,SL,SR,NL,SR,NL`. If SL is in the fourth
position, the earlier NR can be first or third, giving the other two words
in the table below. A final-position SL cannot have its consecutive return.

| odd-lane word at `V_x` | complete possibilities at `P_x` |
|---|---|
| A: `ER,EL,ER,WL` | `NR,NL,SR,SL,SR,NL` or `SR,NL,NR,SL,SR,NL` |
| B: `ER,WL,ER,EL` | `NR,SL,SR,NL,SR,NL` |

To distinguish the rows, the return is fed by `V_x:WL`. In A this is its
last south departure, so the endpoint must be the last south arrival at
`P_x`. In B it is the middle south departure, selecting the middle-arrival
alternative. Directed-edge matching preserves the actual visit order.

#### A four-step return fixes the even lanes of `P`

For even `x`, there are two south arrivals at `P_x` and three east
departures feeding `V_(x+1)`. Writing `a=SL` gives

```text
(NR,NL,SR,SL)=(3-a,5-3a,2-a,a),
```

so the count rows before using chronology are `(3,5,2,0)` and
`(2,2,1,1)`.

Let `J` be the east departure from `P_x` that feeds the unique `EL` event
at `V_(x+1)`. The cap words force the closed return

```text
P_x:J -> V_(x+1):EL -> U_(x+1):NL -> V_x:WL -> P_x.
```

Its directions are `E,N,W,S`. No intermediate event is on the `P` level,
so its endpoints are consecutive visits to the same physical `P_x` and
have opposite turns. The return endpoint is the second and last south
arrival at `P_x`, because `V_x:WL` is the second south departure from the
even-lane word `ER,EL,WR,WL`.

The ten-visit row has no `SL`. Its departure `J` would therefore be `NR`,
but the opposite-turn return on an incoming south port would have to be
`SL`, a contradiction. Thus every even `P` lane has the six-visit count
row

```text
(NR,NL,SR,SL)=(2,2,1,1).
```

Directed-edge order determines the position of `J`. If `V_(x+1)` has
type A, its east-arrival subsequence is `ER,EL,ER`, so `J` is the second
east departure from `P_x`. If it has type B, that subsequence is
`ER,ER,EL`, so `J` is the third. Inserting the consecutive opposite-turn
endpoint into the six-place alternating word leaves exactly

| odd-lane word at `V_(x+1)` | complete possibilities at even `P_x` |
|---|---|
| A: `ER,EL,ER,WL` | `SR,NL,NR,NL,NR,SL`; `NR,NL,SR,NL,NR,SL`; or `NR,SL,SR,NL,NR,NL` |
| B: `ER,WL,ER,EL` | `NR,NL,NR,SL,SR,NL` |

Together with the preceding table, every class on the fourth level from
the upper rail now has exactly six visits and an explicit finite list of
stable port words.

#### Period cost in the explicit partial-rail family

For the family with `W=8j+4>=12`, the top four levels now have at least

```text
2 + 8 + 16 + 24 = 50
```

period visits: two at the rail, two in each `U` class, four in each `V`
class, and at least six in each `P` class.

The full lower rail contributes four visits. Each class at level two has
one north arrival and one west departure. Zero excess forces its count row
`(NR,NL,SR,SL)=(1,0,1,2)`, so that level contributes sixteen visits.
Every level-three class consequently has three east arrivals and three
south departures. If its wake bit is `D`, its horizontal count row is

```text
(ER,EL,WR,WL)=(a,3-a,6+D-3a,3-a).
```

For the two wake classes `D=1`, the least possible multiplicity is five;
for the two non-wake classes it is four. The bottom three levels therefore
contribute at least `4+16+18=38` visits.

There are `W-6` remaining levels, from four through `W-3`. The unique
parity flow and local multiplicity residues in the partial-rail note force
at least eight visits on each. At every even level all four multiplicities
are `2 mod 4`. At each odd level the two odd lanes have odd north and south
edge counts, so they are visited; their multiplicities are `0 mod 4`, hence
at least four apiece. No occupancy of the other two lanes is assumed.

Summing these disjoint sets of levels gives

```text
N >= 50+38+8(W-6) = 8W+40.
```

In particular this family requires `N>=136`. This is a hand-derived
exclusion of its smaller periods, not an exclusion at arbitrary period.

#### Remaining gap

The odd `V` alternatives and the displayed finite word lists at `P` survive
the argument. The layers below `P` have not been forced into a contradiction.
Thus the partial-rail family remains unresolved after these chronological
restrictions. No simulation or mathematical enumeration was used to derive
them.

<a id="source-research-notes-m4-partial-rail-progress-2026-09-07-md"></a>

## m4_partial_rail_progress_2026-09-07

Source: `research-notes/m4_partial_rail_progress_2026-09-07.md`.

### Growth eight, diagonal drift four: partial-rail progress

Research checkpoint: 2026-09-07. Target: the drift orbit represented by
\((-4,4)\), normalized below to \(d=(4,-4)\).

**The orbit remains open.** This checkpoint adds checked local exclusions,
excludes the particular width-ten placement displayed in the previous note,
and classifies the remaining boundary-only wake patterns at every width.
It does not establish nonexistence of every growth-eight highway in this orbit.
There is no defensible completion date or percentage: the remaining obstacle
is an argument for unbounded visit orders and transverse separation.

#### 1. Assumptions and conventions

Use the project's finite-seed P3 criterion and its established reductions:
the mixed wake branch is excluded; in the remaining branch all eight wake
classes have horizontal arrivals; each x-residue and each y-residue modulo
four contains exactly two wakes; the period is divisible by eight; and the
extremal occupied levels are separated by even width \(W\ge10\).
The existing small-period work gives \(N\ge64\). The September 6 full-rail
exclusion shows that each extremal rail occupies one, two, or three lanes.

Write \(t=x+y\), \(r=x\bmod4\), normalize the lower rail to \(L=1\),
and put \(H=L+W\). Horizontal-arrival classes C have odd t; vertical-arrival
classes Q have even t. A wake is a translation class whose stable visit word
has odd length. Stable words alternate R,L, starting R. An actual upper
rail class is the singleton word ER; an actual lower rail class is WR.
A lane mask m means \(\{r: m\mathbin{\&}2^r\ne0\}\).

These are research proofs with executable independent checks. They are not
formally verified in a proof assistant or externally peer reviewed.

#### 2. Singleton companion and the six-wake boundary budget

**Companion theorem.** If the upper rail occupies only lane r, then both
\((H-2,r)\) and \((H-2,r+1)\) are wakes. At a singleton lower rail in lane s,
both \((L+2,s)\) and \((L+2,s-1)\) are wakes. Lane arithmetic is modulo four.

The previous local lemma supplies the same-lane companion. For the new
companion normalize r=0. If lane 1 at H-2 is not a wake, the mask there is
one of 1,5,9,13. Lane 0 at H-4 cannot be a wake: its two x-residue wakes are
already used. The other three bits at H-4 are arbitrary. The three intervening
Q levels have no wakes. These are exactly 32 finite local cases.

`verify_singleton_hand.py` exhausts their count and word domains. It rebuilds
excursions using integer (x,y) coordinates and the chronological matching of
the nth directed-edge occurrences. Its independent count-box and word-position
enumerator agrees with the faster generator on every domain. The final audit
performs 24,740 excursion comparisons and 24,740 complete domain comparisons,
and checks 102,538 physical-return contradictions and 5,178 time cycles.
All 32 cases have no extension through H-5. Every time cycle retained here has
zero period coefficient, so the proof applies to either drift orientation and
every positive period. No finite period cutoff establishes this conclusion.

The full companion theorem presently has a finite certificate proof. The
following short hand argument explains some, but not all, of its rejections.
At a Q cell, suppose its kth east departure first returns to the same physical
cell as its first south arrival. The two visits must be consecutive. The
departure is NR and the return SL; that return is therefore also east
departure k+1. A return from the last east departure to the first south arrival
is impossible. More generally, prescribed subsequent returns cannot skip an
intermediate south arrival. Multicell constraints handle the other branches.

A singleton rail now consumes at least three wakes in its rail and the level
two steps inward. An adjacent or alternating two-lane rail consumes two rail
wakes and at least one nearby wake by the previous lemmas. A three-lane rail
already consumes three. The upper and lower boundary pairs are disjoint.
Consequently

\[
\#\{\text{wakes outside }L,L+2,H-2,H\}\le2.
\]

If both rails are singleton, their occupied lanes r above and s below must
satisfy \(s-r\in\{2,3\}\pmod4\), by the same two-per-x-residue budget.

#### 3. A further classification of ends with only three wakes

Suppose exactly three wakes occur on an upper end's first three horizontal
levels H,H-2,H-4. The preceding budget forces all three onto H,H-2, with no
wakes at H-4. Up to cyclic lane shifts, the possible (rail, inward) masks
before the next local checks are

\[
(1,3),\ (3,1),\ (3,2),\ (3,4),\ (3,8),\ (5,1),\ (7,0).
\]

Only **(3,8) and (7,0)** remain after the checked local exclusions. This
statement concerns any end with that three-wake budget, even when other wakes
occur farther inside the strip. The lower-end statement uses the half-turn
and the corresponding reversed lane order.

For boundary-only classification we also exclude (5,11), assuming no wakes
at H-4. The finite audit is:

| Rail mask | H-2 mask | Generated words | Checked rejection certificates | Complete extensions through H-5 |
|---:|---:|---:|---:|---:|
| 1 | 3 | 1,455 | 660 | 0 |
| 3 | 1 | 90 | 28 | 0 |
| 3 | 2 | 320 | 110 | 0 |
| 3 | 4 | 157 | 66 | 0 |
| 5 | 1 | 345 | 141 | 0 |
| 5 | 11 | 2,499 | 1,640 | 0 |

`verify_m4_boundary_classification.py` reruns all six cases with independently
reconstructed domains, checked rejection certificates, and no timeout.
All time contradictions used are independent of the drift sign. The actual
finite domains follow from count balance and nonnegativity, without a visit
count cutoff. Physical first-return constraints then eliminate word orders.

#### 4. The displayed width-ten placement is excluded

The September 6 note displayed the algebraically surviving placement

\[
D=\{(1,0),(1,1),(1,2),(7,3),(9,3),(11,0),(11,1),(11,2)\}.
\]

It still passes the degree, additive, and rank tests, but **it cannot be the
wake set of an admissible highway at any period**, using the established
project reductions. The proof reconstructs the two end bands and joins them
at the middle Q level t=6.

The lower band has 1,546 possible locally surviving words; the upper band has
32,066. Their port counts determine the middle count row, rather than leaving
an unbounded period search. At middle lane r, let X be the number of north
departures from lower C(5,r), Y the west arrivals at lower C(5,r-1), U the
south departures from upper C(7,r), and V the east arrivals at upper C(7,r+1).
The required equations are

\[
X+U=Y+V,\qquad a=\frac{2V+X-U}{4},\qquad
(NR,NL,SR,SL)=(a,X-a,U-V+a,V-a).
\]

Reject a row unless all four entries are nonnegative integers. Exact excursions
through each end impose consecutive departure/return ordinals at the middle
cells. There are 10,078,210 count-compatible full-band pairs. Testing their
9,822,702 distinct projected self-return pairs leaves exactly 171 full-band
pairs. Every surviving projection has one member, so no unchecked replacement
of a group by one representative is used in the final step.

The final join rejects all 171 pairs after 185 partial middle assignments:
174 physical-return contradictions and 11 time-cycle contradictions. The only
periods permitted by those surviving count rows are 224,240,256,272,288; these
are consequences of the enumeration, not an imposed search ceiling.

`verify_m4_two_ended.py` rebuilds the complete inputs, checks the local domains
independently, and checks each rejection certificate. It also tests a known
period-208 highway in both drift orientations. The lower band is generated
with **negative drift before half-turn**; using positive-drift pruning there
would be an invalid symmetry shortcut.

`verify_m4_interface.py` separately reconstructs all 33,610 excursion signatures
using physical coordinates and checks all 14,506 distinct middle-word domains
with a different generator. Its surviving set agrees exactly. Both audit
files report success. This excludes this one placement; it does not exclude
every width-ten placement or every pair of three-lane rails.

#### 5. Boundary-only wakes: an all-width algebraic reduction

Now assume every wake lies on L,L+2,H-2,H. Record their four masks in the order
\((B,B_I,U_I,U)\). Two wakes in each x-residue means choosing two of four
levels for each of four lanes: exactly \(6^4=1296\) raw patterns. The partial
rail and nearby-wake conditions reduce this to 466.

Use the project's pure-wake additive normal form: if a and b count the
t=1 modulo 4 wakes in each even and odd x lane, respectively, and
\(Z=\sum_{(t,r)\in D}\lfloor t/4\rfloor\), the additive condition is
\(Z\equiv a+b-1\pmod4\). The rank condition requires \(E+\Lambda=1\pmod2\).

##### Why sixteen-level padding preserves these algebraic conditions

Insert sixteen wake-free transverse levels into the gap between the two
boundary pairs, shifting the upper pair up by sixteen. Wake x/y residues are
unchanged. Each shifted wake increases its contribution to Z by four, so the
additive congruence is unchanged.

For completeness, consider the parity-flow masks used in the project's rank
formulas. In a wake-free gap the C-edge mask b is a constant B. The Q-edge
mask a alternates between A and its two-lane rotation \(P^2A\); its transverse
period is four. Sixteen inserted levels contain eight C and eight Q levels,
with the same phase at both ends. The original boundary transition terms are
therefore preserved.

The local correction on each Q level has parity \(|B|+|A|\). Eight copies
sum to zero; no new wake-C correction appears. For C-source edge inversions,
the unchanged-gap summand is

\[
\binom{|B|}{2}+|B|+\sum_{r<s}B_rB_s\equiv |B|\pmod2,
\]

so eight inserted copies also sum to zero. For Q-source terms, write

\[
F(A)=\binom{|A|}{2}+A_0(|A|-A_0)+A_3(|A|-A_3),
\]

\[
C(A,A')=\sum_{r,s}A_rA'_s
\mathbf1_{(r+1\bmod4)\ge(s-1\bmod4)}.
\]

The inserted contribution is four copies of
\(F(A)+C(A,P^2A)\) and four of
\(F(P^2A)+C(P^2A,A)\), hence zero modulo two.
Adjacent-source-level inversion terms cancel in pairs by the original rank
factorization. Thus E and Lambda are individually unchanged.

This proves algebraic periodicity in H modulo sixteen. Every H>=11 reduces
to one of 11,13,15,17,19,21,23,25 while keeping the boundary levels distinct.
The program checks all 256 gap parity states and also corroborates the padding
on 3,728 pattern/height combinations. Those finite checks supplement the
preceding argument. **Padding is not a rule for extending or shortening a P3
trace:** it does not preserve visit words, integer flows, or chronology.

##### Exact surviving patterns

After y-degree, additive, and rank conditions, the eight representative heights
have 4,0,20,4,4,0,20,4 patterns, respectively: 56 in total. The local exclusions
remove 40, leaving the following four rows and their cyclic lane translations.

| H modulo 16 | Least H>=11 | One mask tuple (B,BI,UI,U) | Canonical lower cap | Canonical upper cap |
|---:|---:|---|---|---|
| 15 | 15 | (7,12,8,3) | (7,9) | (3,8) |
| 1 | 17 | (13,0,10,7) | (7,0) | (7,10) |
| 7 | 23 | (3,4,12,11) | (3,8) | (7,9) |
| 9 | 25 | (13,10,0,7) | (7,10) | (7,0) |

For the lower cap, canonicalization includes reversing lane order under the
half-turn. Each row represents four translated masks, giving sixteen patterns.
They form two types of cap pairing, in the two listed orders. Keep the stated
height congruences: simply exchanging ends does not preserve the positive-drift
additive condition. Every survivor uses three wakes at one end and five at the
other. Boundary-only arrangements with four wakes at each end are excluded.

These are necessary patterns, not constructed highways. All four cap types
admit depth-five local words in both drift directions. A further depth-six
probe found local words for (3,8) with negative drift and (7,0) with positive
drift; the other six runs reached their 25-second budgets. None exhausted.
These probes add **no exclusion**. Even the surviving local words only satisfy
the recorded partial constraints; they do not establish global P3 realizability.

#### 6. Exact remaining task

The current cases are zero, one, or two wake classes outside L,L+2,H-2,H.
The zero case has been reduced to the table above but remains open. The one-
and two-interior-wake cases have not been classified completely. Both width
and period remain unbounded across the whole problem.

A concrete conceptual target is a theorem controlling continuation of the
three-wake cap types (3,8) and (7,0) through a wake-free strip, or a compatibility
obstruction between the paired ends. Excluding those two cap types at all
depths would close the boundary-only branch. It would still leave the cases
with interior wakes. Finite-depth timeouts and the sixteen-level algebraic
periodicity do not supply the missing theorem.

The progress is therefore a reduction in the shape of the unresolved problem,
not evidence for a promised completion time.

#### 7. Source and verification record

- The September 6 full-rail and alternating-half-rail notes are included in
  the accompanying archive, together with their original audits.
- The singleton proof and its hand lemma are documented in
  `singleton_conceptual_review.md`; the final orientation-independent audit is
  in `m4_singleton_companion_audit_2026-09-07.log`.
- The complete width-ten checks are
  `m4_two_ended_audit_2026-09-06.json` and
  `m4_interface_independent_audit_2026-09-06.json`.
- The new classification is in
  `m4_boundary_classification_audit_2026-09-07.json`.
- The source parity formulas are in the project's
  [September 4 partial-rail note](04_Growth_eight.md#source-research-notes-growth8-m4-partial-rail-obstruction-2026-09-04-md),
  and the pure-wake additive reduction is in the
  [additive normal-form note](04_Growth_eight.md#source-research-notes-growth8-m4-pure-additive-normal-form-2026-09-04-md).

See `README.md` in the archive for commands and the exact distinction between
the proof drivers and exploratory probes.

<a id="source-research-notes-rail-occupancy-scope-audit-2026-09-03-md"></a>

## rail_occupancy_scope_audit_2026-09-03

Source: `research-notes/rail_occupancy_scope_audit_2026-09-03.md`.

### Extremal singleton visits do not establish full rail occupancy

The claimed all-period exclusion of the whole `(4,-4)` growth-eight orbit
has an unproved premise. Its rank argument assumes that all four residue
lanes are visited on each extremal line. The extremal-line theorem proves
singleton status only for classes that are visited. It does not establish
that every lane is visited.

The same premise was used to put six wake classes on the two rails at
`(3,-3)`. The resulting `7+1` split and its sharpened period and separation
conditions are therefore conditional on full rail occupancy. They cannot
currently be applied to every candidate in that orbit.

This is a gap in the supplied proof, not a constructed P3 counterexample to
full occupancy. The extremal theorem and later rank arguments do not supply
the missing implication. The boundary audit programs impose the full rail
boundary as input.

#### The quantifiers

For drift `(m,-m)`, a transverse line has `m` translation classes. Let
`R_-` and `R_+` be the sets of lane labels actually visited on the lower
and upper extremal lines. The proven statement is

```text
1 <= |R_-| <= m,       1 <= |R_+| <= m,
each class in R_- or R_+ is a singleton odd class.
```

Thus the rails contribute `|R_-|+|R_+|` horizontal wake classes. Replacing
this number by `2m` requires the additional assertion
`R_-=R_+=Z/mZ`. When `m=1` this is automatic. When `m>1` it is not a
consequence of counting the available classes.

In particular, extremal rigidity and the wake-type parity law alone give

```text
alpha+beta=8,       alpha=beta=m (mod 2),       alpha>=2,
```

where `alpha` counts horizontal-arrival wake classes. For odd `m`, these
conditions leave `(alpha,beta)=(3,5),(5,3),(7,1)`. At `m=2` they leave
`(2,6),(4,4),(6,2),(8,0)` before the checker-pure exclusion removes the
last pair. At `m=4`, the coarse P22 table also restricts the vertical
count to `0,4,8`; since `alpha>=2`, the remaining splits are `(8,0)` and
`(4,4)`. Neither split has been removed in full by the rail argument.

#### A counterexample to the geometric inference alone

Start a quarter-turn walk at `(0,0)` with incoming S and take the directions

```text
E,S,W,N,E,N,E,S,W,S,E,S,W,N,E,S,E,S.
```

It ends at `(3,-3)` with incoming S. Its turn word is

```text
L,R,R,R,R,L,R,R,R,L,L,R,R,R,R,R,L,R,
```

so its turn excess is eight. Its lowest transverse level is `t=-1`, visited
at exactly `(0,-1)` and `(1,-2)`, both with port `WR`. Its highest level
is `t=3`, visited only at `(2,1)`, with port `ER`. Every visited extremal
class is a singleton right-turn class, but the lower rail occupies only
two of the three residue lanes and the upper rail only one.

This is not a legal Langton trace: `(1,0)` turns R at time one, then L
at time five and again at time nine. It shows precisely that the drift and turn balance,
together with the stated geometric extremal properties, do not imply full
rail occupancy. A proof using the remaining P3 chronology would still be
needed; the example does not disprove such a theorem.

#### What survives

The four-lane rank calculation still excludes the subfamily at `(4,-4)`
in which both rails are fully occupied. Under that hypothesis the eight
rail classes exhaust the wake, the parity flow is the stated full block
set, and the rank contradiction follows.

At `(3,-3)`, assuming both rails are full, the two remaining classes have
the stated horizontal/vertical types and coincident coordinate residues.
The moment `k=W+1 mod 4` and the bound `N>=4W+12|k|+2` retain that
hypothesis. The period condition `N=6 mod 8` holds whenever the split is
`7+1`, even without full rails; it is not the only period class justified
for the entire orbit. A split `5+3` instead gives `N=2 mod 8`.

The coarse ten-orbit residue ledger is unchanged. The axis-two return
lemmas do not use full diagonal rails. The primitive-diagonal statements
have only one lane per rail and are unaffected. The checker-pure
`(2,-2)` rank proof does not use full rail occupancy either.

The targeted finite-period search source uses the residue conditions and
the exact trace criterion, not the withdrawn full-rail inference. Its
existing finite-period records have not been rerun in this audit.

Consequently no whole growth-eight drift orbit is presently certified
closed by the arguments in the ledger. All ten retain unresolved cases;
the proved subfamily exclusions remain available.

#### Source and artifact correction

The affected arguments are qualified in the case notes and manuscript
sources, and the live summaries are corrected. Historical journal and
handoff entries retain a dated scope warning rather than silently erasing
the earlier claim. Existing rendered PDF and HTML files have not been
regenerated by this mathematical audit and must not be treated as corrected
releases. The source statements and this note take precedence.
