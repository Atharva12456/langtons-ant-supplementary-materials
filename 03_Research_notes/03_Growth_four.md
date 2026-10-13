# Growth-four classification

These notes retain their original dates and hypotheses. Later status
pointers distinguish superseded checkpoints from the current report.
Individual source files and linked records are preserved in
[research_notes_sources.zip](research_notes_sources.zip).

## Contents

- [primitive_cap4_analytic_2026-08-20](#source-research-notes-primitive-cap4-analytic-2026-08-20-md)
- [primitive_g4_cap3_analytic_2026-08-20](#source-research-notes-primitive-g4-cap3-analytic-2026-08-20-md)
- [primitive_g4_cap5_symbolic_2026-08-22](#source-research-notes-primitive-g4-cap5-symbolic-2026-08-22-md)
- [primitive_g4_research_2026-08-20](#source-research-notes-primitive-g4-research-2026-08-20-md)

<a id="source-research-notes-primitive-cap4-analytic-2026-08-20-md"></a>

## primitive_cap4_analytic_2026-08-20

Source: `research-notes/primitive_cap4_analytic_2026-08-20.md`.

### Primitive-diagonal crossing cap four: an analytic obstruction

Subsequent status: the unrestricted primitive-diagonal growth-four case is
excluded by the analytic reduction and computer-assisted affine classification
in [the top-boundary note](03_Growth_four.md#source-research-notes-primitive-g4-cap5-symbolic-2026-08-22-md). The
growth-eight cases remain open. The entries below preserve the earlier
checkpoint and its intermediate questions.

#### Status

This note proves an **analytic conditional exclusion**.  It does not prove
`g>=12` or classify all periodic highways.  Its conclusion is:

> **Cap-four obstruction.**  Every primitive-diagonal finite-support periodic
> highway has one of its first four cuts above the bottom rail crossed at least
> five times in each direction.

Equivalently, after normalizing the drift to `d=(1,-1)` and writing `f_c` for
the number of upward (and hence downward) crossings of the cut between transverse
levels `c` and `c+1`, the inequalities `f_c<=4` for all `c` are impossible.

The proof uses extremal-line rigidity, the established width bound `W>=10`, and
the exact stabilized-order part of the periodic-realisability criterion.  It is
not a bounded-period or bounded-width computation. At this checkpoint, the
remaining primitive growth-four and growth-eight cases therefore required a fat
cut `f_c>=5`.

#### Rooted-plane-tree state

Put the singleton bottom rail at level zero.  The positive transverse excursion
is the contour of a rooted plane tree.  At a fixed depth list its nodes in contour
order and record

```text
B=(b_1,...,b_n)       longitudinal bases,
V=(v_1,...,v_n)       horizontal voltages of the complete subtrees.
```

The root state is `B=(0), V=(1)`.  At depth `d`, put
`epsilon_d=(-1)^d`.  If a parent has children of voltages
`w_1,...,w_k`, then

```text
v(parent)=epsilon_d+w_1+...+w_k.                    (1)
```

Write `P_j=w_1+...+w_j`.  At odd depth the events of a nonleaf parent
of base `b` are

```text
R_b, L_(b+P_1), ..., L_(b+P_(k-1)), R_(b+P_k),
```

and its child bases are

```text
b+1, b+1+P_1, ..., b+1+P_(k-1).
```

An odd-depth leaf contributes a single `L`.  At even depth interchange `R`
and `L`, and remove the `+1` from the child-base formula.  Events on one level
are ordered by decreasing base, with plane order breaking ties.  Exact stabilized
P3 requires the resulting word to be `RLRL...`.

Let `n=f_(d-1)`, `m=f_d`, and let `p` be the number of nonleaf parents at
depth `d`.  The level contains `n+m` events and has total turn excess
`omega=(n+m) mod 2`.  Counting endpoint and interior turns gives

```text
             n+m+omega
p =          ---------       at odd depth,
                 4

             n+m-omega
p =          ---------       at even depth.          (2)
                 4
```

Equations (1)--(2), the cap `m<=4`, and exact stable alternation make the first
four levels a finite/affine calculation.  The details follow so that no voltage
window or search output is being used as a proof.

#### Depth one

Equation (2) permits only `f_1=2` or `3`.

For `f_1=2`, sorting the events `R_0,L_a,R_2` forces `a=1`, hence

```text
B=(1,2),       V=(1,1).                               (3)
```

For `f_1=3`, write the two proper partial sums as `a,q`.  Exact alternation
forces exactly one of them to equal one and the other to be nonpositive.  With
`r<=0`, the complete two-family description is

```text
B=(1,2,1+r),   V=(1,r-1,2-r),
B=(1,1+r,2),   V=(r,1-r,1).                           (4)
```

#### Depth two

From (3), equation (2) permits `f_2=2` or `3`, with one nonleaf.
For `f_2=2`, only the first parent can be nonleaf and exact order forces

```text
B=(1,1),       V=(0,0).                               (5)
```

For `f_2=3`, sorting the five events gives exactly four families:

| bases `B` | voltages `V` | domain |
|---|---|---|
| `(1,1,1+r)` | `(0,r,-r)` | `r<=-1` |
| `(1,1+r,1)` | `(r,-r,0)` | `r<=-1` |
| `(2,2,2+r)` | `(0,r,-r)` | `r>=1` |
| `(2,2+r,2)` | `(r,-r,0)` | `r>=1` |

Indeed, if the first parent is nonleaf, its proper partial sums must be zero and
a strictly negative number; if the second parent is nonleaf, they must be zero
and a strictly positive number.  These are the four choices of which partial sum
is zero and which parent is nonleaf.

Now start instead from (4).  At even depth two every leaf has voltage `+1`, and
the permitted degree rows require two such leaves.  The first family in (4) never
has two.  The second has two only at `r=0`, giving the parent state

```text
B=(1,1,2),     V=(0,1,1),
```

with parent zero nonleaf.  If `f_2=1`, this produces

```text
B=(1),         V=(-1).                                (6)
```

If `f_2=2`, exact sorting gives

```text
B=(1,k),       V=(k-1,-k),       k<=-1.               (7)
```

There are no other depth-two states.

#### Depth three

State (5) needs an odd-depth leaf of voltage `-1` but has none, so it dies.
The same is true of (7): for `k<=-1`, neither `k-1` nor `-k` is `-1`.

For the four `f_2=3` families, equation (2) permits `f_3=1` or `4`.
The first choice requires two voltage-`-1` leaves and is impossible.  The second
requires exactly one leaf, so `|r|=1`.  Before placing the depth-three children,
the four resulting parent states are

| bases | voltages |
|---|---|
| `(1,1,0)` | `(0,-1,1)` |
| `(1,0,1)` | `(-1,1,0)` |
| `(2,2,3)` | `(0,1,-1)` |
| `(2,3,2)` | `(1,-1,0)` |

The first and fourth cannot alternate: the required insertion lies between
consecutive integer coordinates, while the plane tie order fixes the two adjacent
equal signs.  More explicitly, the fixed stable subsequences of the four states,
with coordinates shown as subscripts, are

```text
R_2 R_2 R_1 L_1 R_0,
R_2 R_2 L_1 R_1 R_0,
R_4 R_3 L_3 R_2 R_2,
R_4 L_3 R_3 R_2 R_2.
```

In the first state the second required `L` would have to lie strictly between
coordinates two and one; a tie occurs on the wrong side in plane order.  The
fourth state has the analogous unfillable gap from three to two.

In the second state both inserted `L` events must belong to the last parent, at
coordinates two and one.  Thus the degree row is `(0,1,3)` and that parent's
proper partial sums are zero and one, in either order, giving

```text
B=(1,2,2,3),   V=(2,0,1,0),
B=(1,2,3,2),   V=(2,1,-1,1).                          (8)
```

In the third state both inserted `L` events must belong to the first parent, at
coordinates three and two.  The degree row is `(3,1,0)`, and the same two orders
of proper partial sums zero and one give

```text
B=(3,3,4,3),   V=(0,1,0,2),
B=(3,4,3,3),   V=(1,-1,1,2).                          (9)
```

Finally, state (6) permits `f_3=2` or `3`.  The first forces proper partial sum
zero and produces

```text
B=(2,2),       V=(0,0).                               (10)
```

For `f_3=3`, one proper partial sum is zero and the other is strictly negative.
Writing the latter base as `k<=1` gives precisely

```text
B=(2,k,2),     V=(k-2,2-k,0),
B=(2,2,k),     V=(0,k-2,2-k).                         (11)
```

Thus (8)--(11) are the complete voltage-unbounded frontier after depth three.

#### Depth-four extinction

At even depth four, (2) gives the complete list of possible pairs
`(f_4, number of nonleaves)`:

| `f_3` | possibilities |
|---|---|
| `2` | `(2,1)`, `(3,1)` |
| `3` | `(1,1)`, `(2,1)` |
| `4` | `(1,1)`, `(4,2)` |

Every even-depth leaf has voltage `+1`.

- State (10) has no possible leaf.
- Each parametric state in (11) has at most one voltage `+1`, but needs two
  leaves.
- The first state in (8) and the first state in (9) have only one voltage `+1`,
  but need two or three leaves.

Only the second states of (8) and (9) remain, necessarily with `f_4=4` and two
nonleaves.

For `B=(1,2,3,2), V=(2,1,-1,1)`, parents zero and two are nonleaves.
At coordinate two, the fixed block consists of the final `L` of parent zero,
followed by the two leaf `R` events of parents one and three:

```text
L R R.
```

Every optional interior event at that coordinate is also `R`, so the block cannot
be part of an alternating word.

For `B=(3,4,3,3), V=(1,-1,1,2)`, parents one and three are nonleaves.
At coordinate three, the two leaf `R` events of parents zero and two precede the
starting `L` of parent three:

```text
R R L.
```

Again every optional event there is `R`.  This word cannot alternate either.
The exact frontier is therefore empty at depth four.

Since a primitive-diagonal finite-support periodic highway has `W>=10`, these
four levels always occur above its singleton bottom rail.  In fact the proof gives
the sharper boundary-local statement

```text
max(f_1,f_2,f_3,f_4) >= 5.
```

This proves the stated cap-four obstruction without bounding the period, width, or
subtree voltages.  Applying the same argument from the top rail gives a fat cut
within four levels of that boundary as well.

#### Independent checks and the remaining boundary

The symbolic classification was independently hand-audited.  A separate exact
frontier enumeration reproduces the depth-three table for voltage windows
`3,5,10,20`; the two unbounded families contribute exactly twice the window size,
the five remaining states are fixed, and the depth-four frontier is empty.  The
targeted regression is

```text
python code/python/audit_primitive_cap4_frontier.py
```

It imposes cut cap four and no wake budget.  The theorem is the unbounded algebraic
case split above, not an inference from the four finite voltage windows.

There is also an independent all-width cap-three profile identity.  If
`f_c<=3`, put

```text
z_c=(-1)^c(f_c-2).
```

Every nonwake level leaves `z` unchanged and every wake level raises it by one.
Indeed, a nonwake transition has `f_(c-1)+f_c=4`; the odd-level wake cases are
`1<->2`, and the even-level wake cases are `2<->3`.  Substitution in the definition
of `z` gives increments zero and one, respectively.  The singleton rails give
`z_0=-1` and `z_(W-1)=1`, so exactly two interior wake levels occur.  Each
singleton rail is itself one unmatched `R`, hence one wake class; the total growth
is therefore four.  This already excludes primitive growth eight under cap three;
the exact-P3 cap-four obstruction is stronger.

Neither argument controls a fat cut.  The unresolved primitive cases now satisfy

```text
max_c f_c >= 5.
```

Closing that unbounded branch, rather than extending a bounded table, is the next
required step toward `g>=12`.

<a id="source-research-notes-primitive-g4-cap3-analytic-2026-08-20-md"></a>

## primitive_g4_cap3_analytic_2026-08-20

Source: `research-notes/primitive_g4_cap3_analytic_2026-08-20.md`.

### Primitive-diagonal growth four under crossing cap three

Subsequent status: the unrestricted primitive-diagonal growth-four case is
excluded by the analytic reduction and computer-assisted affine classification
in [the top-boundary note](03_Growth_four.md#source-research-notes-primitive-g4-cap5-symbolic-2026-08-22-md). The
growth-eight cases remain open. The entries below preserve the earlier
checkpoint and its intermediate questions.

#### Status

This note proves an **analytic conditional exclusion**.  It does not prove the
unrestricted primitive-diagonal case, `g>=12`, or highway uniqueness.

Normalize a hypothetical primitive-diagonal growth-four trace to drift
`d=(1,-1)`, put its singleton bottom rail at transverse level zero, and let
`f_c` be the number of upward (equivalently downward) crossings of the cut between
levels `c` and `c+1`.  Assume

```text
f_c <= 3 for every transverse cut c.
```

Then the stabilized lower-prefix condition already fails whenever `W>=6`.
Since every finite-support diagonal highway has `W>=10`, no primitive-diagonal
growth-four highway can have crossing cap three.

The proof uses neither ordinary same-cell alternation nor the upper-prefix half of
the periodic-realisability criterion.  It is therefore an exclusion of a strictly
larger projected-tour class.

#### Tree state

The positive transverse excursion is the contour of a rooted plane tree.  At a
fixed depth, list the current nodes in contour order.  A state consists of

```text
(b_1,...,b_n)       longitudinal bases of the nodes,
(v_1,...,v_n)       horizontal voltages of their complete subtrees,
(e,o)               numbers of used interior even/odd wake levels.
```

At depth `t`, put `s_t=+1` for even `t` and `s_t=-1` for odd `t`.  If a node has
children of voltages `w_1,...,w_k`, then

```text
v = s_t + w_1 + ... + w_k.                         (1)
```

Thus a leaf at odd depth has voltage `-1`.  The turns made at an odd-depth node
are `R`, then one `L` between consecutive children, then `R`; an odd-depth leaf
contributes one `L`.  The even-depth statement has `R` and `L` interchanged.
At each level the events are ordered by decreasing longitudinal coordinate, with
phase order breaking ties.  The lower-prefix hypothesis says that every prefix of
that stable word has nonnegative `#R-#L`.

The line-parity laws and total growth four imply that there is one interior wake
level of each parity.  Together with `f_c<=3`, these facts leave only finitely many
degree patterns at each of the first four depths.

#### Four-level classification

Starting from the bottom state `((0),(1),0,0)`, apply (1), the cap, the one-wake-
per-parity budget, and the lower-prefix condition through depth four.  A direct
finite case split gives exactly the following five affine families.  Translation
of all bases has already been fixed by the bottom rail.

| cut prefix `(f_1,f_2,f_3,f_4)` | bases at depth 4 | voltages at depth 4 | wake budget `(e,o)` | parameter domain |
|---|---|---|---|---|
| `(3,1,2,2)` | `(2,b)` | `(b-2,-b)` | `(0,1)` | `b>=3` |
| `(3,1,2,3)` | `(2,b,c)` | `(b-2,c-b,-c)` | `(1,1)` | `max(b,c)>=3` |
| `(3,1,3,2)` | `(2,b)` | `(b-2,-b-1)` | `(1,0)` | `b>=3` |
| `(3,2,1,3)` | `(2,b,c)` | `(b-2,c-b,2-c)` | `(1,1)` | `b,c>=2` and `(b,c)!=(2,2)` |
| `(3,2,2,2)` | `(2,b)` | `(b-2,1-b)` | `(1,0)` | `b>=3` |

For completeness, the corresponding degree rows through depth four are

```text
(3),(1,0,0),(2),(2,0)
(3),(1,0,0),(2),(3,0)
(3),(1,0,0),(3),(2,0,0)
(3),(2,0,0),(1,0),(3)
(3),(2,0,0),(2,0),(2,0),
```

respectively.  This makes the table a short algebraic check rather than an
unbounded enumeration: substitute the degree row in (1), write the child bases as
successive partial voltage sums, and compare the at most seven level events.  The
nonnegative Catalan words of the required lengths give exactly the displayed
parameter domains.  In particular, every lower-prefix branch with `f_c<=3` is in
the table; no bound on `b`, `c`, the period, or the width is used.

The width-four positive control is not lost in this reduction.  It closes one
depth earlier, with cut profile `(1,3,2,1)` and stabilized level words
`R, RLRL, RLRRL, RRL, R`.

#### Fifth-level obstruction

At depth five, every possible continuation under the cap has exactly one nonleaf
parent.  Consequently every other parent must be a leaf and, by (1), must have
voltage `-1`.

In the first, third and fifth rows of the table there are two parents, but neither
displayed voltage can equal `-1` in the stated parameter domain.  Those families
cannot continue.

In the second row there are three parents.  Requiring two of

```text
b-2, c-b, -c
```

to equal `-1` gives only

```text
(b,c)=(1,0), (1,1), (2,1),
```

all excluded by `max(b,c)>=3`.

In the fourth row, requiring two of

```text
b-2, c-b, 2-c
```

to equal `-1` leaves only the admissible point `(b,c)=(4,3)`.  The state there is

```text
bases    (2,4,3),
voltages (2,-1,-1).
```

The first parent is the unique nonleaf.  Its two `R` endpoints have coordinates
`2` and `5`, while the two leaves contribute `L` at coordinates `4` and `3`.
Stable decreasing-coordinate order is therefore

```text
R(5), L(4), L(3), R(2),
```

namely `RLLR`; its third prefix has charge `-1`.  This last continuation also
fails.  Hence no lower-prefix state reaches depth five.

#### Consequence and boundary

Every width at least six contains these first five levels above the bottom rail,
so the obstruction is width-uniform:

> **Conditional theorem.**  No primitive-diagonal growth-four finite-support
> periodic highway can satisfy `f_c<=3` on every transverse cut.

This upgrades the earlier bounded rows `W=6,8,10,12,14` to an analytic all-width
conditional theorem.  It still does not touch the literal period-62 near-model
whose profile contains `f_c=9`. At this checkpoint, the unrestricted problem was to
control a fat cut (`f_c>=5`, since the line-parity law forbids `f_c=4` in the
relevant interior regime), or to derive a different contradiction that does not
bound the crossing profile.

<a id="source-research-notes-primitive-g4-cap5-symbolic-2026-08-22-md"></a>

## primitive_g4_cap5_symbolic_2026-08-22

Source: `research-notes/primitive_g4_cap5_symbolic_2026-08-22.md`.

### Primitive diagonal growth four: the top-boundary obstruction

#### Status

This note proves that no finite-support periodic highway of growth four has
primitive diagonal drift. The proof combines an analytic reduction with
computer-assisted verification of the remaining affine cases. It has no period
or voltage bound. Normalize the drift to `d=(1,-1)`, put the singleton bottom rail at
transverse level zero, and let `f_c` be the number of crossings in either
direction through the cut between levels `c` and `c+1`.

The earlier computer-assisted part of the note remains useful as a separate
boundary check.  It proves

```text
max(f_1,f_2,f_3,f_4,f_5) >= 6.                       (1)
```

and the analogous inward statement at the top rail.  The top calculation is
sign-reversed in the original longitudinal coordinate; it is not inferred from
a bare spatial reflection. The top-boundary argument below goes farther: its first
three top-rooted rows leave no possible continuation.  Together with the earlier
axis and even-diagonal theorems, this closes every growth-four drift family.
Growth eight remains open, so the bound `g>=12` is not proved.

#### The finite symbolic reduction

At depth `d`, write `n=f_(d-1)` for the number of frontier nodes, `m=f_d` for
their children, and `p` for the number of nonleaf nodes.  Exact stable
alternation gives

```text
4p = n+m+omega     if d is odd,
4p = n+m-omega     if d is even,                         (2)
```

where `omega=(n+m) mod 2`.  Growth four leaves one interior wake level of each
parity.

Assume, contrary to (1), that the first five cuts are at most five.  The cap-four
theorem puts a cut of size five among the first four.  Its first occurrence
cannot be `f_1`: substituting `(n,m)=(1,5)` in (2) gives no integer `p`.
Therefore the first five occurs at depth `j=2`, `3`, or `4`.

The next row has five nodes and at most five children.  Equation (2) gives at
most two nonleaves, so at least three of the five node voltages are fixed leaf
voltages.  The voltage of the depth-one node is one.  After the fixed leaves are
substituted, this root equation leaves at most one free integer parameter among
the remaining voltages.  Every base, endpoint, and earlier event coordinate is
therefore an affine function of one integer.

The primary enumeration checks every cut prefix, every ordered degree row, every
legal placement of the terminal leaves, and every integer order regime of those
affine coordinates.  Coordinate order can change only where two affine functions
are equal, so the complete unbounded check is finite: it evaluates the equality
points that are integral, one integer in every nonempty interval between
successive rational equality points, and both tails.

Earlier rows are required to equal `RLRL...` after sorting by decreasing base,
with contour order breaking ties.  On the terminal row the test is weaker.  It
keeps only leaf turns and the two endpoints of each nonleaf, then asks whether
that fixed word is a subsequence of the required alternating word.  The omitted
interior turns may be inserted anywhere.  Failure of this relaxed test rules out
the actual row.

#### Exhaustive table

There are 1,320 cut/degree/leaf cases.  Exact order on the earlier rows reduces
them to the following nine regimes.  `B` and `V` are the terminal bases and
voltages in plane order.

| cut prefix | next cut | `B` | `V` | fixed word | target |
|---|---:|---|---|---|---|
| `(2,3,5)` | 3 | `(1,2,3,1,2)` | `(2,1,-2,1,1)` | `LLRRLRL` | `RLRLRLRL` |
| `(2,3,5)` | 3 | `(3,4,2,3,3)` | `(1,-2,1,1,2)` | `LLRRLRL` | `RLRLRLRL` |
| `(3,1,3,5)` | 2 | `(2,1,3,2,2)` | `(-1,2,-1,-1,-2)` | `RLLLRRR` | `RLRLRLR` |
| `(3,1,3,5)` | 3 | `(2,1,3,2,2)` | `(-1,2,-1,-1,-2)` | `RLLLRRR` | `RLRLRLRL` |
| `(3,2,5)` | 3 | `(2,-1,0,1,2)` | `(-2,1,1,1,0)` | `LLRLRLR` | `RLRLRLRL` |
| `(3,2,5)` | 3 | `(2,1,2,0,1)` | `(-1,1,-1,1,1)` | `LLRRLLR` | `RLRLRLRL` |
| `(3,2,5)` | 3 | `(2,2,-1,0,1)` | `(0,-2,1,1,1)` | `LLLRRLR` | `RLRLRLRL` |
| `(3,5)` | 2 | `(1,0,0,1,0)` | `(-1,-1,1,-1,1)` | `RRLLLRR` | `RLRLRLR` |
| `(3,5)` | 3 | `(1,0,0,1,0)` | `(-1,-1,1,-1,1)` | `RRLLLRR` | `RLRLRLRL` |

None of the fixed words is a subsequence of its target.  Five rows begin with
`L`; each remaining row contains an unrepairable block of equal turns.  Thus all
1,320 cases fail.

At the top rail, inward depth is `d=T-t` and the original `x` coordinate is
retained.  The nonroot self voltage is `(-1)^(d+1)`, and entering a child shifts
`x` by `-1` at odd depth and by zero at even depth.  Stable events are still
ordered by decreasing `x`.  The same 1,320 structural cases leave only two
exact source regimes:

| cut prefix | next cut | `B` | `V` | fixed word | target |
|---|---:|---|---|---|---|
| `(3,5)` | 2 | `(-2,-1,0,1,-1)` | `(2,1,1,-2,1)` | `RLRLLRR` | `RLRLRLR` |
| `(3,5)` | 3 | `(-2,-1,0,1,-1)` | `(2,1,1,-2,1)` | `RLRLLRR` | `RLRLRLRL` |

Neither fixed word embeds in its alternating target, so the top calculation
also has zero survivors.

##### Analytic top-adjacent cut

The sign-reversed conventions also give a short computation-free consequence.
Let `u` be the unique depth-one node below the top rail, normalized by
`b(u)=0` and `v(u)=1`.  The level count permits only two or three children.
Suppose there are two, with voltages `z_1,z_2`.  The depth-one voltage recurrence
gives `z_1+z_2=0`, while the three depth-one events occur at

```text
x=0, z_1, 0        with turns R,L,R.
```

Decreasing-`x` alternation is possible only when `z_1=z_2=0`.  Both children
then have base `-1`.  At even depth a leaf has voltage `-1`, so these two
zero-voltage children are nonleaves.  Each contributes fixed `L` endpoints at
`x=-1` and `x=0`.  In stable order the four anchors are

```text
end_1, end_2, start_1, start_2.
```

No event can occur between `end_2` at zero and `start_1` at minus one: coordinates
are integral, `end_2` is the last contour event at its coordinate, and `start_1`
is the first at its coordinate.  They are therefore consecutive `L` turns, a
contradiction.  Thus the first inward cut at the top has multiplicity exactly
three.  Write the three child voltages as `z_1,z_2,z_3`.  Their sum is zero, and
the depth-one event coordinates and turns are

```text
(0,R), (z_1,L), (z_1+z_2,L), (0,R).
```

Exact order forces exactly one proper partial sum to be zero and the other to be
an integer `r<0`.  Consequently the depth-two frontier is in one of the two
families

```text
B=(-1,-1,-1+r), V=(0,r,-r),
B=(-1,-1+r,-1), V=(r,-r,0),                 r<=-1.       (3)
```

For three nodes on the next even row, the complete count-law list of possible
child counts is `1,2,5,6,9,10`.  Counts one and two would leave two leaf parents,
but an even-depth top leaf has voltage `-1`, and either family in (3) contains at
most one such voltage.  Counts nine and ten make all three parents nonleaves.
In either family the last parent ends at `x=0` and the first parent starts at
`x=-1`; these are `L` anchors, and no integral-coordinate event can separate
them.  Those cases also fail.  Thus the first two inward cuts are

```text
(f_1,f_2)=(3,5) or (3,6).                         (4)
```

In both surviving cases the unique even-depth leaf forces `r=-1`, and only the
second family in (3) survives.  The three current nodes therefore have

```text
B=(-1,-2,-1), V=(-1,1,0),
```

with the first node the leaf.  Let the two nonleaf degrees be `a,b`, and write
their successive event coordinates as

```text
q_0=-2,...,q_a=0,       r_0=-1,...,r_b=0.
```

For `f_2=5`, either

```text
a=1: (r_1,...,r_(b-1)) is a permutation of (alpha,0,-1), alpha>=1;
a=2: q_1=alpha>=0 and (r_1,...,r_(b-1)) permutes (0,-1).
```

For `f_2=6`, either

```text
a=1: the proper r-coordinates permute (alpha,0,-1,beta), alpha>=1, beta<=-2;
a=2: q_1=alpha>=0 and r permutes (0,-1,beta), beta<=-2,
     or q_1=beta<=-2 and r permutes (alpha,0,-1), alpha>=1;
a=3: (q_1,q_2) permutes (alpha,beta), alpha>=0, beta<=-2,
     and (r_1,r_2) permutes (0,-1).
```

These conditions are necessary and sufficient for exact order on this even
row: successive coordinate differences define the child voltages.  For example,
`f_2=6`, degrees `(0,1,5)`, `q=(-2,0)` and
`r=(-1,-3,-1,0,1,0)` give the exact child frontier

```text
B'=(-2,-1,-3,-1,0,1), V'=(2,-2,2,1,1,-1).
```

Its stable row is `RLRLRLRLR`, so the six-branch is genuinely locally
realisable.

##### The third inward cut

The affine forms settle the entire next row, not only its smallest values.
For `f_2=5`, write the eight forms as

```text
I:  q=(-2,0),       r=(-1, pi(alpha,0,-1), 0),  alpha>=1, pi in S_3;
II: q=(-2,alpha,0), r=(-1, pi(0,-1), 0),        alpha>=0, pi in S_2.
```

The odd-row count and leaf numbers are

```text
f_3:        2 3 6 7 10 11 14 15
p_3:        2 2 3 3  4  4  5  5
leaf count: 3 3 2 2  1  1  0  0.
```

Put `S_i=b_i` and `E_i=b_i+v_i-1` for the first and last fixed `R` anchors of a
nonleaf on this odd row.  Two gaps recur throughout the case split.

* If nodes zero and four are nonleaves, `E_4` is the final contour event at
  `x=-1`, while `S_0` is the first at `x=-2`.  They are consecutive in stable
  order: no integer coordinate lies between them, and neither tie side contains
  a phase slot for the required `L`.
* In type I, `E_0=S_1=-1`; in type II, `E_1=S_2=-1`.  When the indicated pair is
  nonleaf, these are again consecutive `R` anchors, now at the same coordinate
  and at consecutive contour phases.

For `p_3=2`, the leaf equations leave one state,

```text
B=(-2,-1,0,1,-1), V=(2,1,1,-2,1),
```

with nonleaf support `{0,3}` and fixed word `RLRLLRR`.  For `p_3=3`, every
support containing node four dies by the first gap.  The remaining type-II
order has support `{0,1,3}` and leaves `{2,4}`; the remaining generic type-I
order has support `{0,2,3}` and leaves `{1,4}`.  Both have fixed word
`RRRRLLRR`.  At `alpha=1`, the additional type-I support `{0,1,3}` dies by the
second gap.  For `p_3=4`, node four must be the sole leaf.  The only compatible
orders are type I ending in `-1` and type II ordered `(0,-1)`; each has the
second empty gap.  For `p_3=5`, all nodes are nonleaves and the first gap applies
immediately.  Every omitted interior event is `L`, so neither a fixed `LL` nor
an empty slot between consecutive `R` anchors can be repaired.  Thus the entire
`f_2=5` branch is impossible.

For `f_2=6`, the count law gives

```text
f_3: 2 5 6 9 10 13 14 17 18
p_3: 2 3 3 4  4  5  5  6  6.
```

The four-leaf case `f_3=2` has the unique fixed word `RLRLLRLR`.  For `f_3=5`
or `6`, solving the three leaf equations in all forty affine forms leaves five
parameter branches.  Their complete fixed-word set is

```text
RLRLLRRRR, RRRRLLRLR, RLRRRLRLR, RLRLRRRLR, RLRRLRRLR.
```

The first two contain fixed `LL`.  In each remaining word a missing `L` would
have to lie between a specified pair of consecutive `R` anchors: either two
anchors at `x=-1` with consecutive contour phases, or the final anchor at
`x=-1` followed by the first at `x=-2`.  No integer stable key occupies the
required gap.

It remains to check the larger counts.  Node zero is never a leaf in any of the
forty normal forms: its voltage is `2`, `alpha+2`, or `beta+2`, with the stated
parameter domains.  If node five is a nonleaf, its final `R` at `x=-1` and node
zero's first `R` at `x=-2` form the first empty gap above.  Hence:

* for `f_3=17,18`, where all six nodes are nonleaves, the first gap is already a
  contradiction;
* for `f_3=13,14`, the sole leaf must be node five, leaving both nodes at the
  `q/r` block junction nonleaf; their endpoint and start are consecutive `R`
  anchors at `x=-1`;
* for `f_3=9,10`, the two leaves must be node five and one junction node.  The
  leaf equations leave six affine coordinate orders.  In all six the leaves
  are the first `r` node and node five, both at `x=-1`, with no fixed `R` between
  them.  The compressed word is `RRRRLLRRRR`.

Thus `f_2=6` has no continuation either.  A primitive growth-four trace has four
distinct wake levels.  The two extremal levels use two of them, so its even
width is at least four and the three inward rows considered above exist.  The
top-rooted case tree is therefore empty: primitive-diagonal growth four is
impossible at every period.

The reduction is analytic and period-unbounded. Its final exhaustive affine
verification is computer-assisted. The script
`code/python/audit_primitive_g4_top_prefix.py` enumerates the 8 and 40 affine
forms, solves the unit-voltage equations exactly, partitions every remaining
integer parameter line at every base/endpoint gap crossing, and performs exact
integer-gap matching for the omitted events.  It also checks the two
parameter-free endpoint obstructions for the large cuts.  It uses no voltage
bound.  The checked summary and source hash are in
`results/primitive_g4_top_prefix_certificate.json`.

The reproduction and audit commands are:

```text
python code/python/primitive_g4_cap5_symbolic.py
python code/python/verify_primitive_g4_cap5_indep.py
python code/python/verify_primitive_g4_cap5_top.py
python code/python/audit_primitive_g4_cap5.py
python code/python/audit_primitive_g4_top_prefix.py
```

The verifier does not import the primary program.  It constructs affine pairs
directly, derives the terminal voltage sum from the root equation, and builds
the integer order cells from exact rational crossing points.  Both programs
report 1,320 cases, nine regimes, and zero survivors, and they print the same
nine bottom rows above.  The separate top verifier reports 1,320 cases, the two
top regimes above, and zero survivors.  The cross-audit checks all three source
hashes and both certified tables.

Because the established width bound is `W>=10`, five inward levels exist from
either rail.  The bottom and top calculations use their respective signed tree
recurrences; no reflection symmetry is assumed.  No period, width, or voltage
cutoff enters either enumeration.

<a id="source-research-notes-primitive-g4-research-2026-08-20-md"></a>

## primitive_g4_research_2026-08-20

Source: `research-notes/primitive_g4_research_2026-08-20.md`.

### Primitive-diagonal growth four: exact chronology frontier (20 August 2026)

Subsequent status: the unrestricted primitive-diagonal growth-four case is
excluded by the analytic reduction and computer-assisted affine classification
in [the top-boundary note](03_Growth_four.md#source-research-notes-primitive-g4-cap5-symbolic-2026-08-22-md). The
growth-eight cases remain open. The entries below preserve the earlier
checkpoint and its intermediate questions.

#### Status

This note continues `line_parity_research_2026-08-18.md`. It does **not** prove
`g>=8`, `g>=12`, or uniqueness of the standard highway.

What is proved before this note:

- diagonal periodic highways have even transverse width `W>=10` (the exclusions
  at widths four, six and eight are computer-assisted all-period results);
- axis and even-diagonal growth-four drift are impossible at every period;
- for primitive drift `d=(1,-1)` and growth four, the four wake levels split
  `3` horizontal to `1` vertical and `N=6 (mod 8)`;
- the extremal levels are singleton right-turn rails, and the adjacent level has
  the forced arrival strings recorded in the 18 August note.

At this checkpoint, primitive-diagonal growth four was the only remaining
`g=4` family. Every `g=8` geometry remains open.

#### Stable prefix charge

For one transverse class, order its period events by the stabilised key

```text
tau_i = i - N x_i                       (d=(1,-1)).
```

For the resulting turn word define the prefix charge

```text
q(k) = #R in the first k events - #L in the first k events.
```

The stabilised-word part of the exact finite-support criterion is

```text
q(k) in {0,1} for every k, with q(0)=0.
```

Equivalently, the word is `R,L,R,L,...`. The full criterion also includes its
finite partial-class conditions. The lower inequality `q(k)>=0` is the
right-before-matching-left (black-lifetime) half; the upper inequality `q(k)<=1`
is the left-before-next-right (white-lifetime) half. Neither half may be silently
replaced by a sum over the class: earlier exact countermodels have all class sums
nonpositive while retaining positive individual arcs.

#### Exact countermodel to the upper-half-only route

The word

```text
RRRRRRLRLRLLRRRLLLLLRLRRLLRRLLRRRLLLLRLLLRLRRRRRRLRRLL
```

with initial heading north has:

```text
N = 54
endpoint = (1,-1)
heading reset = yes
growth = 4
transverse width W = 10
extremal levels = -7,3, both singleton
odd/excess-one levels = {-7,-5,2,3}, with the required 3-to-1 parity split
every class excess in {0,1}
```

Every intended left-to-next-right lifted-time inequality holds: in prefix language,
`q(k)<=1` in every stabilised class. Nevertheless the word is not finite-support
realisable: it fails full P3 and ordinary same-cell alternation. More precisely,
nine within-period cells are defective, containing eleven adjacent
equal-turn pairs. It is therefore a **near-model, not a highway**, and proves that the upper half alone
cannot follow from the counting laws, singleton rails, endpoint, and one-tour
geometry.

The complementary lower-half route has survived stronger hostile searches that also
imposed ordinary same-cell alternation, but only as bounded evidence. Double-swap
searches reached candidates with two ordinary alternation defects and six negative
prefix defects; no exact lower-half model was found. This is not a theorem and no
absence claim should be promoted.

A separate 20 August hill-climb put ordinary same-cell defects directly into the
objective. Its best exact structural point had `W=12`, one ordinary defect, and nine
negative-prefix defects; it found no zero-defect countermodel before the bounded run
was stopped. This is a different Pareto point, not stronger absence evidence, and
the scratch search is not a released certificate.

Small-period checks also delimit its scope. At `N=14`, one physically alternating
primitive structural word satisfies every lower prefix inequality, and at `N=22`
one satisfies every upper prefix inequality. Both have width below ten. Any viable
one-sided theorem must therefore use the proved `W>=10` barrier, not merely primitive
growth four and ordinary same-cell alternation.

#### Standard-highway deletion counterexample

The standard period-104 highway itself rules out a general pose-factor deletion
lemma. In one unwrapped period there are 36 proper same-heading factors whose
displacement is the full `(2,-2)`. None of the 36 repeated factors passes the exact
finite-support criterion. Only one complementary zero-pose factor is the word
`RRRR`; the other complements have lengths from 8 to 100 and arbitrary turn words.
Hence neither “the boundary factor has an `RRRR` cap” nor “delete a zero-displacement
pose loop and inherit P3” is valid without a new, much stronger separation theorem.

#### Narrowest viable next theorem

The remaining proof target must retain literal same-cell chronology, lifted class
order, and the proved width barrier. A useful sufficient contradiction would be:

> In every heading-reset, single-tour primitive-diagonal growth-four trace with
> `W>=10`, singleton extremal rails, and ordinary same-cell alternation, some
> stabilised class has a prefix with `q(k)<0`.

Proving instead that some prefix has `q(k)>1` would also work, but the exact
upper-half countermodel makes that direction less plausible. Aggregate class
voltages, start-only or end-only conditions, deletion inheritance, and a bounded
offset transfer matrix have all been falsified and should not be revisited without
new input.

#### A proved Dyck reduction for the lower half

There is a useful exact reduction that does not solve the remaining problem.  Put

```text
delta_t = #R_t - #L_t
```

for a complete stabilised level word, and let `omega_t` be its odd-class indicator.
The per-level mod-four theorem gives `delta_t = omega_t (mod 4)`.  If every prefix
charge is nonnegative, then in particular `delta_t>=0`.  Since

```text
sum_t delta_t = growth = 4 = sum_t omega_t,
```

every nonnegative difference `delta_t-omega_t`, being divisible by four, must
vanish.  Therefore

```text
delta_t = omega_t  for every level t.
```

Thus every even class word is a Dyck word, and every odd class word is a Dyck
prefix ending at height one.  This is a proved consequence of the lower half, not a
computational observation.  It converts the remaining chronology question into a
simultaneous Catalan-order problem on all transverse levels.

#### Crossing cap three: analytic all-width conditional exclusion

The restriction `f_c<=3` is not automatic, but within it the counting layer is
completely explicit.  Normalize the unique bottom rail to level zero.  If the two
interior wake levels are the even (horizontal-arrival) level `h` and odd
(vertical-arrival) level `v`, then the level multiplicities are one on the rails,
five at `h`, three at `v`, and four elsewhere.  The recurrence

```text
f_t = m_t - f_{t-1},   f_0=1
```

determines the whole crossing profile.  Before imposing the endpoint there are
`(W/2)(W/2-1)` weak profiles.  The endpoint identity

```text
y = sum_c (-1)^c f_c = -1
```

is equivalent to `h+v=W+1`; hence exactly `W/2-1` profiles remain, all with
`N=4W-2`.  This profile classification is analytic.

The earlier bounded computation has now been replaced by an all-width analytic
argument.  Encode the positive transverse excursion as the contour of a rooted
plane tree.  A frontier node records its longitudinal base and the horizontal
voltage of its complete subtree.  If the frontier is at depth `t`, put
`s_t=+1` for even `t` and `s_t=-1` for odd `t`; a parent with child voltages
`w_1,...,w_k` has

```text
v=s_t+w_1+...+w_k.
```

The cap, the one-wake-per-parity budget, and the lower-prefix condition leave
exactly five affine frontier families after four levels:

```text
profile       bases       voltages             budgets       domain
3,1,2,2       2,b         b-2,-b               0,1           b>=3
3,1,2,3       2,b,c       b-2,c-b,-c           1,1           max(b,c)>=3
3,1,3,2       2,b         b-2,-b-1             1,0           b>=3
3,2,1,3       2,b,c       b-2,c-b,2-c          1,1           b,c>=2, not both 2
3,2,2,2       2,b         b-2,1-b              1,0           b>=3
```

At the fifth level every cap-three continuation has exactly one nonleaf parent,
so every other parent must have leaf voltage `-1`.  The first, third, and fifth
families have no such leaf; the second has no admissible pair of them.  The fourth
has one candidate, `(b,c)=(4,3)`, but its stable word is `RLLR`, whose third
prefix is negative.  Hence no branch reaches the fifth interior level.  The full
case split, including the corresponding degree rows, is recorded in
`primitive_g4_cap3_analytic_2026-08-20.md`.

Therefore no primitive-diagonal growth-four periodic highway with `W>=6` can have
`f_c<=3` on every transverse cut.  Since the proved width bound is `W>=10`, this
excludes the cap-three regime for all periods and widths.  The proof deliberately
uses neither ordinary same-cell chronology nor the upper-prefix half of the
periodic-realisability criterion.

The two separately structured projected-tour enumerators remain useful independent
bounded corroboration and a width-four positive control:

```text
W    weak profiles    raw tours    endpoint/growth    q>=0
4          2               24               6          1
6          6              360              60          0
8         12            3,888             498          0
10        20           37,584           4,008          0
12        30          347,976          32,430          0
```

The width-four survivor is the known positive control
`LLLRLRRRRLRRRR` in the north-facing phase, with profile `(1,3,2,1)` and stable
level words

```text
R, RLRL, RLRRL, RRL, R.
```

At width six, exactly seven endpoint/growth tours keep levels zero through three
Dyck; all seven first fail at level four, with word `LRRRL`, `LRRL`, or `LLLL`.
The affine frontier proof explains this first failure uniformly, without bounding
the longitudinal offsets, period, or width.

Reproduction:

```text
python code/python/primitive_g4_projected_tours.py --max-width 12 --assert-known
python code/python/verify_primitive_g4_projected_indep.py --max-width 12
python code/python/audit_primitive_g4_projected.py
results/primitive_g4_projected_w12.json
```

The table is a **bounded computer-assisted cross-check** of the analytic conditional
theorem.  The theorem still says nothing about an unrestricted profile with a fat
cut.  In the relevant interior regime the line-parity law rules out `f_c=4`, so the
remaining branch has some `f_c>=5`.

#### A literal fat-profile near-model

Ordinary same-cell alternation alone is not the missing theorem.  A direct search
over finite initial colourings found the north-facing word

```text
LRRLRLRLRRRRLRLLRLLRLRRRRLLLLRLRRRRLLLLRLRRLRLLRRRRLLRLLLLRRRR
```

with the following independently replayed data:

```text
N=62, endpoint=(1,-1), heading restored, growth=4, W=10,
crossing profile=(1,3,5,2,3,9,3,1,3,1),
singleton bottom and top rails, four class excesses equal to one,
ordinary same-cell defects=0.
```

It is a literal one-period Langton trace from a finite initial colouring, not merely
an abstract turn word.  It is nevertheless not a highway certificate.  Its total
negative lower-prefix depth is seven, on four levels:

```text
t=-1: RLLRLRLR
t= 1: LRRLR
t= 4: LRLR
t= 5: LRRL
```

The largest crossing number is nine, so the example also shows exactly why the
cap-three computation cannot be promoted to the general primitive case.  An
exhaustive tape-bit neighbourhood through radius four visited 410,847 finite
colourings and found no exact structural point with a smaller lower deficit; this
last sentence is local search evidence only.

#### Failed spatial-chain/connectivity interpretation

The lower condition `q(k)>=0` defines nonnegative black-lifetime intervals on the
disjoint union of lifted class-time lines. It does **not** make the projected
one-period ant curve the boundary of a nonnegative finite spatial 2-chain. The
period curve has homology one on the translation cylinder, whereas every finite
2-chain boundary is null-homologous. Subtracting any of the canonical straight
single-cut cylinder generators does not repair the sign problem: the literal
primitive word `LLLRLRRRRLRRRR` has ordinary same-cell alternation and nonnegative
stable prefixes, but every relative filling in that canonical family has both
positive and negative coefficients. This statement is deliberately not made for
an arbitrary homologous representative (choosing the period curve itself would
make the difference zero).

Connectivity also does not transfer to net growth. In that word the four stable
wake representatives have two Tait components, while the seven positive toggles
form one spanning component and three negative toggles reduce the net growth to
four. The genuine standard highway is decisive at `W=10`: full P3 holds, yet its
twelve canonical strand bases form four Tait components, and its 22 positive
one-period toggles form five components before ten removals. The dynamically shed
twelve-edge tree is a different, phase-aligned object containing carried widget
edges. Consequently neither stable representatives nor positive toggles support a
connectivity bound on `g`; the representative choice is also gauge-dependent under
shifts by the drift. Do not infer `g>=W/2+2` from `q>=0`.
