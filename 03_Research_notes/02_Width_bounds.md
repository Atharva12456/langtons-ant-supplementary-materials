# Width bounds and dated proof drafts

These notes retain their original dates and hypotheses. Later status
pointers distinguish superseded checkpoints from the current report.
Individual source files and linked records are preserved in
[research_notes_sources.zip](research_notes_sources.zip).

## Contents

- [transverse_mod4_theorem_draft](#source-research-notes-transverse-mod4-theorem-draft-md)
- [width4_crossing_splice_proof_draft](#source-research-notes-width4-crossing-splice-proof-draft-md)
- [width4_research_2026-07-21](#source-research-notes-width4-research-2026-07-21-md)
- [width6_research_2026-08-17](#source-research-notes-width6-research-2026-08-17-md)
- [width8_research_2026-08-17](#source-research-notes-width8-research-2026-08-17-md)

<a id="source-research-notes-transverse-mod4-theorem-draft-md"></a>

## transverse_mod4_theorem_draft

Source: `research-notes/transverse_mod4_theorem_draft.md`.

### Transverse mod-four level theorem — working draft (17–18 August 2026)

Historical draft, superseded by
[line_parity_research_2026-08-18.md](01_Foundations.md#source-research-notes-line-parity-research-2026-08-18-md).
The candidate status and unresolved checks below describe this earlier stage.

Status: **candidate theorem, under hostile audit.** Verified on the genuine
period-104 standard highway and by exhaustive check of every sub-lemma; the
sub-lemmas are elementary and analytic, so the claim is not a bounded search
result. Nothing here is promoted until the audit closes.

#### 0. Setting and normalisation

A *periodic highway* is a bi-infinite ant trace with `p_{i+N} = p_i + d` for a
fixed nonzero drift `d` and ant period `N`, arising as the asymptotic regime of
a finite-support start. Throughout, `d` is diagonal and normalised so that
`d = (m,-m)` with `m >= 1`; quarter-turn rotations cover the other
diagonal signs.

Set the **transverse level**

```text
t = x + y,
```

which is constant along `d`. Every ant move changes `t` by exactly `+-1`,
because a move changes exactly one of `x,y` by `+-1`.

Write `f_t` for the number of period moves crossing the cut `(t,t+1)` upward and
`m_{t,r}` for the number of period events in the translation class
`(t, x mod m)`. Put `m_t = sum_r m_{t,r}`, the number of period events at
level `t`.

#### 1. Three elementary sub-lemmas

**Lemma A (arrival axis is a function of level parity).**
Ant headings alternate between the horizontal and the vertical axis, because
every step turns by a quarter turn. Since `t` also changes parity at every
step, the axis of the move *arriving* at a cell is determined by the parity of
that cell's level. Normalise `t` so that **horizontal arrivals are exactly the
odd levels** (`C` levels); vertical arrivals are the even levels (`Q` levels).

*Exhaustively verified:* `sublemma_check.py`, all closed diagonal-drift
heading-reset words of every even length `<= 14`, 8,532 words, 0 failures.

**Lemma B (reflect/continue rule).**
With `t = x + y` and drift normalised so `d = (m,-m)`:

```text
odd  level (horizontal arrival, vertical departure):  R  <=>  t reverses,
even level (vertical arrival, horizontal departure):  R  <=>  t continues.
```

*Proof.* At an odd level the incoming heading is `E` or `W` and the outgoing is
`N` or `S`. Incoming `E` means `x` rose, so `t` rose; outgoing `S` means `y`
fell, so `t` fell. The right turn from `E` is `S`, so `R` reverses the sense of
`t`; the right turn from `W` is `N`, likewise a reversal. At an even level the
incoming heading is `N` or `S` and the outgoing is `E` or `W`; the right turn
from `N` is `E`, and both raise `t`, so `R` continues; the right turn from `S`
is `W`, and both lower `t`. []

*Exhaustively verified:* 114,520 individual step checks, 0 failures.
(The rule flips if one uses `t = x - y` for a drift with `ab > 0`; the
normalisation above is the one that makes the stated form correct.)

**Lemma C (flow at a level).**
Let `M_t` be the number of period events at level `t` that are local maxima of
`t` (arrive from below, leave downward) and `n_t` the number of local minima.
The quotient level walk is closed, so each cut is crossed equally often in both
directions, and counting the four incoming/outgoing combinations at level `t`
gives

```text
m_t = f_{t-1} + f_t,        M_t - n_t = f_{t-1} - f_t.
```

Hence the number of **reflections** at level `t`,

```text
rho_t := M_t + n_t,
```

satisfies `rho_t = M_t - n_t = f_{t-1} - f_t = f_{t-1} + f_t = m_t  (mod 2)`.

*Exhaustively verified:* 39,688 level checks, 0 failures.

#### 2. The theorem

**Theorem (transverse mod-four level theorem).**
For a periodic highway with diagonal drift `d = (m,-m)`, at every transverse
level `t`,

```text
sum_r ceil (m_{t,r}/2) = m_t  (mod 2)     if t is odd,
sum_r floor(m_{t,r}/2) = m_t  (mod 2)     if t is even.
```

*Proof.* Because the translation class of a cell is `(t, x mod m)`, every cell
of the class `(t,r)` is visited exactly `m_{t,r}` times over all time: the
period events of that class are `(i_k, x_k)`, `k = 1..m_{t,r}`, and the visits
to the cell of the class with longitudinal coordinate `X` occur at the
`m_{t,r}` distinct times `i_k + ((X - x_k)/m) N`. Each such cell is white
before the highway reaches it, so its turns read `R,L,R,L,...` in time order,
giving `ceil(m_{t,r}/2)` right turns and `floor(m_{t,r}/2)` left turns. The
period events of the class are in bijection with the visits to any one of its
cells, so the class contributes exactly `ceil(m_{t,r}/2)` right turns to the
period.

By Lemma B the reflections at an odd level are exactly its right turns and at
an even level exactly its left turns, so

```text
rho_t = sum_r ceil (m_{t,r}/2)   (t odd),
rho_t = sum_r floor(m_{t,r}/2)   (t even).
```

Lemma C gives `rho_t = m_t (mod 2)`. []

**Corollary (primitive diagonal).** For `d = (1,-1)` there is one class per
level, so `m_t = m_{t,0}` and the theorem reads

```text
t odd  :  m_t = 0 or 1  (mod 4),
t even :  m_t = 0 or 3  (mod 4).
```

Equivalently, **every level of even multiplicity has `m_t = 0 (mod 4)`**, every
odd level of odd multiplicity has `m_t = 1 (mod 4)`, and every even level of
odd multiplicity has `m_t = 3 (mod 4)`. In particular no even level has
`m_t in {1,2}`, and no odd level has `m_t in {2,3}`.

#### 3. Immediate consequences at primitive-diagonal growth four

Let `d = (1,-1)`, `g = 4`. The odd-multiplicity levels are exactly the `g = 4`
translation classes of the settled wake, so there are four of them. Write the
occupied levels as `T_0 .. T_1` and `W = T_1 - T_0`.

1. Every level with `T_0 < t < T_1` outside the four wake levels has
   `m_t = 0 (mod 4)`, hence `m_t >= 4`.
2. Every even level has `m_t >= 3` (it is `3 (mod 4)` if a wake level and
   `0 (mod 4)` otherwise).
3. `N = sum_t m_t = 3 . 1 + 1 . 3 = 6 = 2 (mod 4)` using the residue-theorem
   split of the four wake levels (three at odd `t`, one at even `t`; see §4).
4. `sum_{t odd} m_t = N/2` counts horizontal arrivals, and is `3 (mod 4)`,
   so `N = 6 (mod 8)`.
5. `f_t` is **never** `0 (mod 4)`: writing `c_t` for the number of wake levels
   `<= t`, one gets `f_t = (-1)^{t-T_0} c_t (mod 4)` with `c_t in {1,2,3}` on
   the occupied cuts.
6. Non-negativity of `M_t, n_t` forces `|f_{t-1} - f_t| <= rho_t`, i.e. roughly
   `max <= 3 min` on adjacent cuts. With the proved extremal theorem
   (`m_{T_0} = m_{T_1} = 1`, so `f_{T_0} = f_{T_1-1} = 1`) this pins the two
   cuts next to each boundary: `f_{T_0+1}, f_{T_1-2} in {2,3}`, hence
   `m_{T_0+1}, m_{T_1-1} in {3,4}`. Since only one even level may be a wake
   level, at most one of `m_{T_0+1}, m_{T_1-1}` equals 3.

#### 4. What is still assumed, and what is open

- §3 items 3–4 use the signed mod-four wake-residue theorem in the form "the
  four wake levels split 3–1 by checker parity". For primitive diagonal the
  checker parity of a cell is exactly `t mod 2`, so the signed sum over the
  four wake levels is `+-2`, which forces a 3–1 split. **This step must be
  re-derived directly from the paper's Theorem 7.1 rather than assumed.**
- The proved transverse rigidity theorem is used for `m_{T_0} = m_{T_1} = 1`
  and for `T_0, T_1` both being horizontal-arrival (odd) levels, hence `W`
  even. Its applicability to `m = 1` drift must be confirmed against §9.
- **Open:** the constraint system of §3 is finite for each `W` but `W` is
  unbounded, so this is not yet an exclusion of primitive-diagonal growth
  four. A `W`-uniform argument, or an upper bound on `W`, is the missing step.

#### 5. Reproduction

```text
scratchpad/lang/reflection_parity_check.py   # all identities on the real period-104 highway
scratchpad/lang/sublemma_check.py 14         # exhaustive sub-lemma verification
```

<a id="source-research-notes-width4-crossing-splice-proof-draft-md"></a>

## width4_crossing_splice_proof_draft

Source: `research-notes/width4_crossing_splice_proof_draft.md`.

### Width-four crossing-sequence splice: proof draft

**Date:** 21 July 2026  
**Status (updated after release audit):** This draft has two distinct results, at
different maturity levels — do not conflate them.
- The **all-white blank-column crossing graph is acyclic** (Section 9 here) was
  **promoted** after the correction recorded in Journal §38.16: it is
  the blank-column classification lemma and the no-width-four-highway theorem
  in `paper/main.tex`, computer-assisted with a Lean-checked rank
  consequence. Where this draft still says "candidate" about that acyclicity claim,
  read it as superseded by the promoted theorem.
- The **m<=70 splice / pumping cutoff** (the draft's primary subject) remains a
  **candidate** decidability route and is NOT claimed in the paper. Its Lean endpoints
  are named `drift_le_candidate_*_cutoff` precisely to mark them as unproven kernels.
**Purpose:** reduce all width-four periodic highways to a finite drift range

#### 1. Macro trace and notation

Normalize the drift to `(m,-m)`, `m>0`, and use transverse lines `0,...,4`.
A width-four trace has a macro presentation

```
(s_i, ell_i) --tau_i--> (s_(i+1), ell_(i+1)),   0<=i<P,
```

where `s_i` is one of `LN,LS,UN,US`, every `tau_i` is one of the twelve transitions
in `WidthFourSearch`, and `ell_(i+1)-ell_i` is `+1` or `-1`. After a cyclic phase
choice, `(s_0,ell_0)=(LN,0)` and `(s_P,ell_P)=(LN,m)`. The ant period is `2P`.

Each transition crosses exactly one longitudinal cut. It also turns one odd-line
cell in its source column and one even-line cell in its target column. Thus a
transition type specifies:

- source and target macro states;
- crossing direction;
- the two transverse endpoint lines; and
- the two turn symbols.

There are six transition types in each direction.

#### 2. Infinite lift and the correct cut order

Extend the geometric macro path formally by translation: period `n` uses phase `i` at
`ell_i+nm` and global macro time `i+nP`. This is a continuous bi-infinite geometric
path. Finite-seed realizability is imposed only in forward time, so the proof must
not use a formal negative-period turn as though it were an executed ant step.

For cut residue `r in {0,...,m-1}`, a phase-`i` transition may cross the lifted cut

```
r + qm + 1/2.
```

Translate that event by `-q` periods to the representative cut `r+1/2`. Its global
time there is

```
kappa = i - Pq.
```

The decorated crossing signature `Sigma_r` is the list of transition types crossing
the cut orbit `r mod m`, sorted by `kappa`. Raw phase order is wrong when the trace
overshoots the fundamental interval.

Its **control projection** `Gamma_r` retains only the crossing direction and the
even transverse line on which the ant lands.

Because the lifted path crosses a fixed representative cut continuously, directions
in `Sigma_r` alternate and begin and end with `+`. Hence `|Sigma_r|` is positive odd.
Every macro phase crosses one cut orbit, so

```
sum_r |Sigma_r| = P.
```

To realise this signature in the genuine forward orbit, choose `Q` larger than every
lift index `q` appearing in the one-period trace. At the far-ahead physical cut
`r+Qm+1/2`, the same event occurs in period `Q-q` at actual time

```
QP + (i-Pq) >= 0.
```

Thus `Sigma_r` is the actual chronological crossing sequence at every sufficiently
far representative cut, shifted by a constant time. No backward extension of the
finite-seed dynamics is used.

Also choose the splice start beyond the finite seed and with a backtracking margin.
The one-period set `{ell_i}` has a finite minimum, so after a sufficiently large
period index the forward trace never returns to the uncompressed prefix. The tail
surgery can therefore be separated from the untouched finite prefix by a cut which
is crossed for the last time before surgery begins.

#### 3. Density of short signatures

The proved width-four bound is `P<=7m`. Let `L` be the number of residues whose
signature length is at most seven. Non-short signatures have positive odd length at
least nine. Therefore

```
7m >= P >= L + 9(m-L) = 9m-8L,
```

so `m<=4L`. The final arithmetic implication is theorem
`many_low_crossing_cuts` in `lean/Langton/WidthFour.lean`.

#### 4. Candidate splice lemma

##### Statement

If `Gamma_r=Gamma_s` for two distinct cut residues, a P3-valid width-four trace can
be replaced by a P3-valid trace of strictly smaller positive drift and transverse
width at most four.

##### Direct one-tape encoding

There is a useful way to avoid treating a two-turn macro transition as an atomic
black box.  Regard the longitudinal coordinate `ell=x` as a one-dimensional tape
coordinate.  One tape symbol is the five-bit colour vector of the cells on
transverse lines `0,...,4` in that column.  The finite control stores the transverse
line, compass heading, and (if a conventional Turing-machine model without a
stay-put move is desired) one auxiliary phase bit.  A vertical ant move is a
stay-put tape move and a horizontal ant move crosses one tape boundary.  This is a
deterministic one-tape machine with alphabet of size at most `2^5` and finite
control.  A finite black ant seed is a finite nonblank tape.

For a tape boundary `u+1/2`, record immediately after each crossing the crossing
direction and finite-control state.  Call this the **control crossing sequence**.
The decorated macro type used in `Sigma_r` determines this datum: it specifies the
source and target odd-track states, direction, even endpoint line, and both turns.
In fact `Gamma_r` is exactly the control crossing sequence.  The direction is the
horizontal heading `E` or `W`. A rightward move lands on line `2` or `4`, and a
leftward move on line `0` or `2`; these are all the finite-control data immediately
after the crossing. Equality of `Gamma`
therefore suffices.  The decorated alphabet is a strict over-refinement.

The ordinary crossing-sequence splice lemma now applies without an extra assumption
about endpoint colours.  If two boundaries of one deterministic computation have
the same control crossing sequence, keep the initial tape to the left of the first
boundary and to the right of the second, delete the intervening cells, and glue.
Between successive crossings the new computation copies the appropriate old
half-tape computation.  At the next boundary crossing the equal control state lets
it switch halves.  Induction on the crossing number proves that every read, write,
turn, and move is legal.  This is the precise content needed here from the classical
one-tape crossing-sequence lemma.

Equivalently, form the classical crossing-sequence graph.  A vertex is a finite
control crossing sequence; the column between two consecutive boundaries is an
edge labelled by its initial five-bit tape symbol, and the two endpoint sequences
are compatible exactly when the deterministic local column history exists.  Far
ahead of the finite seed every edge label is the all-white symbol.  The old
width-four highway supplies a spatially periodic closed walk of length `m` in this
graph, with vertex at cut residue `r` equal to `Gamma_r`.  If
`Gamma_r=Gamma_s`, the portion between the two equal vertices is a closed subwalk;
deleting it leaves a closed walk of length `m-(s-r)`.  This graph picture is the
finite combinatorial core of the simultaneous splice below.

##### Periodic spatial deletion

Orient the residue circle so `0<=r<s<m`, put `Delta=s-r`, and set `m'=m-Delta`.
Choose the far-ahead `Q` above. For every integer `q>=Q`, delete the slab of
longitudinal columns strictly between the
lifted cuts

```
r+qm+1/2  and  s+qm+1/2.
```

Let `S` be the remaining columns. The order-preserving compression `phi:S->Z`
satisfies

```
phi(ell+m)=phi(ell)+m'.
```

Choose `Q` so far ahead that the original finite seed lies wholly to the left of
the first deletion.  The compressed initial tape therefore still has finite
nonblank support: the operation deletes infinitely many columns, but every deleted
or shifted far-tail column is initially blank.

The infinitely many splices are defined by a finite-time direct limit.  Up to any
fixed time, a one-head computation visits only finitely many columns, so only
finitely many deleted slabs can affect that prefix.  Apply the ordinary splice
lemma to those finitely many disjoint slabs.  Increasing the finite set cannot
change the already constructed prefix, by determinism and locality.  The compatible
prefixes therefore define one infinite legal computation on the compressed finite
seed.  This is stronger and cleaner than postulating an infinite pre-existing wake.

There is also a monotonicity proof ruling out truncation at infinity.  For cuts
`A<B`, the matching rightward crossing occurs at `A` before it occurs at `B`, while
the matching leftward crossing occurs at `B` before it occurs at `A`.  Each splice
therefore jumps forward in the old chronological execution and deletes an interval;
it never inserts, duplicates, or reverses events.  After adding the `(K+1)`-st
farther splice, the retained event list is a subsequence of the `K`-splice event
list.  The index of any fixed retained crossing occurrence is consequently a
nonincreasing natural number and eventually stabilises.  Every prescribed occurrence
exists in every finite splice by the one-cut lemma, so none can disappear only in
the limit.  Conversely, any alleged extra limit crossing would occur at a finite
event index and hence already occur in a sufficiently large finite splice.  Thus the
limit has exactly the stated crossing sequences.

##### Equivalent macro description

At each deleted slab, pair its left- and right-boundary crossings in the order given
by the stabilised control signatures. The directions alternate, so a rightward entrance is
paired with the corresponding rightward exit, and similarly in the reverse
direction.

The literal one-tape proof switches half-computations immediately after the
horizontal crossing and uses only equality of destination line and direction.  It
then reads the retained destination-column symbol and continues by the actual ant
rule. Regrouping this legal ant computation into pairs recovers transitions in the
twelve-entry macro table.

When the stronger decorated signatures agree, there is also a direct macro
visualisation: equality gives the same source/target state and the same odd/even
endpoint lines and turns, so one may replace the two boundary events and intervening
slab segment by one transition across the glued boundary.

- On a rightward splice, retain the odd-cell turn from the old left event and the
  even-cell turn from the old right event.
- On a leftward splice, retain the odd-cell turn from the old right event and the
  even-cell turn from the old left event.

Under that stronger equality the combined pair is exactly the common legal macro
transition type. This paragraph is only a visualisation; legality for the weaker
control-signature hypothesis comes from the one-tape induction, not from equality
of the turn pairs.

This is exactly the one-tape splice above, expressed in the two-turn macro language.
The one-tape encoding supplies the formal intermediate states and removes any need
to assume that an atomic two-cell update can simply be split.

##### Eventual periodicity and the new drift

Beyond the untouched finite prefix, both the original executed history and the
family of deleted slabs are invariant under translation by one old period:

```
(time, ell) -> (time+2P, ell+m).
```

After compression the same spatial symmetry is `ell -> ell+m'`.  The direct-limit
splice is equivariant under this symmetry.  More explicitly, translate each retained
local column transcript and its ordered boundary-crossing occurrences by one new
closed-walk cycle.  Compatibility identifies the same local read/write transcript,
and the `j`-th occurrence at a boundary maps to the `j`-th occurrence at its
translate.  This defines a successor-preserving self-map of the oriented tail event
path.  A successor-preserving self-map of a one-way discrete path has the form
`n -> n+k`; here `k` is finite, and it is positive because the map changes the
longitudinal coordinate by `m'>0`.  Write `k=2P'` (it is even because the translated
state returns to the same odd-track macro phase).  Hence the symmetry maps the event
path to itself forward by a fixed positive finite number `2P'` of ant events.
Starting at a tail event after the first deletion gives a repeating finite word
whose heading/control state resets and whose displacement is `(m',-m')`.

The positivity and finiteness of `P'` can also be seen at one retained cut: its
control crossing sequence is nonempty and has net one rightward crossing.  Between
that cut and its translate by `m'` the spliced head executes a finite nonempty
segment, and equivariance repeats that segment.

#### 5. Preservation of local turns and P3

Every physical cell outside the deleted slabs maps to one compressed cell.  In the
one-tape proof, a retained column is always run by one of the two original half-tape
computations.  Induction on successive boundary crossings shows that its reads and
writes occur in exactly their old order.  Thus each retained ant cell has exactly
its old chronological turn word, including the two cells adjacent to a glued
boundary.  This establishes, rather than assumes, the boundary-history assertion in
the macro description.

On the periodic tail, the compression respects translation. Retained residues modulo `m` map
bijectively to residues modulo `m'`; explicitly, for retained cells,

```
ell_2 = ell_1 (mod m)  iff  phi(ell_2)=phi(ell_1) (mod m').
```

Since `phi` is increasing, it preserves the front-to-back order of physical-cell
blocks in every translation class. Thus the stabilized word of every new class is
identical to the stabilized word of its old retained class. P3 start-`R` and
alternation are preserved.

The direct-limit construction already supplies a finite seed.  Equivalently, apply
the exact periodic-trace criterion directly to the extracted tail word: the class
words above are unchanged, so P3 holds and the criterion constructs a fresh finite
seed without an infinite black background.  The trace is nonempty and has nonzero
diagonal drift.  Its transverse width is even and at most four; nonzero diagonal
motion cannot have width zero, and width two has already been excluded.  Hence the
result is again width four.

#### 6. Explicit candidate cutoff

Choose a hypothetical width-four highway with minimal drift `m`. By the splice
lemma, all `Gamma_r` are distinct. A short signature has odd length `1,3,5`, or `7`.
At every event its direction is fixed by alternation, and the destination even line
has two geometrically possible values. Therefore the number of short control signatures is at most

```
F = 2 + 2^3 + 2^5 + 2^7 = 170.
```

Since `L<=F` and `m<=4L`,

```
m <= 680.
```

The full average-length budget improves this.  Let `n_k` count signatures of length
`k` for `k=1,3,5,7`, and let `n_+` count the remaining signatures, each of length at
least nine. Distinctness gives

```
n_1<=2,  n_3<=8,  n_5<=32,  n_7<=128.
```

Relative to average length seven, the maximum deficit supplied by the short
signatures is

```
6*2 + 4*8 + 2*32 = 108.
```

Every long signature costs at least two units above seven, so `n_+<=54`. Hence the
stronger, counting-optimal bound is

```
m <= 2+8+32+128+54 = 224.
```

Extremal singleton rigidity improves the signature capacities. In a signature of
length `2n+1`, there are `n+1` rightward slots and `n` leftward slots. The exceptional
rightward landing on top line `4` can occur at most once: two such phases would lie
in the same top extremal translation class. Likewise the exceptional leftward
landing on bottom line `0` can occur at most once. All other landings are on line
`2`. Hence the number of signatures is at most

```
(n+2)(n+1),
```

the product of the choice of no top event or one of `n+1` slots and the choice of no
bottom event or one of `n` slots. At lengths `1,3,5,7` the capacities are therefore
`2,6,12,20`. Their maximum deficit below average length seven is

```
6*2 + 4*6 + 2*12 = 60.
```

Thus there are at most 30 signatures of length at least nine, and the strongest
present counting bound is

```
m <= 2+6+12+20+30 = 70.
```

For each fixed `m`, `P<=7m` makes exact word enumeration finite. The candidate splice
lemma would therefore prove that width-four existence is decidable by a finite
search. It does not prove that no width-four highway exists.

The cutoff arithmetic is checked by
`drift_le_candidate_extremal_control_cutoff` in Lean. The cruder bounds `224`, `680`
and the older decorated `1151736` remain valid but are superseded. The splice itself
is not formalized.

#### 7. Evidence and sources

`code/python/width4_crossing_signatures.py` implements the stabilized key, both
signature projections, and checks that modular signatures partition all macro phases and alternate directions. On the
explicit endpoint near-model with `m=10`, cut residues `3,...,9` have identical
five-event signatures `d(+),c(-),b(+),h(-),d(+)`; deleting a slab removes one repeated
five-transition block and yields the `m-1` family.

The classical information-exchange statement appears in Emmanuel Jeandel,
*Computability of the entropy of one-tape Turing machines*, STACS 2014, Section 3.3,
following F. C. Hennie's crossing-sequence method. Jeandel states that equal crossing
sequences allow the tape to be cut at one boundary and pasted to the shifted tape at
another while preserving the machine's behavior.

#### 8. Adversarial audit checklist

The candidate splice argument must establish each of these points:

1. Does the `i-Pq` order exactly equal chronological order at a representative cut
   in the translated lift?
2. Does equal decorated signature pair entrances/exits of every periodically deleted
   slab without a lift-index mismatch?
3. Can the two-cell macro update always be represented by the claimed boundary
   splice, or is an additional tape symbol/state needed in the signature? Proposed
   discharge: use the explicit five-bit-column one-tape encoding above; decorated
   macro equality over-refines the ordinary control crossing sequence.
4. Is every retained cell's turn history unchanged, including the two cells adjacent
   to a glued boundary?
5. Is the translation-class bijection modulo `m` versus modulo `m'` exact?
6. Does finite-support realizability survive periodic compression without importing
   an infinite black background? Proposed discharge: start all deletions beyond the
   finite seed, define the simultaneous splices as a finite-time direct limit, and
   independently apply the exact criterion to the extracted tail word.
7. Is positive growth guaranteed after a splice that deletes all visits to an old
   extreme line?
8. Does cyclic choice of time zero preserve the based macro assumptions used by the
   width-four reduction?

Until all eight are discharged, `70` is a candidate cutoff, not a theorem of
the paper.

#### 9. Stronger candidate: the all-white crossing graph is acyclic

The pumping argument led to a direct local classifier which, if its finite
enumeration survives audit, excludes width four completely and makes the cutoff
unnecessary.

Choose a longitudinal column beyond the finite initial seed. Its five strip cells
are initially white. Let `u` and `v` be the control crossing sequences at its left
and right boundaries. Directions are implicit: positions `0,2,...` are rightward
and `1,3,...` leftward. Store only the destination even line. Extremal singleton
rigidity gives at most one `4` in a rightward slot and at most one `0` in a leftward
slot of each boundary sequence.

The column compatibility test is deterministic. Start with the first left-boundary
entry, toggle the indicated cell, turn, and follow vertical moves within the column
until the next horizontal exit. Match that exit against the next event of the
appropriate boundary sequence. If the head returns, consume the next entry event
from the same boundary and continue. The column has only five colour bits. Tracking
those bits, the current entry state, and the four flags recording whether each
boundary has already used its exceptional top/bottom event gives a finite exhaustive
recursion.

Writing a sequence by concatenating its line numbers, the complete list of
all-white compatible directed edges is

```
202       -> 4
4220222   -> 2, 202, 20222, 2022224
2042222   -> 2, 202, 20222, 2022224
202242222 -> 422, 42202, 4220222.
```

There are exactly 12 edges on 10 occurring vertices. The graph is acyclic; its
longest directed path is

```
202242222 -> 4220222 -> 202 -> 4,
```

of length three.

Any finite-support width-four highway has infinitely many initially white columns
ahead of its seed. Every adjacent pair of their exact boundary crossing sequences
must be one of the twelve edges above, producing an infinite directed path in this
finite graph. No such path exists. Therefore the finite table implies:

> **Candidate theorem.** No finite-support periodic Langton highway has transverse
> width four.

`code/python/width4_crossing_graph.py` independently obtains the table in two ways:
pairwise checking of all extremal signatures through length 25, and an unbounded
finite-state generator. The pairwise and generated edge sets agree. It then checks
graph acyclicity and longest path three. The unbounded generator reaches 22 entry
states, has maximum entry depth eight, and
finds no reachable entry cycle. Source SHA-256:
`2AF99EDCBC355945B547AB1F80CAEE6927FA75D6C1C064C5ADC41D13B5FE3E33`.

The key audit obligations are: the crossing state must really be only direction and
destination line; the local simulator's turn convention and left/right event
indices must match the ant; the four exceptional-event flags must exactly encode
extremal singleton rigidity; and the unbounded recursion must treat repeated states
soundly. Until those are checked independently (preferably also formalised), this
remains a candidate theorem rather than a manuscript result.

`lean/Langton/WidthFourCrossing.lean` separately records the twelve-edge table and
proves that every edge lowers the displayed rank, hence no four-edge chain exists.
Its SHA-256 is `548DF94E2B8B60CE23269153EE446CFF824AC1DB6AA1A41773F4E605205324FF`.
This formalises graph acyclicity, not exhaustiveness of the Python local classifier.

`code/python/verify_width4_crossing_graph_indep.py` is a separately written literal
verifier using compass-letter headings and a set of black rows; it imports none of
the search or crossing-graph code and reproduces the same 12 edges. SHA-256:
`694C1178B00FA8AB929A5375255E53762C403DE02FC1D2958A4409EF9B84AFE0`.
As a convention check, it also simulates the documented finite seed of the genuine
standard highway, extracts crossing sequences at far cuts 100 and 101, and exactly
replays the intervening initially white column (sequence lengths 31 and 21).

#### 10. Current self-audit status (18:23 CDT)

The direct one-tape encoding discharges the earlier ambiguity about splitting a
two-cell macro update and gives a local proof of finite-support preservation.  The
crossing-sequence graph and the successor-preserving event-path argument now give an
explicit proof of the equivariance step.  The chronological-subsequence monotonicity
argument rules out truncation or creation of crossings at the infinite-limit stage.
All eight listed issues now have proposed discharges in this draft, but no manuscript
claim should depend on the lemma until those proposed discharges constitute a
complete proof.

<a id="source-research-notes-width4-research-2026-07-21-md"></a>

## width4_research_2026-07-21

Source: `research-notes/width4_research_2026-07-21.md`.

### Width-four research log - 21 July 2026

#### Scope and status

**Current status after the post-cutoff audit.**  The direct blank-column result in
this log was promoted to a computer-assisted theorem: no diagonal finite-support
periodic highway has transverse width four.  Two independent exact enumerators
certify the complete 12-edge local graph, and Lean checks its rank consequence.
Journal \S38.16 records the label-hypothesis repair and the exact
formalisation boundary.  The time-stamped prose below preserves the discovery process
and therefore sometimes says ``candidate'' or ``not yet proved.''

This session follows the classification-side route, not the universal entrance
route.  The extremal-line theorem and the period-unbounded exclusion of transverse
width two were taken as established inputs.  The initial target was the next case,
transverse width four; at the beginning of the interval no all-period width-four
exclusion had yet been proved.

The manuscript is deliberately not being edited during the 90-minute research
interval.  This file records derivations and bounded experiments that may later be
promoted only after audit.

#### Normalised geometry

Normalise a diagonal drift to

\[
d=(m,-m),\qquad m>0,\qquad t(x,y)=x+y,
\]

and shift the transverse range to the five lines `0,1,2,3,4`.  Lines 0, 2, and 4
have horizontal arrivals; lines 1 and 3 have vertical arrivals.  Extremal rigidity
makes every visited cell on lines 0 and 4 a once-used `R` cell.

Use the longitudinal coordinate `ell=x`.  Observe the ant only when it is on one of
the odd lines.  There are four states:

- `LN`: lower track, arrival north;
- `LS`: lower track, arrival south;
- `UN`: upper track, arrival north;
- `US`: upper track, arrival south.

Every macro move contains two ant turns, first at an odd-line cell and then at an
even-line cell.  Direct evaluation of the turn rule gives the complete transition
table:

| state | next state | delta ell | turns | even line |
|---|---|---:|---|---:|
| LN | LS | +1 | RR | 2 |
| LN | UN | +1 | RL | 2 |
| LN | LN | -1 | LR | 0 |
| LS | LN | -1 | RR | 0 |
| LS | LS | +1 | LR | 2 |
| LS | UN | +1 | LL | 2 |
| UN | US | +1 | RR | 4 |
| UN | UN | -1 | LR | 2 |
| UN | LS | -1 | LL | 2 |
| US | UN | -1 | RR | 2 |
| US | LS | -1 | RL | 2 |
| US | US | +1 | LR | 4 |

Completeness of the based reduction: choose any bottom-extremal visit and cyclically
start immediately after it.  Its forced `R` turn leaves the bottom line heading
north, so the new initial state is `LN`.  After one trace period the state is again
`LN`, translated by `m`; a top-line transition must occur because the width is four.
Conversely, every such closed macro path expands uniquely to a turn word in the
five-line strip.  No cyclic-minimum normalisation is used, so choosing the bottom
visit does not discard positive-growth cycles.

#### A general width-growth sandwich

The residue theorem and extremal parity combine to give a useful all-period bound
that is not special to width four.

**Theorem (diagonal width-growth sandwich).** Let a finite-support periodic highway
have diagonal drift `d=(m,-m)` after normalisation, with `m>0`, growth `g`, and
transverse width `W`.  Then

\[
W\text{ is even},\qquad 2m\le g\le mW.
\]

**Proof.** Translation classes have the complete labels `(t,x mod m)`.  For a fixed
`x`-residue there is therefore at most one odd class on each of the `W+1` transverse
levels.  The signed residue identity says that the number of odd classes in that
fiber is positive and even.  Extremal rigidity says `W` is even, so `W+1` is odd and
the largest possible even fiber size is `W`.  Summing the upper bound over all `m`
residues gives `g<=mW`, because growth is the number of odd classes.  The lower bound
`g>=2m` is the strand-density bound.  QED.

Equivalently, every such highway satisfies `W>=g/m`, rounded upward to the next even
integer.  For the standard highway `(m,g,W)=(2,12,10)`, this alone gives only
`W>=6`; it is a genuine constraint but not a uniqueness argument.

#### The six-mask odd-skeleton theorem

For `j in {0,1,2,3,4}` and `r in Z/mZ`, let

\[
o_{j,r}=1
\]

exactly when the translation class on level `t=j` with `x=r (mod m)` has odd
stabilised length.  The pair `(t, x mod m)` is a complete translation-class label:
equal labels imply that the coordinate difference is `(km,-km)=k d`.

**Theorem (six-mask constraint).** For every longitudinal residue `r`, the set

\[
M_r=\{j:o_{j,r}=1\}
\]

is one of

\[
\{0,2\},\ \{1,3\},\ \{0,4\},\ \{2,4\},\
\{0,1,2,4\},\ \{0,2,3,4\}.
\]

For every `y`-residue `s`, the diagonal set

\[
D_s=\{j:o_{j,j-s}=1\}
\]

belongs to the same list.

**Proof.** One odd class supplies one wake-strand base.  Checkerboard sign is
`(-1)^j` on level `j`.  The signed mod-four wake-residue theorem, applied to the
`x`-residue `r`, gives

\[
o_{0,r}-o_{1,r}+o_{2,r}-o_{3,r}+o_{4,r}=2\pmod 4.
\]

There are only five binary variables.  Exhausting their values gives exactly the six
sets displayed above: the three positive two-subsets `{0,2}`, `{0,4}`, `{2,4}`;
the negative two-subset `{1,3}`; and the two four-subsets obtained by deleting level
3 or level 1 from `{0,1,2,3,4}`.  For a fixed `y`-residue `s`, the class `(j,r)` has
`y=j-r=s (mod m)`, hence `r=j-s`; the `y`-residue identity gives the same calculation
for `D_s`.  QED.

**Consequences.** If `h` longitudinal residues use a four-element mask, then

\[
g=2m+2h,\qquad 0\le h\le m,
\]

so

\[
2m\le g\le4m,\qquad h\equiv m\pmod2
\]

because `g` is a positive multiple of four.  Both extreme levels occur at least
once.  By extremal rigidity, every odd class on levels 0 and 4 is represented by one
phase and every visited extremal class is odd.

This is an all-period structural theorem, but it does not exclude width four.  Many
binary cylinders satisfy both six-mask rules.  The exact counts for circumference
`m=1,...,8`, before imposing chronology, are `6,14,30,70,146,302,650,1422`; hence
residue incidence alone leaves a large family of countermodels.

#### Exact macro search

`code/python/search_width4.py` enumerates the complete based macro table, enforces
same-physical-cell alternation during the depth-first search, and applies the full
translation-class criterion at every structural leaf.  Its fast leaf checker uses
the exact class key `(t,x mod m)` and chronological key `i-N*((x-r)/m)`.  It was
cross-checked against the general criterion on the standard period-104 word, its
square, and all 791 positive-normalised diagonal heading-reset words through length
14; there were zero disagreements.

Current completed zero-hit rows:

| macro period | ant period | nodes | structural leaves | P3 hits |
|---:|---:|---:|---:|---:|
| 20 | 40 | 315,115 | 18,884 | 0 |
| 21 | 42 | 547,153 | 32,827 | 0 |
| 22 | 44 | 923,385 | 57,003 | 0 |
| 23 | 46 | 1,599,297 | 98,995 | 0 |
| 24 | 48 | 2,715,756 | 171,745 | 0 |
| 25 | 50 | 4,694,674 | 297,730 | 0 |
| 26 | 52 | 8,005,882 | 515,706 | 0 |
| 27 | 54 | 13,821,690 | 892,915 | 0 |
| 28 | 56 | 23,641,165 | 1,545,598 | 0 |
| 29 | 58 | 40,779,962 | 2,674,711 | 0 |
| 30 | 60 | 69,894,284 | 4,626,994 | 0 |
| 31 | 62 | 120,486,560 | 8,001,133 | 0 |
| 32 | 64 | 206,786,094 | 13,830,708 | 0 |
| 33 | 66 | 356,298,082 | 23,900,914 | 0 |
| 34 | 68 | 612,059,978 | 41,293,786 | 0 |
| 35 | 70 | 1,054,244,055 | 71,328,579 | 0 |
| 36 | 72 | 1,812,117,741 | 123,182,155 | 0 |
| 37 | 74 | 3,120,499,770 | 212,684,599 | 0 |
| 38 | 76 | 5,365,871,341 | 367,141,131 | 0 |

The period-50 through period-76 rows go beyond the general paper search cutoff, but they
remain bounded computations and must not be described as an all-period exclusion.  The
Java and Python engines agree on the overlapping rows; the Java run is the source of
the period-58 through period-76 counts.

#### A period bound at fixed drift

The four-state reduction also gives an all-period theorem which was not visible in
the unrestricted period search.

**Theorem (width-four period--drift bound).**  If a P3-valid width-four highway has
normalised drift `(m,-m)`, `m>0`, macro period `P`, and ant period `N=2P`, then

```
P <= 7m,   N <= 14m,   and   P = m (mod 2).
```

**Proof.**  Name the macro-transition counts as follows:

```
x: LN->LN,  a: LN->LS,  b: LN->UN,
c: LS->LN,  d: LS->LS,  e: LS->UN,
f: UN->US,  q: UN->UN,  h: UN->LS,
i: US->UN,  j: US->LS,  y: US->US.
```

Flow conservation at `LN` and `US` gives `c=a+b` and `f=i+j`.  The visits to
the bottom extremal line are exactly the `x+c` transitions, and the visits to the
top line are the `f+y` transitions.  Extremal singleton rigidity gives

```
x+c <= m,   f+y <= m,
```

because an extremal translation class is labelled by its `x`-residue modulo `m`
and no such class can occur twice.  In particular `c<=m` and `f<=m`.

On the lower odd line, `a,b,c` turn `R`, whereas `x,d,e` turn `L`.  Summing the
alternating P3 words of all translation classes on that line shows that their total
turn excess is nonnegative.  Hence

```
x+d+e <= a+b+c = 2c <= 2m.
```

Similarly the upper odd line has `2f` right turns and `q+h+y` left turns, so

```
q+h+y <= 2f <= 2m.
```

Let `L1=x+d+e` and `L3=q+h+y` be the lower and upper odd-line left-turn totals.
Summing all transition counts and using the flow identities gives

```
P = 2c + 2f + L1 + L3.
```

The signed longitudinal displacement is

```
m = L1 - L3 - 2x + 2y,
```

because `a+b-c=0` and `f-i-j=0`.  Since `L1<=2c<=2(m-x)`, this identity gives

```
L3 <= m - 4x + 2y,
L1+L3 <= 3m - 6x + 2y.
```

Using also `c<=m-x` and `f<=m-y`,

```
P <= 2(m-x)+2(m-y)+3m-6x+2y
  = 7m-8x
  <= 7m.
```

Every macro transition changes the longitudinal coordinate by `+1` or `-1`, while
the total change is `m`; therefore `P` and `m` have the same parity.  QED.

The constant seven cannot be improved by transition counts, odd-class counts, or
the six-mask residue theorem alone.  Let

```
v = RRLRLLRRRRLLRR
```

be the first primitive period-seven near-model in the table below and take `v^m`.
It has drift `(m,-m)`, macro period `7m`, growth `4m`, exactly `4m` odd classes,
and the mask `{0,2,3,4}` in every longitudinal residue.  Thus it saturates the new
bound while satisfying the incidence/residue skeleton.  For `m=1` it also satisfies
ordinary same-cell alternation.  For every `m>=2`, phases 9 and 17 of `v^m` are
successive visits to the same physical cell `(3,-2)` and both turn `R`, so
concatenating the translated blocks already fails same-cell alternation in the first
two copies.  This family is therefore
an incidence-level sharpness witness, not a highway and not a structural counterexample
for general `m`.  Any improvement below `7m` must use local or stabilised ordering.

Combining `N<=14m` with the strand-density inequality `g>=2m` gives the useful
speed form

```
N <= 7g.
```

Thus a hypothetical width-four highway must create at least one net black cell per
seven ant steps.  This corollary does use the residue/strand theorem through
`g>=2m`; the period--drift bound itself does not.

This is the missing boundedness statement for a *fixed drift*, not a proof that the
whole fixed-width problem is finite-state: the parameter `m` remains unbounded.

##### Primitive diagonal drift is impossible at every period

For `m=1`, the preceding proof becomes a short hand classification rather than a
computer search.  Each extreme line is visited exactly once.  A unique bottom visit
must be `LS->LN` (otherwise a tour which leaves `LN` cannot return), and a unique top
visit must be `UN->US` (otherwise `US` cannot first be reached).  Thus `c=f=1`,
`a+b=i+j=1`.  There are only five translation classes, one on each transverse line.
Growth is their number of odd classes, is positive, and lies in `4 Z`; hence growth
is four.  The two extreme singleton classes already contribute two.  Let the three
interior class excesses be `epsilon_1,epsilon_2,epsilon_3 in {0,1}`; they sum to two.
On the lower and upper odd lines the excesses are respectively
`2-(d+e)` and `2-(q+h)`, so both left-turn totals lie in `{1,2}`.  Moreover

```
P = 4 + (d+e) + (q+h)
```

and `P` is odd because `m=1`.  Thus the two left-turn totals have odd sum; they are
`1` and `2` in one order or the other, and `P=7`.  This derivation does not use the
residue theorem.

Flow conservation leaves the following six state-compatible ant words.  The last
column gives one stabilised interior class, in chronological order; each violates
P3 immediately.

| ant word | bad stabilised class | failure |
|---|---|---|
| `RRLRLLRRRRLLRR` | `LRLR` | starts `L` |
| `RRLRLLLRRRRLRR` | `LRLR` | starts `L` |
| `RRLLRRRRLLLRRR` | `RLLR` | adjacent `LL` |
| `RRLLLRRRRLLRRR` | `RLLR` | adjacent `LL` |
| `RLRRRRLLLRLRRR` | `RRL` | adjacent `RR` |
| `RLLRRRRLLRLRRR` | `LRR` | starts `L` |

Therefore no width-four periodic highway has primitive diagonal drift
`(|a|,|b|)=(1,1)`, at any period.

##### Drift-targeted exact search

`code/java/WidthFourSearch.java` now accepts an optional fixed drift.  It prunes an
endpoint which cannot reach that drift, rejects the wrong period parity, and, when
the drift is fixed, rejects a repeated extremal residue as soon as it occurs.  The
last prune is exactly Theorem (extremal-line rigidity), not a heuristic.  On shared
test ranges its surviving leaf counts equal the `ext` counts of the unpruned search.
The finite range `P<=7m` can therefore be searched exhaustively for each specified
`m`.

The completed finite ranges have zero P3 hits for `m=1,...,9`.  For `m<=6` the
fixed-drift engine was run over the entire interval.  For `m=7,8`, the paper's
all-highway result supplies `P<=24`, and the fixed-drift runs supply respectively
`P=25,27,...,55` and `P=26,28,...,64`.  Thus the present exact finite-drift theorem
is:

> No width-four periodic highway has normalised drift `(m,-m)` for `1<=m<=9`.

The machine-readable summary is `results/width4_drift_exclusion_summary.json`.
This is not an all-drift width-four theorem.

For `m=9`, the existing all-highway search covers `P<=24`, the unrestricted
width-four search covers `25<=P<=38`, and the fixed-drift engine covers every
admissible odd `P` from `39` through the theorem limit `63`.  The final row
`(m,P)=(9,63)` visited `17,532,472,230` nodes in `435.052` seconds and had zero
structural leaves (hence zero P3 checks and zero hits).

#### Spatial block form of the P3 ordering

The chronology criterion admits a useful ordering-sensitive reformulation.  Fix a
transverse line and a longitudinal residue `r mod m`.  Write each occupied physical
cell in that translation class as `ell=r+qm`, and let `B_q` be the word of turns made
at that one physical cell during the period, in ordinary phase order.  Then the
stabilised translation-class word is exactly

```
B_qmax B_(qmax-1) ... B_qmin,
```

with empty blocks omitted.  Indeed an occurrence at phase `i` in cell `q` has
ordering key `i-Nq`.  If `q'>q`, then
`i'-Nq' <= N-1-N(q+1) < -Nq <= i-Nq`, so every occurrence in the higher cell
precedes every occurrence in the lower cell; equal-`q` occurrences retain phase
order.

Consequently P3 is equivalent to three local block conditions: every nonempty
`B_q` alternates; the rightmost nonempty block begins with `R`; and the last turn of
each block differs from the first turn of the next nonempty block to its left.  In
bit notation (`R=0`, `L=1`), if `F_q` is the first turn of a block, this says

```
F_q = parity(total visits in all occupied blocks strictly to its right).
```

Ordinary same-cell alternation supplies the first condition for an actual ant
trace, so the unexploited content is now isolated at the spatial joins.  The three
period-50 countermodels that start `R` fail exactly at these joins.  This lemma is
exact and all-period, but it has not yet yielded a global contradiction; it is the
current route toward replacing the finite `m<=9` computation by an all-`m` proof.

There is an equivalent charge form which is stronger than the aggregate class
identity.  Define the one-period physical-cell charge

```
chi(q) = (# R turns in B_q) - (# L turns in B_q).
```

An alternating block has `chi=0` when its length is even and `chi=+1` or `-1`
when its length is odd, according to its first turn.  The join rule therefore says
that the nonzero charges, read from largest `q` to smallest `q`, are exactly

```
+1, -1, +1, -1, ... .
```

Equivalently, every forward prefix sum of physical-cell charges in one translation
class belongs to `{0,1}`.  Summing the entire class recovers the old odd-class
identity, but the prefix statement is strictly ordering-sensitive and is violated
by incidence countermodels.  Localising the width-four transition-count equations
at a longitudinal cut and combining them with this prefix bound is the most concrete
remaining analytic route.

The alternating-list algebra behind this charge statement was already formalised in
`lean/Langton/P3Endpoint.lean` as `StabilizedP3Word.raw_prefix_bound`. The new step in
this session is the geometric block-order lemma identifying those formal decreasing
levels with ordinary visit blocks of physical cells in the width-four coordinate.
Accordingly this should be presented as a spatial reformulation/bridge, not as an
independent new algebraic theorem.

##### Prefix-flow relaxation: useful failure

`code/python/width4_prefix_flow.py` tests that route without silently assuming a
chronological order. It keeps integer flow conservation on every `(state,ell)`
vertex, `P<=7m`, positive growth, extremal-residue singleton bounds, and every
`{0,1}` prefix-charge inequality. A second version also forces the support of the
directed multigraph to be weakly connected, which together with the degree equations
is enough for some Euler trail to exist.

The disconnected relaxation was SAT already at `m=1`. Adding support connectivity
makes `m=1` UNSAT but remains SAT at `m=2` (`P=12,g=4`) and `m=3`
(`P=19,g=8`). One Euler ordering of the `m=2` flow is

```
b f i h d d c b h d d c,
```

and fails ordinary same-physical-cell alternation at `(1,0)` with successive `R`
turns. This identifies the remaining gap exactly: prefix charges constrain the
*multiset* of local turns, but a connected Euler flow need not realise those turns in
the locally alternating order. Thus the present flow and prefix inequalities alone
cannot prove width-four exclusion; an order-compatible Euler-trail obstruction is
still required. The SAT outputs are countermodels to a proof strategy, not highways.
An additional connected-relaxation query imposing `P>=5m+7` at `m=4` was stopped
after about fourteen CPU minutes without a solver answer; it is recorded as a
timeout, not as evidence for or against the empirical `5m+6` bound.

##### Low crossing-sequence density and a possible pumping route

There is one more exact consequence of `P<=7m`. Work modulo translation by `m`.
For each cut residue `r=0,...,m-1`, let `C_r` count macro steps crossing any lifted
cut `r+qm+1/2`. The quotient path winds once, so forward crossings minus backward
crossings at every cut residue equals one. Hence every `C_r` is positive and odd.
Every macro step crosses exactly one lifted cut, so

```
sum_r C_r = P <= 7m.
```

Let `L` be the number of cuts with `C_r<=7`. Every other cut has `C_r>=9`, while a
low cut still has `C_r>=1`; therefore

```
7m >= sum_r C_r >= L + 9(m-L) = 9m-8L,
```

and `L>=m/4`. Thus a positive density of cuts have crossing sequences of length at
most seven over a finite transition alphabet. This is the standard raw material for
a crossing-sequence pumping lemma: in a sufficiently large minimal counterexample,
two low cuts should have identical signatures and the intervening slab might be
spliced out to reduce `m`.

This is not yet a decidability theorem. A valid signature must include enough tape
colour, row/state, direction, and period-boundary data to make the splice preserve
the ant computation and P3 seed/wake relation. Proving that two equal signatures
really can be spliced is the missing obligation. The density lemma does, however,
turn the previously vague bounded-memory hope into a precise finite-signature
research program.

`code/python/width4_crossing_signatures.py` computes the modular cut signatures and
a deliberately under-decorated
chronological signature (crossing direction, macro states, transition, and turn
pair). On the exact endpoint near-model at `m=10`, cut residues `3,...,9` have
the same five-event phase-free signature

```
d(+) c(-) b(+) h(-) d(+).
```

Residues `0,1,2` correctly receive the six overshoot steps crossing lifted cuts
`10,11,12`; this is why absolute-cut signatures would be wrong. Deleting the
five-transition slab between consecutive repeated cuts turns the explicit
`m` endpoint family into the same family at `m-1`. Thus the naive splice works on
the repeated-block witness and explains its linear form. This is a sanity check for
the crossing-sequence program, not proof that this under-decorated signature is
sufficient on arbitrary traces.

##### Candidate crossing-sequence splice theorem (proof draft)

**Status at 17:45 CDT:** complete proof draft, awaiting adversarial review. Do not
promote the resulting cutoff to the manuscript until the periodic splice/P3 bridge
has been checked independently.

For a macro phase `i` crossing the lifted cut `r+qm+1/2`, define its stabilised cut
key to be `i-Pq`. The **decorated crossing signature** `Sigma_r` is the sequence of
macro transition types at cut residue `r`, sorted by that key. A transition type
records source and target macro states and the two turns; it therefore records which
transverse cells on the two endpoint columns are toggled and with which turns. The
directions in `Sigma_r` alternate `+,-,+,...,+` because the translated infinite path
has signed winding one across the cut.

Let `Gamma_r` be the control projection retaining only direction and the even
transverse line on which the ant lands. It is the actual one-tape control crossing
sequence.

**Candidate splice lemma.** If `Gamma_r=Gamma_s` for two residues `0<=r<s<m`, a
width-four P3-valid trace of drift `m` can be spliced to a P3-valid trace of drift
`m'=m-(s-r)` and transverse width at most four.

**Proof draft.** In every translated longitudinal period, remove the slab of columns
between the lifted cuts `r+qm+1/2` and `s+qm+1/2`. Pair the crossings of its two
boundary cuts in their stabilised chronological order. On a rightward pair, switch
from the old left-half computation immediately after crossing the left boundary to
the old right-half computation immediately after the matching crossing of the right
boundary; do the symmetric operation for a leftward pair. Equality of `Gamma`
supplies the same horizontal heading and destination transverse line, exactly the
finite control needed for this switch. The deterministic one-tape induction below
then shows that all retained events are legal and every retained physical cell has
exactly its old chronological turn history. If the stronger decorated signatures
agree, the same operation can also be visualised as combining equal macro boundary
transitions, but that extra equality is not required.

Let `S` be the remaining set of longitudinal columns and let `phi:S->Z` be the
order-preserving compression. Periodic deletion gives

```
phi(ell+m) = phi(ell) + m'.
```

Hence `phi` bijects retained translation classes modulo `m` with translation classes
modulo `m'`, preserves their front-to-back physical-cell order, and (by the preceding
turn-history observation) preserves every stabilised P3 word. The spliced macro path
has the same start/end state and nonzero drift `m'`. It is nonempty; on its own
extreme transverse line the geometry plus start-`R` forces a singleton `R` class, so
growth is positive. The exact periodic-trace criterion therefore supplies a finite
seed. Its width is even and at most four; width two is already impossible, so it is
again width four. This is the usual crossing-sequence cut-and-paste principle applied
to the two-column macro machine. A standard one-tape formulation can simulate each
macro transition with a finite intermediate state carrying the turn pair.

Finite-seed subtlety: keys `i-Pq` may be negative, and the formal negative-period
path need not be dynamically realised. Choose a physical representative cut
`r+Qm+1/2` far enough ahead that every event occurs at the genuine forward time
`QP+(i-Pq)>=0`, and splice only the future periodic tail. The extracted smaller-
drift tail word is then checked by P3 and receives a fresh finite seed from the exact
criterion; no infinite backward wake is imported.

The information-exchange step is consistent with the classical one-tape crossing-
sequence lemma: equal boundary state sequences permit the left half of one tape
computation to be glued to the shifted right half of another. Jeandel's formulation
states this explicitly in Section 3.3 of *Computability of the entropy of one-tape
Turing machines* (STACS 2014), following Hennie. What remains to audit here is not
that classical lemma, but the equivariant deletion of every translated slab and the
claim that the compressed P3 words are exactly preserved.

The boundary-colour issue can be formulated without any macro-level handwave.
Encode the width-four ant as a deterministic one-tape machine: longitudinal columns
are tape cells with five-bit colour symbols, and the finite control records the
transverse line and heading. Vertical ant moves are stay-put tape moves (or a
two-state simulation of one), while horizontal ant moves cross tape boundaries.
The control projection `Gamma` is the ordinary control crossing sequence. Thus the
classical splice lemma preserves the complete reads and writes on each
retained half, including the two cells next to the join.

For all translated slabs at once, start beyond the finite seed and take a finite-
time direct limit. Any finite execution prefix visits only finitely many slabs, so
it is produced by finitely many ordinary disjoint splices; determinism makes these
prefixes compatible. The compressed initial tape is still finite support because
all far-tail columns are initially blank. Translation of the old tail by `(2P,m)`
preserves the splice pattern and becomes a translation by `m'=m-(s-r)` after
compression. The remaining self-audit obligation is to state completely why this
equivariance advances the spliced oriented event path by one positive finite number
of events. A retained cut with nonempty net-right crossing sequence supplies the
proposed proof. The theorem remains labelled candidate pending hostile review.

That last step has now been rewritten in the crossing-sequence graph. Far beyond the
seed, each longitudinal column is initially the all-white five-bit symbol; its two
boundary crossing sequences form a compatible labelled edge. The highway therefore
gives a closed walk of length `m` in the graph. Equal vertices `Gamma_r=Gamma_s`
allow the intervening closed subwalk to be deleted, leaving a closed walk of length
`m'`. In the direct-limit computation, translating every retained local column
transcript by one new cycle maps each `j`-th boundary occurrence to the corresponding
`j`-th occurrence. It is therefore a successor-preserving self-map of the one-way
tail event path, hence `n -> n+k`; `k` is finite and positive because the spatial
coordinate changes by `m'>0`. This gives the required time period. The remaining
review target is whether the direct limit could truncate a nominal crossing
sequence at infinity; the finite-prefix compatibility argument is intended to rule
that out.

The truncation issue has a monotone resolution. For two cuts `A<B`, a paired
rightward crossing occurs at `A` before `B`, and a paired leftward crossing at `B`
before `A`. Every splice therefore jumps forward in the old execution and only
deletes a chronological interval. Adding a farther splice makes the retained event
list a subsequence of the previous one. The event index of a fixed retained crossing
is a nonincreasing natural number and stabilises; the finite one-cut lemma guarantees
the occurrence exists at every stage. No crossing can vanish only at infinity, and
an extra crossing at a finite limit index would already occur at a finite stage.
This completes the present self-audit of the direct limit, still subject to an
independent adversarial check before manuscript promotion.

Assuming the splice lemma, choose a width-four highway of minimal drift magnitude
`m`. Its control signatures are pairwise distinct. At least `m/4` have length at most
seven. For a rightward crossing the destination is line `2` or `4`; for a leftward
crossing it is line `0` or `2`. The direction pattern is fixed at odd lengths, so
there are two choices per event. Therefore the number
of possible low control signatures is at most

```
F = 2 + 2^3 + 2^5 + 2^7 = 170.
```

The density lemma gives the first cutoff `m <= 4F = 680`. The full average-length
budget is stronger. Distinct length-`1,3,5,7` signatures have capacities
`2,8,32,128`. Relative to average seven, their total available deficit is
`6*2+4*8+2*32=108`. Every other signature has length at least nine and costs at
least two units, so there are at most 54 of them. Therefore

```
m <= 2+8+32+128+54 = 224.
```

Extremal singleton rigidity makes the count polynomial rather than binary. In a
length-`2n+1` signature, the exceptional rightward top landing `(+ ,4)` can occur at
most once, and the exceptional leftward bottom landing `(- ,0)` can occur at most
once; otherwise two phases occupy the same extremal translation class. All other
landings are on line `2`. Hence there are at most `(n+2)(n+1)` signatures of that
length. The short capacities become `2,6,12,20`, with total deficit
`6*2+4*6+2*12=60`; at most 30 signatures can have length at least nine. Therefore

```
m <= 2+6+12+20+30 = 70.
```

Combining this explicit drift cutoff
with `P<=7m` would make width-four existence decidable by a finite search. It would
not itself exclude width four, and the present exact search through `m=9` is nowhere
near the new cutoff.

The first implementation sorted a modular signature in raw phase order. That was
also insufficient: an event at phase `i` on the lifted cut `r+qm+1/2` occurs at the
representative cut at time `i-Pq`. The checker now sorts on this stabilised key. All
raw-phase signature output is superseded.

An earlier count used all six decorated macro transition types available in each
direction and gave the weaker conditional cutoff `1,151,736`. The literal one-tape
encoding shows that decoration is unnecessary for splicing: fixed direction plus
destination even line is the complete crossing control. The older number remains a
valid over-refined conditional bound but is superseded by the extremal-weighted
bound `70`.

##### Candidate all-period width-four exclusion from the blank-column graph

The control projection makes a stronger finite local test possible. For an initially
white longitudinal column, simulate its five cells using the exact crossing
sequences at the left and right boundaries. Each sequence alternates direction,
starts and ends rightward, and by extremal singleton rigidity contains at most one
rightward top landing `4` and at most one leftward bottom landing `0`.

`code/python/width4_crossing_graph.py` performs the literal column simulation. Its
unbounded finite-state generator tracks the 32 colour masks, current entry line and
heading, and four exceptional-event flags. It finds no reachable entry-state cycle
and exactly these compatible edges (line numbers concatenated):

```
202       -> 4
4220222   -> 2, 202, 20222, 2022224
2042222   -> 2, 202, 20222, 2022224
202242222 -> 422, 42202, 4220222.
```

The 12-edge, 10-vertex graph is acyclic; its longest path has length three,
`202242222 -> 4220222 -> 202 -> 4`. A finite-support width-four highway would have
infinitely many initially white columns beyond its seed, and their adjacent exact
boundary sequences would form an infinite path in precisely this graph. Thus the
finite table is a candidate proof that width four is impossible at every period.

The script cross-checks the generator against independent pairwise compatibility
tests for every extremal signature through length 25. Source SHA-256 is
`2AF99EDCBC355945B547AB1F80CAEE6927FA75D6C1C064C5ADC41D13B5FE3E33`.
The generator reaches 22 entry states, has maximum entry depth eight, and finds no
reachable entry cycle.
At the time of discovery this was a promotion gate: a referee still had to attack
the control-state projection, turn convention, boundary indexing, exceptional flags,
and repeated-state logic.  That gate was discharged after the 19:00 cutoff; the
details and one repaired statement-level omission are in Journal \S38.16.
`lean/Langton/WidthFourCrossing.lean` checks the rank-decrease certificate and
impossibility of a four-edge chain, but explicitly assumes the 12-edge table is
complete. Its SHA-256 is
`548DF94E2B8B60CE23269153EE446CFF824AC1DB6AA1A41773F4E605205324FF`.
An independent literal verifier using compass-letter headings and set-valued black
rows, importing no project search code, reproduces the same 12 edges:
`code/python/verify_width4_crossing_graph_indep.py`, SHA-256
`694C1178B00FA8AB929A5375255E53762C403DE02FC1D2958A4409EF9B84AFE0`.
It also validates the boundary convention on the genuine standard finite seed by
replaying an initially white far-ahead column between cuts 100 and 101; the extracted
boundary lengths are 31 and 21 and the replay is exact.

The mechanism is genuinely width-four-specific. The generic exploratory generator
`code/python/explore_even_width_crossing_cycles.py` finds no reachable local entry
cycle at width four, but at both widths six and eight finds the same two-state cycle

```
(black rows {1,2}, entry line 2 east)
  <-> (black rows {1,3}, entry line 2 west),
```

without reusing either exceptional extreme event. Wider strips therefore recover
unbounded interior memory, so the acyclic-column proof does not extend directly.
SHA-256: `760CD63D8CCC0292AD5FF2A3134CAE7A4E2CDD1AA16758527BFF5F706806F327`.

###### Paper-grade lemma chain for the direct exclusion

The following formulation survived the final pre-manuscript self-audit.

1. **Far-cut lemma.**  After a 180-degree rotation if necessary, take drift
   `(m,-m)` with `m>0`, longitudinal coordinate `x`, and shift the five transverse
   lines to `t=x+y in {0,...,4}`.  For every sufficiently large half-integer cut
   `x=k+1/2`, the complete future crossing sequence is finite, has positive odd
   length, and alternates east, west, ..., east.  This follows because the periodic
   path has only finitely many phase offsets from `nm`, while its longitudinal
   coordinate tends to `+infinity`.
2. **Control-projection lemma.**  Record the transverse coordinate immediately
   after each horizontal crossing.  Eastward records lie in `{2,4}` and westward
   records in `{0,2}`.  Event parity supplies the direction.  This record is the
   full control state with which the deterministic ant computation enters the next
   tape column; vertical moves stay in that column.
3. **Extremal-signature lemma.**  In one cut sequence, eastward label `4` and
   westward label `0` each occur at most once.  Either repetition would enter the
   same extremal cell at the fixed destination column twice, contrary to
   extremal-line rigidity.
4. **Blank-column classification lemma (computer-assisted).**  Starting from five
   white cells, the exact deterministic within-column simulation, under the two
   singleton restrictions on each boundary, permits exactly the twelve displayed
   ordered pairs of boundary sequences.  The exhaustive recursion has 22 reachable
   entry states, no reachable state cycle, and maximum depth eight.  A separately
   written recursion returns the same edge set.
5. **Rank lemma.**  Assign rank 3 to `202242222`, rank 2 to `4220222` and
   `2042222`, rank 1 to `202`, and rank 0 to all other occurring signatures.  Every
   one of the twelve edges strictly lowers rank.  Hence there is no directed path
   of four edges.  This finite implication is checked in Lean.
6. **Tail contradiction.**  At the time the periodic tail begins, only finitely
   many cells have been visited and only finitely many are black.  Every sufficiently
   far column is therefore an untouched white five-cell column.  Its two exact cut
   sequences are an edge in the classified graph.  Consecutive far columns would
   give arbitrarily long, indeed infinite, directed paths, contradicting the rank
   lemma.

The theorem is scoped to diagonal-drift finite-support periodic highways.  It does
not exclude non-diagonal translators, does not exclude widths six or eight, and does
not prove that arbitrary finite seeds ever enter a periodic tail.  The only
computer-assisted premise is item 4; the paper must not describe the current Lean
artifact as an end-to-end formalisation of that premise.

The width-six two-cycle was also decoded by hand.  In mask `{1,2}`, an eastward
entry on centre line 2 turns `L` at black row 2 and then `R` at white row 3, exiting
east with mask `{1,3}`.  A westward return on line 2 turns `R` at white row 2 and
then `L` at black row 3, exits west, and restores `{1,2}`.  Hence the repeated cells
themselves alternate perfectly and no extreme is reused.  This proves that the
failure of the width-four method at width six is not removed by ordinary local
alternation; a wider proof must couple columns or exploit the first-letter order of
whole translation classes.  The oscillator remains a local obstruction, not a
global highway.

##### A sharp but unproved structural pattern

For every tested `m=3,...,9`, the *last* macro period having even a
same-cell-alternating, extremal-singleton structural leaf is

```
P = 5m + 6,
```

and there are exactly `m` leaves at that endpoint.  One family has a transparent
five-macro repeated block and growth four.  The same runs show longitudinal
overshoot bounds `min ell >= 1-m` and `max ell <= 2m+1` for every structural leaf
through `m=8`.  These two regularities strongly suggest a rotor/odometer lemma that
would improve `P<=7m` to roughly `P<=5m+6`.

Neither regularity is proved.  The completed `m=9` theorem-bound range confirms the
period endpoint, but the overshoot observation was recorded only through `m=8`.
Do not use `5m+6`, the `m`-leaf count, or the overshoot bounds in the manuscript as
theorems; they are research targets for a future local-alternation argument.

One endpoint leaf does have an exact formula, although it is only a near-model. In
transition-count notation, for every `m>=3` take

```
(b q f j d d c) (b h d d c)^(m-2) (b h d d e f i h c).
```

Each displayed transition is valid in the four-state automaton. The first block,
each repeated block, and the last block have net longitudinal displacement one, so
the total drift is `m`; their lengths give `P=5m+6`. Grouping the cells in the three
block types shows ordinary same-physical-cell alternation. The bottom visits occupy
`m` distinct residues and the two top visits occupy distinct residues for `m>=3`,
so it also has extremal singleton rigidity. Its growth is four. It is not P3-valid:
on the lower odd line the two cells `ell=m+1` and `ell=1` in one residue have
ordinary words `LR` and `LRL`, so their right-to-left stabilised concatenation is
`LRLRL` and starts with `L`. It also fails the aggregate odd-class identity. This
family proves that an eventual upper bound `P<=5m+6`, if established, would already
be sharp at the ordinary-alternation/extremal level.

The next fixed-drift run confirmed this structural pattern at `m=10`: `P=56` has
exactly ten extremal-singleton, ordinary-alternating leaves, all with growth four and
none satisfying growth/odd-class equality; `P=58` has no structural leaf. Completed
zero-hit rows at this checkpoint cover every even `P=40,42,...,60`. The `P=60` row
visited `19,138,313,024` nodes and had no structural leaf. Higher theorem-
range rows were still running and are not counted until completion. At the extended
checkpoint, `P=62` also completed: `30,238,836,043` nodes, no structural leaf, and
no P3 hit. Then `P=64` completed `47,442,673,612` nodes with no structural leaf or
P3 hit. `P=66` then completed `74,038,045,927` nodes with no structural leaf or P3
hit. The `P=68` and `P=70` workers were stopped unfinished at 18:56:13 CDT; neither
returned a completed row, so both remain uncounted. The completed
rows are preserved in `results/width4_m10_partial_2026-07-21.json`.

#### Lean arithmetic checkpoint

`lean/Langton/WidthFour.lean` machine-checks deliberately delimited arithmetic
kernels:

1. the exhaustive six-mask classification from five binary variables and the signed
   mod-four equation;
2. `P<=7m` from the boundary, displacement, and odd-line count inequalities;
3. `P congruent to m (mod 2)` from the numbers of `+1` and `-1` macro moves; and
4. `P=7` in the primitive case once the two odd-line left-turn totals are `1` and
   `2`;
5. the even-fiber step and finite summation step in the upper bound `g<=mW`;
6. the arithmetic ordering of phase keys in distinct physical-cell blocks; and
7. the one-quarter lower bound for cuts crossed at most seven times.

The pinned Lean 4.32.0 build completes 22 jobs, the audit reports only the standard
Lean axioms, and a source scan finds no `sorry` or `admit`.  This is not an
end-to-end formalisation of the geometry: extremal rigidity, the macro transition
table, flow identities, and the passage from P3 alternation to the count inequalities
remain explicit mathematical inputs.

#### Independent SMT formulation

`code/python/width4_smt.py` encodes a fixed `(m,P)` instance directly in Z3.  Its
symbolic variables are the macro state, longitudinal coordinate, and transition at
each time.  For every phase it forms the exact class key

```
phase - 2P * floor(ell/m)
```

and counts how many same-class phases have smaller keys.  Even rank is constrained
to `R` and odd rank to `L`, which is the stabilised P3 condition without calling the
enumerator's checker.  Any SAT word is replayed through the independent Python walk
and P3 implementation before being reported.

Z3 5.0.0 returned exact `unsat` for `(m,P)=(1,7),(2,6),(2,8),(2,10),(3,9)` and
for `m=9`, `P=9,11,13,15`.  It timed out rather than returning `unsat` at the harder
instances `(2,12)`, `(9,17)`, and `(9,19)`.  Therefore the SMT work is presently a
bounded cross-check, not a stronger exclusion and not a proof certificate.  The
timeouts are recorded as timeouts, never as negative results.

##### Failed optimisation: incremental class arithmetic

A proposed Java prune tracked partial class parities and transverse-line turn
excesses, rejecting a branch when the remaining phases could not make each line's
excess equal its number of odd classes.  The condition was sound and reproduced the
small rows, but on the completed benchmark `(m,P)=(9,57)` it visited
`4,621,247,456` nodes in `410.472` seconds, versus `4,623,723,311` nodes in
`329.221` seconds without the bookkeeping.  A `0.054%` node reduction did not pay
for per-node array updates.  The optimisation was removed from the final source.

#### Important limitation

The phrase "fixed width is finite-state, therefore decidable" has not been proved.
A finite alphabet on an unbounded longitudinal tape is not itself a finite state
space and can support Turing-machine behaviour.  What is proved finite-state here is
only the odd-skeleton residue constraint: the vertical and diagonal six-mask rules
form a finite-memory shift of finite type.  Turning that skeleton into a complete
chronological highway classifier still requires a bounded-memory theorem that is
currently missing.

#### Next mathematical target

The bounded data suggest a universal start-order obstruction: among structural
width-four cycles, the odd-class identity has survivors, but every survivor still
has at least one translation class whose stabilised sequence starts with `L` or
fails alternation.  The useful target is therefore not another incidence equation.
It is a proof that every single tour of the four-state ladder with nonzero winding
forces one such bad chronological class.

##### Failed strengthening: condition (ii) alone is not enough

Through ant period 48, no structural leaf even satisfied the condition that every
stabilised class starts with `R`.  It was tempting to conjecture that the first-turn
condition alone excludes width four.  Period 50 disproves that strengthening: there
are exactly three based structural cycles with every class starting in `R`.  Their
drift is `(1,-1)`; two have growth 8 and one has growth 4.  They fail alternation in
respectively 5, 4, and 5 classes.  The growth-4 example also satisfies the aggregate
odd-class identity (`growth = 4 = number of odd classes`), so even the first-turn
condition plus that incidence identity is insufficient.

One of the three countermodels is

`LRLRLRLRLRLRLRLRLRLRRLRRLRLRLRLRLRLRLRLRLRLRRLLRRR`.

Its five transverse classes have sizes `3,11,11,12,13`; all start with `R`, but
their stabilised sequences include long constant blocks and violate alternation.
This is a useful negative result: any all-period width-four proof must use both
ordering clauses of the exact criterion, not merely the first-turn clause that was
enough to establish the extremal-line theorem.

##### Discarded boundary-transition reduction

An attempted ten-transition reduction was rejected during this session.  I initially
read the pair labels as though the first symbol were the even-line turn and deleted
`LN->LN` and `US->US`.  In fact the macro pair is `(odd turn, even turn)`; those two
transitions are `LR`, so their *boundary* turn is `R`, exactly as extremal rigidity
requires.  The deleted `L` occurs on the adjacent odd line.  No statement or search
depending on that false reduction is retained.

<a id="source-research-notes-width6-research-2026-08-17-md"></a>

## width6_research_2026-08-17

Source: `research-notes/width6_research_2026-08-17.md`.

### Width-six research log — 17 August 2026

The completed audit at the end of this log records the computer-assisted
all-period width-six exclusion. The opening objectives and candidate sections
retain the status of the earlier exploratory stages.

#### Objective and claim discipline

The target is an all-period exclusion of diagonal finite-support periodic highways
of transverse width six.  Together with the proved even-width theorem and the
width-two and width-four exclusions, this would prove `W >= 8`.

Nothing in this file is a theorem merely because it appears here.  Each item is
labelled as one of:

- **proved input** — already established in the paper;
- **exact computation** — exhaustive only over the stated finite range;
- **candidate lemma** — requires a complete proof and adversarial audit; or
- **failed route / countermodel** — retained to prevent its reuse.

The universal highway conjecture remains open.  No width-six exclusion is claimed
at the start of this log.

#### Proved inputs

Normalize diagonal drift to `d=(m,-m)`, `m>0`, put `t=x+y`, and shift the
transverse range to the seven lines `0,...,6`.  Lines `0,2,4,6` have horizontal
arrivals and lines `1,3,5` have vertical arrivals.  Every reached cell on the two
extremal lines `0,6` is a singleton translation class, is entered once, and turns
`R`.  The exact finite-support criterion says that the stabilized word in every
translation class alternates and starts with `R`.

Observe the ant only on odd lines.  A macro step contains one turn on an odd line
and one on an even line.  Its state is `(odd line, vertical arrival heading)`, so
there are six states.  The longitudinal coordinate is `ell=x`; each macro changes
`ell` by `+1` or `-1`.  A width-six highway can be cyclically based immediately
after a bottom-extremal visit, in state `(1,N)`, and returns to that state translated
by `m` after one macro period.  It must also visit line `6`.

#### Known local obstruction to the width-four method

The one-column all-white entry graph is recurrent at width six.  Suppressing the
extremal-use flags, it contains the literal two-state rotor

```text
(black rows {1,2}, enter row 2 east)
    <->
(black rows {1,3}, enter row 2 west).
```

The eastward half turns `L` at black row 2 and `R` at white row 3; the westward
half turns `R` at white row 2 and `L` at black row 3.  Both reused cells alternate
correctly, and neither extreme is touched.  Therefore per-cell alternation and the
four extremal singleton flags cannot make the width-six blank-column graph acyclic.
This rotor is only a local transcript: no global periodic path, nonzero drift, or
start-with-`R` translation-class ordering follows from it.

#### Exact exploration apparatus

`code/python/search_width6.py` generates the complete six-state macro table directly
from the turn rule, enforces ordinary physical-cell alternation during DFS, and
applies the full stabilized P3 criterion at every closed positive-drift width-six
leaf.  A reported hit would therefore be a genuine periodic trace admitted by a
finite seed.  A zero row is only a bounded exact computation.

The immediate purpose is diagnostic:

1. find the smallest structural and start-with-`R` near-models;
2. identify which line and class order kills them;
3. test candidate transition-count inequalities before attempting a proof; and
4. decide whether coupled-column recurrence survives the complete P3 ordering.

#### Live questions

1. Does P3 force a period--drift bound at width six analogous to `P<=7m` at width
   four?  A finite bound at fixed `m` is useful but is not by itself an all-drift
   exclusion.
2. Can the centre rotor appear on infinitely many initially white columns while the
   stabilized word of every translated class starts with `R`?
3. Does coupling two consecutive blank columns eliminate all recurrent components,
   or merely create a larger rotor?
4. Can the signed residue identities restrict the seven-bit odd masks strongly
   enough that every recurrent local component misses a required wake class?

#### Candidate breakthrough: five blank columns are impassable

**Status: candidate computer-assisted lemma, awaiting independent implementation
and hostile bridge audit.  Do not cite as a theorem yet.**

The bounded crossing graph has no directed cycle through maximum signature length
21.  More strongly, its longest observed directed path is four from length cap nine
onward.  This suggested eliminating the unbounded signature alphabet by simulating
several adjacent columns at once.

`code/python/width6_block_exclusion.py` performs an exact finite-state exploration of
a blank `k`-column by seven-line block.  Its state retains:

- all `7k` colour bits;
- the entry line and heading at the current outer boundary;
- a bit for every physical extremal cell already visited; and
- the four possible exceptional extreme events on the two outer cuts.

Between outer-boundary crossings the program runs literal Langton dynamics.  At an
outer exit it nondeterministically permits every geometrically possible later
re-entry line.  Thus it deliberately over-approximates the unknown computation
outside the block.  A right exit is recorded as a possible final exit before any
return is chosen.  Previously seen full states are merged because the retained
state determines every future in-block update and every permitted outer re-entry.

Fresh output:

```text
columns=1 states=429   transitions=814   terminals=162
columns=2 states=2,052 transitions=2,966 terminals=824
columns=3 states=811   transitions=1,043 terminals=259
columns=4 states=257   transitions=324   terminals=36
columns=5 states=151   transitions=212   terminals=0
columns=6 states=151   transitions=212   terminals=0
```

The four-column terminals are a positive control.  The zero at five columns agrees
with the independently generated bounded boundary graph's longest path four, but
those programs currently share the same turn convention and are not independent
implementations.

##### Proposed global bridge

A positive-drift periodic highway crosses each fixed far-ahead longitudinal cut
only finitely many times.  Finite initial support and the finite preperiod imply that
five sufficiently far consecutive strip columns are initially white and untouched
when the periodic tail begins.  The ant starts to their left.  Its first entry into
the block is therefore a rightward crossing of the left boundary; positive drift
forces an eventual final rightward exit from the right boundary.  The intervening
literal history, with arbitrary excursions outside either outer cut, is one of the
states explored by the block program.  Extremal-line rigidity supplies the
once-visit constraints on the physical extreme cells and the two outside extreme
cells represented only by outer-cut flags.  A zero-terminal certificate would
contradict the required final exit.

If the finite classifier and this bridge pass audit, no diagonal width-six periodic
highway exists.  With even transverse width and the already accepted width-two and
width-four exclusions, this proves `W >= 8`.

##### Required attacks before promotion

1. Verify independently that horizontal moves update `(column,t)` by `(±1,±1)` and
   vertical moves by `(0,±1)`, and that the stored crossing labels are destination
   transverse lines.
2. Check that all information influencing future in-block dynamics survives state
   merging; in particular, no boundary-word history beyond the four extreme flags
   may affect legality.
3. Prove that internal-cut extreme events are already represented by physical
   extremal-cell visit bits and that only the two outward-facing extreme cells need
   the outer flags.
4. Write a separately structured verifier using compass headings and set-valued
   colours/visits, with no import from either width-six classifier.
5. Extract at least one four-column terminal transcript and replay it literally as a
   positive control.
6. Have an adversarial referee attempt to embed a hypothetical highway transcript
   that enters first from the right, bypasses a column, or lacks a final right exit.

#### Stronger flag-free form: six blank columns are impassable

**Computer-assisted theorem; supersedes the five-column formulation.**

The five-column classifier is sound, but it remembers four flags for extreme events
immediately outside the block.  A hostile relaxation removes all four flags, forgets
the entire exterior history after every exit, and permits every geometrically allowed
return after every outer excursion.  With that strictly larger transition system,
five columns have 46 right-exit terminals but six columns have none:

```text
relaxed columns=1 states=192   transitions=480   terminals=72
relaxed columns=2 states=3,453 transitions=6,951 terminals=1,131
relaxed columns=3 states=5,208 transitions=7,977 terminals=1,867
relaxed columns=4 states=633   transitions=900   terminals=102
relaxed columns=5 states=555   transitions=819   terminals=46
relaxed columns=6 states=357   transitions=555   terminals=0
```

For six columns the 357 boundary-entry states produce 172 rejected attempts to
revisit one of the 12 physical extremal cells, no trapped deterministic in-block
cycle, and at most 58 literal cell visits between outer crossings.  The only legal
exits are through the left boundary: destination lines 0, 2, and 4 occur 38, 78,
and 69 times respectively.  No state reaches the right boundary.

`verify_width6_block_indep.py --relaxed` reproduces every state, transition,
terminal, rejection, maximum-segment, and exit count using compass headings and
immutable sets, with no imports from the primary classifier.  A third single-cell
state exploration (not boundary-compressed) independently reached 3,186 in-block
states plus 118 explicit left-outside nodes (3,304 total), with no right-outside
node.  The boundary-compressed scripts
retain a positive control: five columns have 46 terminals after the relaxation.

##### Paper-grade local lemma

Let a `6 x 7` block consist of six consecutive longitudinal columns and transverse
lines `0,...,6`, initially all white.  Suppose every one of its 12 cells on lines
0 and 6 may be entered at most once.  Start with an eastward entry through the left
boundary on destination line 2, 4, or 6.  Between literal in-block segments, allow
an exit through either outer boundary to be followed by an arbitrary return through
the same boundary on any geometrically permitted destination line, forgetting all
outside state.  Then no right-boundary exit is reachable.

The finite premise is computer-assisted.  It is a reachability calculation on 357
reachable boundary states, not a bounded-period or bounded-crossing-length search.
The arbitrary-return rule is an over-approximation, so the classifier does not need
to prove that a chosen exterior excursion is itself dynamically realizable.

##### Global contradiction

For a hypothetical width-six periodic highway, normalize `d=(m,-m)`, `m>0`, and
`t=x+y in {0,...,6}`.  Let `N` be the ant period.  At phase `i` of translated
period `q`,

```text
x(qN+i) = qm + x(i),
```

so `x` tends to `+infinity`, and every fixed longitudinal cut is crossed only
finitely many times.  Choose six consecutive columns beyond both the finite initial
black support and the finite past footprint at the start of the periodic tail.  They
are initially white and untouched.  Continuity and the fact that the ant starts to
their left force the first block entry to be eastward through the left boundary.
Since `x` tends to infinity and both outer cuts have finite crossing sequences, the
block history has a final eastward exit through the right boundary.

Every actual outside excursion is included among the classifier's arbitrary return
choices.  It returns through the same outer boundary: moving from one side of the
block to the other while staying in `t in {0,...,6}` would already cross an in-block
column.  Extremal-line rigidity says that each of the 12 in-block cells on lines 0
and 6 is entered at most once, exactly the classifier's only history-sensitive
rejection.  The actual block history would therefore reach a right-exit terminal,
contradicting the exact zero-terminal result.

With the exact certificate and mathematical reduction recorded below, this
excludes every diagonal
finite-support periodic highway of transverse width six.  Combining it with even
width and the accepted width-two and width-four exclusions gives `W >= 8`.  It says
nothing about universal entrance, non-diagonal translators, or whether width eight
is possible.

#### Promotion gate and completed audit

The `W>=8` statement entered the paper only after all of the following held:

1. a complete mathematical reduction from a hypothetical width-six highway to the
   proposed finite obstruction;
2. an exact classifier whose completeness assumptions are stated explicitly;
3. an independently written verifier or a fully formal enumeration;
4. hostile review of coordinate conventions, boundary ordering, finite-support tail
   selection, and the global-to-local bridge; and
5. isolated fresh-process reruns with archived outputs and hashes.

The released primary classifier, separate verifier, and certificate audit
check the flag-free six-column formulation. Their SHA-256 hashes are

```text
width6_block_exclusion.py       3f1c92c831e45bcc0e60a282e4652bf72a07da22a1dc7ef711de2172a78c24af
verify_width6_block_indep.py    7121555c44eb96eda955002136b8cda35ea8f9d2f979da3416f7e62fb422c65f
audit_width6_block.py           68aba194450ba05872fe37bbd20c260916c5718dc805e15b09be76d11a4c1908
```

The machine-readable record is `results/width6_block_certificate.json`.  Promotion
status is **computer-assisted all-period exclusion of diagonal width six**, with the
global reduction proved in the manuscript and the finite reachability premise
reproduced by two separately written enumerators.  It is not an end-to-end Lean
formalization and does not settle the universal highway conjecture.

<a id="source-research-notes-width8-research-2026-08-17-md"></a>

## width8_research_2026-08-17

Source: `research-notes/width8_research_2026-08-17.md`.

### Width-eight research log — 17 August 2026

The promotion-audit section at the end records the computer-assisted
all-period width-eight exclusion and the resulting diagonal bound `W>=10`.
The initial candidate sections retain the status at the start of the log.

#### Objective and claim discipline

The target is an all-period exclusion of diagonal finite-support periodic highways
of transverse width eight.  If accepted, the even-width theorem and the exclusions
of widths two, four, six, and eight would imply `W>=10`, matching the standard
period-104 highway's width.

Current status at creation: **exact exploratory computation, not yet a theorem**.
Nothing here proves `g>=12`, universal entrance, or uniqueness.  The universal
highway conjecture remains open.

#### Candidate finite obstruction

Normalize diagonal drift to `(m,-m)`, `m>0`, and put `t=x+y in {0,...,8}`.  Explore
an initially white block of consecutive longitudinal columns while retaining all
in-block colours, once-entry status of the in-block extremal cells on `t=0,8`, and
the inward boundary pose.  After every outer exit, erase all exterior history and
allow every geometrically possible return through that same boundary:

- eastward left entries on destination lines `2,4,6,8`;
- westward right entries on destination lines `0,2,4,6`.

This is a strict over-approximation of actual exterior dynamics.  The first
exploratory implementation found 1,188 right-exit terminals for seven columns and
zero for eight columns.  A separately structured in-memory set/compass verifier
reproduced its eight-column counts: 20,320 states, 42,004 return transitions, 9,819
repeated-extremal rejections, zero local loops, maximum 90 cell visits within one
segment, and left exit counts 1,586, 3,090, 3,114, 2,711 at labels 0,2,4,6.

Released candidate implementations are being added as
`code/python/width8_block_exclusion.py` and
`code/python/verify_width8_block_indep.py`.  Their complete counts, hashes, and a
deterministic cross-audit are required before promotion.

#### Candidate global bridge

Let `N` be the ant period.  At phase `i` of translated period `q`,
`x(qN+i)=qm+x(i)`, so the longitudinal coordinate tends to infinity.  Choose eight
consecutive columns beyond both finite initial black support and the finite past
footprint at periodic-tail start.  They are untouched and white.  The first block
entry is eastward from the left, and some later right exit is forced.

Every excursion between maximal in-block segments returns through the same outer
boundary before the next segment: within the full strip `t in {0,...,8}`, changing
longitudinal sides would already cross the block.  All actual returns are therefore
allowed by the relaxation.  Extremal-line rigidity supplies once-entry for the 16
in-block extremal cells.  A certified zero right-exit result would contradict the
hypothetical highway transcript.

#### Promotion gates

1. Primary and separately written on-disk enumerators reproduce every certified
   count.  The release certificate records columns six through eight; smaller
   blocks are not claimed as an archived complete table.
2. A deterministic audit checks exact tables, source hashes, and positive controls.
3. A hostile referee audits coordinate conventions, state completeness, and the
   global same-side-return bridge against the actual released code.
4. The paper and public summaries state the computer-assisted boundary and keep
   `g>=12`, uniqueness, and universal entrance open.
5. Fresh-process reruns, a clean LaTeX build, visual PDF review, and regenerated
   artifact hashes succeed.

#### Promotion audit and accepted status

The primary and separate verifier reproduce every certified row, and
`audit_width8_block.py` checks the complete row data, headline fields, positive
controls, and embedded source hashes. The global reduction is the mathematical
argument stated above; these finite checks do not replace that argument.



Official source SHA-256 values are:

```text
width8_block_exclusion.py       fe879d015e716a4b3e4aa951d20069d8c6b323d272563b776115ebf993c603f9
verify_width8_block_indep.py    29cf021cb92027d4ec090238ca0ece2cbb6ad32f02f298cf9943c6196d2ea70e
audit_width8_block.py           fc59b26d515533c5d559cf31cd2d008a6931675c2b99a8510ec4587c6f56f693
```

Promoted claim: **computer-assisted all-period exclusion of diagonal transverse
width eight; hence diagonal `W>=10`**.  The global reduction is a conventional proof;
the exhaustive local reachability premise is computer checked by two separately
written implementations and is not formalized in Lean.  This lower bound is attained
by the standard highway, but no uniqueness at width ten follows.  `g>=12`,
non-diagonal translators, universal entrance, and the highway conjecture remain open.
