# Foundations and exact identities

These notes retain their original dates and hypotheses. Later status
pointers distinguish superseded checkpoints from the current report.
Individual source files and linked records are preserved in
[research_notes_sources.zip](research_notes_sources.zip).

## Contents

- [axis_two_exit_cycles_2026-09-03](#source-research-notes-axis-two-exit-cycles-2026-09-03-md)
- [cylinder_exit_cycles_2026-09-03](#source-research-notes-cylinder-exit-cycles-2026-09-03-md)
- [first_entry_detour_charges_2026-09-04](#source-research-notes-first-entry-detour-charges-2026-09-04-md)
- [highway_research_note](#source-research-notes-highway-research-note-md)
- [line_parity_research_2026-08-18](#source-research-notes-line-parity-research-2026-08-18-md)

<a id="source-research-notes-axis-two-exit-cycles-2026-09-03-md"></a>

## axis_two_exit_cycles_2026-09-03

Source: `research-notes/axis_two_exit_cycles_2026-09-03.md`.

### Four-vertex exit cycles at axis drift two

For drift `(2,0)`, every last-exit cycle consists of the two translation
classes on each of two adjacent rows.  Starting at the lower vertical-arrival
class, its selected edge directions are

```text
E,N,E,S.
```

Every first-departure cycle also uses four vertices on adjacent rows, but
its selected directions are `W,N,W,S`, with voltage `-1`.

For a last-exit cycle, the one-period decomposition from
`cylinder_exit_cycles_2026-09-03.md` becomes

```text
N = 4 + D_1+D_2+D_3+D_4,       D_i in 4 Z_(>=0).
```

The `D_i` are actual closed return excursions, not unspecified paths with
only prescribed displacement.  At growth eight, the known period condition
`N=4 mod 8` also makes their total divisible by eight.

First-visit order gives a second reduction: every trace has a row with two
coupled closed returns of positive lengths summing to `N`.  Their signed
changes add to one period's change with one explicit root correction.

This reduction holds at arbitrary period and transverse height.  It does not
give a bound on the wake contributed by the four excursions, so the axis
growth-eight case remains open.

#### Why only two rows occur

A row has exactly one vertical-arrival class `Q_y` and one horizontal-arrival
class `C_y` modulo `(2,0)`.  Every departure from `Q_y` goes horizontally to
`C_y`.  Every departure from `C_y` goes vertically to `Q_(y-1)` or `Q_(y+1)`.
The visit multiplicities of `Q_y` and `C_y` are equal, since horizontal steps
give a bijection from the occurrences of the former to those of the latter.
Under P3, their wake indicators are therefore equal as well.

In either selected exit graph, contract the selected `Q_y -> C_y` edges.
A directed cycle becomes a simple nearest-neighbor cycle on the row line.
Such a cycle must be `y -> y+1 -> y`: at its greatest row, its predecessor
and successor would otherwise repeat the same smaller row.  Restoring the
contracted edges gives four distinct quotient vertices.

The last-exit cycle has voltage `+1` by the cylinder theorem.  Its two
horizontal steps must therefore both be east.  The vertical steps are north
from the lower row and south from the upper row, proving the stated form.

These are geometric edge directions, not a list of the actual selected
incoming headings.  For example, the cycle's east edge may reach `C_y`
before its last visit, which may instead have a west incoming heading.
Consequently the lower cycle row has not been proved non-wake in general,
nor the upper cycle row wake.  That conclusion will hold below only when
the cycle row is an actual extreme of the whole trace.

#### Horizontal first/last matching inequalities

Choose representatives `Q=(r,y)` and `C=(1-r,y)`, where `r` is zero or one.
The horizontal voltages from `Q` to `C` are

```text
lambda(E)=r,       lambda(W)=r-1.
```

For first visits, let `u` indicate that the edge leaving first `Q` is east,
and let `z` indicate that the edge entering first `C` is east.  The latter
edge comes from an occurrence of `Q`, which need not be its first.  If the
first lifted times are `F_Q,F_C`, extremality at each endpoint gives

```text
F_Q+1-N(r-1+z) <= F_C <= F_Q+1-N(r-1+u).
```

Since `N>0`, this requires `u<=z`.  Repeating the argument with last lifted
times gives

```text
T_Q+1-N(r-1+u) <= T_C <= T_Q+1-N(r-1+z),
```

now requiring `u>=z`.  Equality of the two direction indicators forces
equality of the bounds.  In that case the selected `Q` departure lands
directly at the selected `C` visit.

There is a precise alternative in the strict cases.  For first visits the
only mismatch is outgoing west and incoming east.  Let `delta_Q` be the
time from first `Q` to the `Q` occurrence feeding first `C`, with physical
copies aligned.  Let `delta_C` be the time from first `C` to the arrival of
the first `Q` west edge.  Both are positive closed-return lengths, and
subtracting the voltage equations gives

```text
delta_Q+delta_C=N,       delta_Q,delta_C in 4 Z_(>0).
```

For last visits the only mismatch is outgoing east and incoming west.  The
corresponding lengths run from the `Q` occurrence feeding last `C` to last
`Q`, and from the last `Q` east-edge arrival to last `C`.  They obey the same
identity.  In particular, a strict mismatch cannot be treated as an exact
matching of the selected visits.

#### First-departure cycles go backward

The two-row reduction applies to first-departure cycles as well.  At the
lower row of such a cycle, the selected `C` edge goes north.  The selected
visit is a first visit and turns right, so its actual incoming heading is
west.  Thus `z=0`, and the first matching inequality forces `u=0`: the
lower horizontal cycle edge is west.

If the upper horizontal edge were east, the geometric cycle would have
directions `W,N,E,S`.  It would be a clockwise unit square with voltage
zero.  At a sufficiently future physical copy, each corner's first visit
turns right along its selected square edge.  Its predecessor must therefore
be the previous corner.  The earliest first visit among the four corners
would require an earlier corner visit, a contradiction.  Therefore the
upper horizontal edge is west too.  Every first-departure cycle has directions
`W,N,W,S` and voltage `-1`.

This argument uses the actual incoming heading only to infer `z` at the
lower `C`.  It does not identify that heading with the geometric incoming
cycle edge without the matching inequality.

#### The complete first-port profile

The first matching inequality leaves exactly the following first-port pairs
on a visited row:

| State | First `Q` port | First `C` port |
|---|---|---|
| A | SR | WR |
| B | SR | ER |
| C | NR | ER |

The pair `NR,WR` would have `u=1,z=0`, which is forbidden.  The actual bottom
row is A and the actual top row is C.  An A row immediately below a C row
would be the clockwise square excluded above.  Thus every first-departure
cycle consists of adjacent rows AB.

A B row must occur.  The visited rows form an interval; starting from the
bottom A row, the first non-A row cannot be C and must be B.  This also
gives an AB pair.  The lowest C row has a B immediately below it, giving
a BC pair.  Hence the coupled-return construction below applies to every
axis-two trace, not only to an optional local profile.

Now select the predecessor of each first visit and direct these edges
backward.  The first-entry result in `cylinder_exit_cycles_2026-09-03.md`
gives reverse voltage `-1`; the row-line argument again gives four vertices.
Reversing this cycle yields forward directions `E,N,E,S`.  The selected
first incoming headings are S at the lower `Q`, N at the upper `Q`, and E
at both `C` vertices.  Its two first-port states are therefore BC.

Every such BC pair gives the dual period decomposition into four closed
excursions starting at first visits, followed by the selected first-entry
edges.  This records the white starting colour at each excursion root.  It
does not make the other cells encountered there initially white.

The B rows also give a two-return identity.  Choose a representative with
`r=0`; the `r=1` case differs only in copy alignment.  Write `F_Q,F_C` for
the first lifted times.  The positive closed returns from the strict first
mismatch have departure intervals

```text
Q return: [F_Q, F_C-1),
C return: [F_C-N, F_Q+1).
```

The first is at `Q`; the second is at the appropriate translated `C` cell.
They share the first `Q` west-departure event and together omit the `Q`
east-departure event feeding first `C`, relative to one complete period.
If the latter event has turn sign `s` (`+1` for R and `-1` for L), their
turn balances satisfy

```text
T_Q+T_C = g+1-s.
```

At growth eight this is eight when `s=+1`, and ten when `s=-1`.  The two
returns share a history; treating them as independent excursions would lose
this relation.

The same accounting holds cell by cell.  For an interval `I`, let `Delta_I`
be the signed change in its black set, with coefficients in `{-1,0,1}`.
For the period interval `P=[F_C-N,F_C)`, the overlap and omission give

```text
Delta_Q + Delta_C = Delta_P + (1-s) 1_Q.
```

Here all three intervals use the same physical coordinates.  On projecting
by `(2,0)`, the signed period change becomes the wake vector `Omega`, whose
coefficients are zero or one.  Thus

```text
pi(Delta_Q) + pi(Delta_C) = Omega + (1-s) 1_[Q].
```

Projection sums signed coefficients; it does not count distinct changed
cells.  In particular, the mod-four additive charges of this identity give
the existing period residue equations with the displayed root correction.
They are not a further wake obstruction.

#### A heading reversal with unchanged root needs six changed cells

Let a finite legal ant segment return to a cell `z=(x_0,y_0)` with the
opposite incoming heading.  Suppose that `z` has the same colour at the two
endpoints.  Then at least six distinct physical cells have odd visit count
in its departure interval.

Write `Delta` for its signed black change and `D` for the support of
`Delta`.  The row-column parity identity P27 makes the incidence graph of
`D` Eulerian: both endpoint tokens are the same coordinate vertex because
the endpoint headings have the same axis.  This graph is simple and
bipartite.  Any nonempty such graph has at least four edges, and its edge
count is even.

The signed endpoint charges rule out four.  For a mod-four weight `w`
satisfying the zero four-corner condition, the additive-charge cocycle gives

```text
sum_x Delta(x) w(x) = F_h(z)-F_(h+2)(z) = 2w(z)  (mod 4).
```

The last equality is the opposite-heading identity in the cocycle proof.
Use, separately, the admissible weights

```text
w_row(x,y) = (-1)^(x+y) [y=y_0],
w_col(x,y) = (-1)^(x+y) [x=x_0].
```

Each weighted sum is two modulo four.  Consequently `D` has a cell on the
root row and a cell on the root column, so `D` is nonempty.  If it had only
four cells, its simple Eulerian incidence graph would be a four-cycle:
the four corners of a rectangle.  One of its two rows would be `y_0` and
one of its two columns would be `x_0`.  The rectangle would therefore
contain `z`.  But unchanged root colour says `z` is absent from `D`.
This contradiction proves `|D|>=6`.

For a B row, the `Q` return starts at its first `SR` visit and ends just
before the feeding east departure.  If that feeding turn is R, its port
is `NR`: the heading has reversed and the root has returned to white.
The six-cell bound applies.  If the feeding turn is L, its port is `SL`;
the root is black, and the ordinary nonempty Eulerian-support bound gives
four cells instead.  The `C` return always changes incoming heading from
E to W, so it has the six-cell bound whenever its root returns to white.

These are physical-cell bounds.  A changed cell may have been black at the
start, and different physical cells may project to the same translation
class.  Neither bound can be added directly to the growth-eight wake count.

#### The first-return ray restriction

The coupled returns retain a spatial restriction that arbitrary legal
closed excursions need not satisfy.  Translate a B row to height zero,
normalize the first `C` visit to `(0,0)` at time zero, and put the first
visit to `Q=(1,0)` at time `delta_C-1`.  Then

```text
C return: [0, delta_C),
Q return: [delta_C-1, N-1).
```

The `C` return ends at `(0,0)`, and the `Q` return ends at `(1,0)` just
before the east step feeding first `C+d` at time `N`.

The first visit to `C+kd` is at time `kN`.  The first visit to `Q+kd` is
at time `delta_C-1+kN`.  Thus, before its final `Q` departure, the `C`
return cannot visit any cell `(x,0)` with `x>0`.  Its final two steps are
S,W, because the final `Q` visit is the first `SR` there.  The `Q` return
cannot visit any `(x,0)` with `x>=2`.  These statements exclude a whole
horizontal ray, not only an early return to the named root.

The proof uses first-visit order in translated copies and holds for any
period.  It still leaves the path free to enter those columns on other
rows; no half-plane containment follows.

##### The shortest C return

Every B-row `C` return has length at least eight.  A four-step return would
be a unit square.  Starting south and ending west forces directions
`S,E,N,W`, but then its final `Q` arrival is N, not the required first S
arrival.

At length eight the direction word is unique:

```text
S,W,N,E,N,E,S,W.
```

Indeed, the four vertical steps must be `S,N,N,S`.  The horizontal steps
are two east and two west, with the last west.  If the first horizontal
step were east, the next north step would visit `Q=(1,0)` too early.
Thus the horizontal steps must be `W,E,E,W`, proving the claim.  Its turns
are `R,R,R,R,L,R,R,R`, and its signed black change is six.

This return forces the feeding turn `s` to be L.  The physical cell
`Q-d=(-1,0)` feeds first `C` at time `-1`, with the same turn `s` as the
feeding event at time `N-1`.  The eight-step return next visits `(-1,0)`
at time three with port `NR`.  There is no intervening visit there, so
alternation makes the time-minus-one turn L.

The coupled `Q` return has signed change four, but it cannot be the
four-step all-right square.  The eight-step `C` return leaves `(0,1)`
black at time five.  Starting at first `Q` at time seven, the actual next
steps are W to the now-white `C`, then N to `(0,1)`.  That cell turns
left, forcing W.  Hence the `Q` return starts `W,N,W` and has length
greater than four.  With `N=4 mod 8` and `delta_C=8`, this gives

```text
delta_Q >= 12,       N >= 20.
```

##### Ray avoidance does not make the discrepancy positive

There is a legal twelve-step return starting at `C=(0,0)` heading E,
with initial black set

```text
{(-1,-1), (-1,-2), (0,-2)}.
```

Its direction and turn words are

```text
directions: S,W,S,E,N,W,N,E,N,E,S,W,
turns:      R,R,L,L,L,L,R,R,L,R,R,R.
```

It first visits `Q=(1,0)` at time eleven, with incoming S and a right
turn.  Before that event it avoids every `(x,0)` with `x>0`.  The repeated
departure cells `C` and `(0,-1)` each have turns R then L;
`(-1,-1)` has L then R.  All other departure cells occur once, so the
displayed turns follow directly from the given initial colours.

At the return to `C`, its colour is again white.  The signed discrepancy is

```text
removed: (-1,-2), (0,-2),
added:   (-1,0), (0,1), (1,1), (1,0).
```

Thus the six-cell bound is sharp even with the ray restriction, while
the signed change is only two.  This finite return does not claim a
P3-periodic extension.  Its entering black cells require earlier histories,
and no contradiction in those histories has been proved here.  Their
compatibility with the other return is the missing global condition.

#### Exact lifetime identities at the trace extremes

At the lowest visited row choose representatives

```text
Q=(x,y_min),       C=(x-1,y_min),
```

with `Q` vertical-arrival.  The allowed port words are alternating subsequences
of

```text
Q: SR,SL,SR,SL,...
C: WR,EL,WR,EL,... .
```

They have the same length and start with right turns.  Write `Q_Ri,Q_Li`
and `C_Ri,C_Li` for corresponding right and left occurrences.  A right
departure from `Q` reaches `C` with voltage zero.  A left departure reaches
`C+d` with voltage one.  Within each directed edge block, matching preserves
stable order.  Thus

```text
tau(C_Ri)=tau(Q_Ri)+1,
tau(C_Li)=tau(Q_Li)+1-N.
```

Subtracting gives, for every pair present in the stable words,

```text
bottom Q black lifetime = bottom C black lifetime + N,
bottom C white lifetime = bottom Q white lifetime + N.
```

Here a black lifetime runs from `R_i` to `L_i`, and a white lifetime from
`L_i` to `R_(i+1)`, at one physical cell.  In particular, the lifetimes on
the left are strictly longer than one period.

At the highest visited row choose instead

```text
Q=(x,y_max),       C=(x+1,y_max).
```

The stable port words now use `NR,NL` at `Q` and `ER,WL` at `C`.  Right
departures have voltage zero and left departures voltage minus one, giving

```text
tau(C_Ri)=tau(Q_Ri)+1,
tau(C_Li)=tau(Q_Li)+1+N.
```

Hence

```text
top C black lifetime = top Q black lifetime + N,
top Q white lifetime = top C white lifetime + N.
```

Every nonempty return to a physical cell has length a positive multiple of
four.  Each of the long lifetimes in these displays is therefore at least
`N+4`.  None can be contained in a single excursion of a last-exit-cycle
decomposition, since every such excursion has length less than `N`.

#### Which extremes can a last-exit cycle touch?

If a last-exit cycle reaches the lowest trace row, it uses both of that row's
classes.  Its horizontal edge is east.  But the last `Q` port on that row
is `SR` (westward) if wake, and `SL` (eastward) if non-wake.  Thus a cycle
touching the trace bottom requires a non-wake row.

At the highest trace row, the last `Q` port is `NR` (eastward) if wake and
`NL` (westward) if non-wake.  A cycle touching the trace top therefore
requires a wake row.

There are no excursion waits at either boundary class when a cycle has
such contact.  At a non-wake bottom `Q`, any arrival earlier than the final
`L` precedes a subsequent black lifetime longer than `N`.  The wait from
that arrival to the last visit cannot fit in the decomposition.  Thus the
cycle arrives directly at the last `Q` visit.  Its last `SL` departure
matches the last `EL` at `C`, giving zero wait there too.

At a wake top `Q`, an arrival earlier than the final `R` similarly precedes
a white lifetime longer than `N`.  Thus the wait at `Q` is zero, and its
last `NR` departure matches the last `ER` at `C` with zero wait.

Nothing here forces a cycle to touch a trace extreme.  Extreme classes may
belong to trees feeding an interior cycle.  The unresolved case is therefore
not removed by treating a cycle's own lowest row as the trace bottom, or by
assigning one wake row to every interior last-exit cycle.

#### A local odd-row count is insufficient

A closed return can have four odd-visit cells on two rows of the same parity.
Here is a literal eight-step example, with no periodicity claim.  Start at
`(0,0)` heading north, with black cells

```text
(1,0), (1,1), (0,1),
```

and all other cells white.  The visited departure cells and their turns are

| Step | Cell | Incoming heading | Turn | Outgoing step |
|---|---|---|---|---|
| 0 | `(0,0)` | N | R | E |
| 1 | `(1,0)` | E | L | N |
| 2 | `(1,1)` | N | L | W |
| 3 | `(0,1)` | W | L | S |
| 4 | `(0,0)` | S | L | E |
| 5 | `(1,0)` | E | R | S |
| 6 | `(1,-1)` | S | R | W |
| 7 | `(0,-1)` | W | R | N |

The final state of the ant is again `(0,0)` with heading north.  The two
repeated cells have opposite turns on their two visits.  The odd-visit cells
are exactly `(0,1),(1,1),(0,-1),(1,-1)`, all on the odd rows `1` and `-1`.
The black domino on row one disappears and a black domino appears on row
minus one; `(1,0)` returns to black.  The turn balance and net black change
are both zero.

This refutes an opposite-parity claim based only on legal closed excursions.
It does not construct a periodic P3 trace: the initial black cells would need
their own consistent earlier histories.  In particular, the excursion's
four odd-visit cells are not four new wake classes.  Their signs depend on
the colours present when the excursion starts.

<a id="source-research-notes-cylinder-exit-cycles-2026-09-03-md"></a>

## cylinder_exit_cycles_2026-09-03

Source: `research-notes/cylinder_exit_cycles_2026-09-03.md`.

### Exit cycles wind once, with an exact excursion decomposition

Let a finite-support periodic Langton trace have period `N` and nonzero drift
`d=(a,b)`.  Select the edge leaving the last stable occurrence of each visited
translation class.  Every directed cycle of this last-exit graph has voltage
exactly `+1`.

Moreover, a cycle of length `k` gives an exact decomposition of one period
into its `k` selected lattice edges and closed return excursions of lengths
`D_1,...,D_k`, where

```text
N = k + sum_i D_i,       D_i in 4 Z_(>=0).
```

In particular, every individual excursion is shorter than `N`.  This is
stronger than the positive-voltage inequality: it retains the actual motion
omitted between selected last visits.  It does not bound the wake carried by
the excursions or exclude growth eight.

#### Chronological signs

Choose a representative cell `c_v` for each visited translation class.  Give
a phase occurrence at `c_v+n_i d` lifted time `i-N n_i`.  Write `T_v` for the
largest such time, and let the last selected edge have target `f(v)` and
voltage `lambda_v`, so

```text
c_v + selected step = c_(f(v)) + lambda_v d.
```

The arrival at its target occurs no later than that target's last visit.
Hence

```text
T_(f(v)) + N lambda_v >= T_v+1.
```

Summing around a directed cycle gives `N Lambda>=k>0`.  Its integer voltage
is therefore positive.  This is the last-exit inequality proved in
`odd_skew_excursions_and_domino_transfer_2026-08-31.md`; it does not require
the drift vector to be primitive in the lattice.

For comparison, let `F_v` be the first stable visit time and select the edge
leaving that visit.  Its target's first visit is no later than the arrival,
so

```text
F_(g(v)) + N lambda_v <= F_v+1.
```

A first-departure cycle consequently has `N Lambda<=k`.  Since it uses
distinct classes, `k` is at most the number of visited classes, which is at
most `N`.  Positive voltage would force equality throughout.  Every class
would then be a singleton, and P3 would make every turn right.  An all-right
heading-reset word closes after complete four-step squares and has zero
drift.  Thus a nonzero-drift trace has no positive first-departure cycle.

#### Why a simple quotient cycle cannot wind twice

The quotient surface `R^2/Zd` is a cylinder, even when `d` is not primitive.
The lattice edges embed in it.  Two projected unit edges can meet away from
their endpoints only if they are the same projected edge: translation by
`d` preserves the integer lattice.

A functional-graph cycle has distinct quotient vertices.  Its realization
therefore has no self-intersection, unless it retraces an undirected edge.
Such retracing would be a two-edge backtrack.  In the present directed lattice
that is impossible: the incoming and outgoing axes at every cell are
perpendicular.  Here the checker/heading invariant matters: every visit to a
translation class has the same incoming axis, since heading reset makes the
drift preserve checker parity.  The selected edge and an earlier incoming
edge therefore remain perpendicular even when they belong to different
visits.  Thus every selected cycle is an embedded simple closed curve in the
cylinder.

Identify the cylinder with the punctured plane, using longitudinal position
as angle and the exponential of transverse position as radius.  The image
of an embedded cycle is a Jordan curve.  Its winding about the puncture is
zero if the puncture is outside, and otherwise is `+1` or `-1` according to
orientation.  The winding is precisely the cycle's edge voltage.  Therefore

```text
last-exit cycle:       Lambda=+1,
first-departure cycle: Lambda=0 or -1.
```

The previously proved orientation restriction still applies to the
zero-voltage first-departure cycles: their planar lifts are counterclockwise.
The winding statements do not imply that either functional graph has only
one cycle.  The standard period-104 trace has two last-exit cycles, as
recorded in the excursion note.

#### Recovering a full period from a last-exit cycle

Choose a sufficiently late physical copy of the cycle, starting at the last
visit to a cell representing `v_0`.  Follow its selected edge to the next
physical cell.  The actual trace runs from this arrival to that same cell's
last visit before taking its selected edge.  This intervening segment is a
closed return excursion; it may have length zero.

Repeat at each successive cycle vertex.  Chronological extremality ensures
that each selected last visit occurs after the preceding selected edge, so
these segments concatenate in actual time.  Voltage `+1` puts the final
cell at the starting cell plus `d`.  Its last visit is exactly `N` steps
after the starting last visit.  The selected edges and intervening excursions
thus partition one period, proving

```text
N=k+D_1+...+D_k.
```

A closed quarter-turn walk alternates horizontal and vertical steps.  Zero
displacement makes the count on each axis even, so its length is divisible
by four.  This proves `D_i in 4 Z_(>=0)`.  If `r` selected edges do not land
directly at their target's last visit, it also gives

```text
N>=k+4r,       N=k mod 4.
```

The cycle itself alternates step axes and has displacement `d`.  Hence its
length obeys

```text
k >= 2 max(|a|,|b|).
```

For example, at drift `(1,-3)` every last-exit cycle has length at least six.

#### The first-entry version

There is also a first-entry version of the decomposition.  At each first
visit select its physical predecessor, directing the selected edge backward.
If that predecessor is in class `p(v)` with reverse voltage `mu_v`, then

```text
F_(p(v))+N mu_v <= F_v-1.
```

Every reverse-first-entry cycle consequently has strictly negative voltage.
The cylinder argument makes it exactly `-1`.  Reverse the cycle's orientation
to obtain forward voltage `+1`.  Starting at a sufficiently future first
visit, the actual trace waits at each cycle source until the departure
feeding the next cycle vertex's first visit, then takes that selected edge.
These waits are closed excursions starting at first visits.  They give
another exact identity `N=k+sum_i D_i`, with `D_i in 4 Z_(>=0)`.

This graph is different from the first-departure graph: one selects edges
entering first visits, the other edges leaving them.  The first-entry waits
start at white, right-turn visits; the last-exit waits end at last visits.
Neither description fixes the initial colours of the other cells met by
an excursion.

##### Exactly half the first-entry vertices have positive waits

For this forward first-entry cycle, its incoming edge at a physical vertex
`v` is the actual first arrival there. If the geometric corner at `v` is
R, that first visit immediately traverses the geometric outgoing edge.
Its target cannot have its selected first arrival later via the same edge:
the first departure from `v` has already reached that exact physical cell.
Thus the wait at an R corner is zero. At an L corner the geometric edge
is opposite to the actual first R departure, so the wait is positive.

Every embedded essential cycle on the flat translation cylinder has total
signed turning zero. One elementary proof takes a straight longitudinal
circle beyond its transverse range. The two disjoint circles bound a flat
annulus. Triangulate it; summing the triangle angles gives total boundary
exterior angle `2 pi chi=0`. The straight circle contributes zero, so the
polygonal cycle does too. There is no curvature singularity at the seam
because the identification is a translation.

Consequently a length-`k` first-entry cycle has exactly `k/2` L corners
and exactly `k/2` positive waits. Each positive wait has length at least
four. The period decomposition therefore yields the all-period bound

```text
N >= 3k >= 6 max(|a|,|b|).
```

This counts time, not signed black change. In particular, it does not
assert that a longer excursion adds four wake cells.

The turn-change argument in `first_entry_detour_charges_2026-09-04.md`
strengthens this to `N>=6 max(|a|,|b|)+2(|a|+|b|)`. That note also gives
the exact integer detour charges whose sum is `g/4`, and explains why
their positivity does not follow from local alternation and ray avoidance.

#### The missing wake estimate

##### Every positive last-exit wait reverses heading

Suppose the selected last departure from a physical cell `u` reaches a
cycle vertex `v` with incoming heading `h`. Let `D_v` be the wait from this
arrival to the last visit to `v`. If `D_v>0` and that last visit also had
heading `h`, its predecessor would again be the physical cell `u`.
That would visit `u` after its selected last departure, a contradiction.
The fixed incoming axis leaves only the opposite heading. Thus

```text
D_v=0: the incoming heading is unchanged,
D_v>0: the incoming heading is reversed.
```

This proof also covers the wrap edge of a lifted cycle: the final vertex
is the appropriate translated physical cell, not an unshifted representative.

Let `c_v` be the geometric turn of the cycle at `v`, with R equal to `+1`
and L to `-1`. The actual terminal turn is `s_v=2 omega_v-1`, since P3
ends an odd class with R and an even class with L. Both departures use the
same selected edge, so reversal of the incoming heading reverses the turn:

```text
D_v=0  iff  s_v=c_v,
D_v>0  iff  s_v=-c_v.
```

These equivalences retain information that the voltage inequalities alone
do not record. In particular, every positive last-exit excursion has turn
balance two modulo four.

##### Diagonal cycle extrema and rail avoidance

Now normalize `d=(m,-m)` with `m>0`, and use transverse coordinate
`t=x+y`. Every minimum of a positive-voltage embedded essential cycle
has geometric port `SL`; every maximum has geometric port `ER`.
For a negative-voltage cycle, the corresponding ports are `WR` at every
minimum and `NL` at every maximum.

To see this, use the orientation-preserving cylinder coordinates
`(u,t)=(x-y,x+y)`, with `u` taken modulo `2m`. For a curve oriented with
voltage `+1`, the component extending to `t=-infinity` is on its right,
and the component extending to `t=+infinity` is on its left. This follows
equivalently by its signed crossing number with an arc from the lower end
of the cylinder to the upper end. The sides exchange for voltage `-1`.

At a minimum the only possible quarter-turn corners are `W->N` and
`S->E`. At the former corner, a sufficiently close point southwest of
the vertex is on its left but lies strictly below the whole curve. This
contradicts voltage `+1`, so its minimum must be `S->E`. At a maximum
the possible corners are `E->S` and `N->W`; the latter puts a nearby
northeast point on the right, although it is strictly above the curve.
This excludes it for voltage `+1`. Exchanging left and right gives the
negative-voltage statement. Choose each neighborhood disjoint from all
nonincident edges; other equal extrema do not affect the argument.

In particular, positive cycles have vertical-arrival minima and horizontal-
arrival maxima. Their transverse width is odd. Negative cycles have the
opposite types and also have odd width.

Combining the positive-cycle corners with the exact wait rule gives

```text
at a cycle minimum: D_v>0 iff omega_v=1,
at a cycle maximum: D_v>0 iff omega_v=0.
```

A positive wait at a wake minimum ends with actual port `NR`, so its final
arrival comes from one level below that minimum. A positive wait at a
non-wake maximum ends with actual port `WL`, so its final arrival comes
from one level above that maximum. Such excursions must leave the cycle's
transverse range on the indicated side.

These statements concern the cycle's extrema, not an assumed full trace
boundary. They imply unconditional rail restrictions. A positive last-exit
or forward first-entry cycle cannot meet the actual lower rail: its
horizontal singleton vertices cannot be positive-cycle minima. A negative
first-departure cycle cannot meet the actual upper rail. A zero-voltage
first-departure cycle is counterclockwise; its bounded planar interior is
on the left. The same southwest/northeast test shows that it cannot meet
either horizontal rail. Hence every first-departure cycle avoids the
upper rail. None of these conclusions fills an unvisited rail lane.

##### What is still missing

The edge arriving along a selected cycle need not be the incoming edge of
the selected visit at its target.  A return excursion may intervene and
reverse the incoming heading.  Consequently, first-turn `R` or terminal-turn
parity does not determine the geometric turn of the cycle at that vertex.
Counting the curve's corners as wake cells would discard exactly the
excursions retained above.

A closure argument still needs to control these excursions using stable
visit order and the growth-eight wake budget.  The one-winding theorem
provides an exact decomposition for that argument, not the missing estimate.

<a id="source-research-notes-first-entry-detour-charges-2026-09-04-md"></a>

## first_entry_detour_charges_2026-09-04

Source: `research-notes/first_entry_detour_charges_2026-09-04.md`.

### First-entry detour charges and a stronger period bound

The first-entry cycle gives an exact integer decomposition of growth. It also
gives the uniform bound

```text
N >= 6 max(|a|,|b|) + 2(|a|+|b|)
```

for nonzero drift `(a,b)`. Both statements follow from visit order and planar
geometry. They use no enumeration. Neither closes a growth-eight drift orbit.

The sign of an individual detour charge remains the obstruction. Simple
detours have charge one, but a legal eight-step detour with charge zero is
given below. Its compatibility with an entire periodic trace is not asserted.

#### Exact charge accounting

Use the forward first-entry cycle from
`cylinder_exit_cycles_2026-09-03.md`. Its length is `k`, its voltage is one,
and its geometric turn sum is zero. The actual period consists of the
selected edges and closed waits at their sources. Exactly the `k/2`
geometric L corners have positive waits; R corners have zero waits.

At a positive wait, let `T` be the sum of the actual turns during the wait,
excluding the departure along the selected edge. Let `s` be that departure's
turn, with R equal to `+1` and L to `-1`. Define

```text
q = (T+s+1)/4.
```

This is an integer. If the final incoming heading equals the first incoming
heading, feeding the geometric L edge requires `s=-1`, and `T=0 mod 4`.
If the heading is reversed, feeding that same edge requires `s=+1`, and
`T=2 mod 4`. The fixed incoming axis leaves no other case.

Every zero-wait R corner contributes one actual R. Adding the turns in the
period therefore gives

```text
g = sum_positive_waits T + k/2 + sum_positive_waits s
  = 4 sum_positive_waits q.
```

At growth eight, the `k/2` integer charges sum to two. The formula by itself
does not say that the charges are positive, or even nonnegative.

#### A four-step wait cannot follow a geometric R corner

A four-step closed quarter-turn walk is a unit square. Its root is visited
once before the return. Since this is a first-entry wait, that first visit
is white/R, and the return finds the root black. The feeding turn is thus L.
The selected geometric turn is also L, so the return heading equals the
initial heading. The square's closing corner at the root is consequently R:
the square is clockwise, and all four turns during the wait are R.

Let `u` be the physical predecessor of the root's first visit. The square
visits `u` at its third step, then returns to the root. There is no intervening
visit to `u` after its selected departure immediately before the wait.
Because the square turns R at `u`, that preceding departure must have turned L.

If `u` were a geometric R corner of the first-entry cycle, its selected
departure would instead be its first, right-turn departure. Hence a
four-step wait is impossible at the L corner of every cyclic R-to-L
transition.

Let `rho` count these transitions. The `k/2` positive waits cost at least
four steps each, and these `rho` waits cost at least eight. Thus

```text
N >= 3k + 4 rho.                                      (1)
```

There is at least one transition, so equality in the earlier bound `N>=3k`
is impossible at every nonzero drift, independently of growth.

#### Drift forces enough turn changes

Write `e_i` for the selected unit step leaving cycle vertex `i`, with indices
modulo `k`, and `c_i` for the geometric turn from `e_(i-1)` to `e_i`.
Two successive quarter turns give

```text
e_(i+1) = -c_i c_(i+1) e_(i-1).
```

If the turns agree, `e_(i-1)+e_(i+1)=0`; if they differ, the sum is
`2 e_(i-1)`. Summing around the cycle yields the vector identity

```text
(a,b) = sum_(c_i != c_(i+1)) e_(i-1).
```

There are `2 rho` changes, since R-to-L and L-to-R changes alternate in a
cyclic word. Taking the lattice one-norm gives

```text
|a|+|b| <= 2 rho.
```

Combine this with (1) and `k>=2 max(|a|,|b|)`:

```text
N >= 6 max(|a|,|b|) + 2(|a|+|b|).                     (2)
```

For diagonal drift `(m,-m)`, (2) is `N>=10m`. At growth eight, combining
it with the existing period congruences gives `N>=20` at `(2,0)` and
`N>=40` at either `(2,4)` or `(2,-4)`. These are consequences of this
argument alone, not claims that those periods are feasible or that other
proved restrictions stop there. There is still no upper bound on `N`.

#### Eight-step positive waits have charge zero

First suppose an eight-step positive wait revisits its root before the final
return. The intermediate return must occur at step four, since closed
quarter-turn walks have length divisible by four.

If the first square is clockwise, the root returns with its initial heading
and is black. Its L departure at step four already takes the selected edge.
That reaches the selected target too early, contrary to the definition of
the wait.

For the other orientation, rotate coordinates so the initial heading is N.
The first square has directions `E,N,W,S` and turns `R,L,L,L`. At step four
the black root has heading S, so its L turn again sends it E. The next cell
was flipped from black to white during the first square, forcing R and then
S. A four-step return now has to finish W,N. At step eight the root is white
and the heading is N, so its next R again takes E, not the selected W edge.
This also cannot be the required wait. Hence the root has no intermediate
visit in an eight-step positive wait.

The return therefore finds the root black. The feeding turn is L, the
return heading equals the initial heading, and `T=0 mod 4`.

There is no simple eight-edge unit lattice polygon that turns at every
vertex. Its four horizontal and four vertical edges put its bounding box
inside a two-by-two square. A simple polygon's enclosed unit faces must be
edge-connected. A single face has perimeter four, and two adjacent faces
have perimeter six. Perimeter eight therefore leaves an L-shaped set of
three unit faces or the full two-by-two square. Both have consecutive
collinear boundary edges.

Thus some other physical cell repeats. Its two visits are four steps apart,
and splitting the cyclic closed walk there gives two unit squares. Write
their clockwise orientation signs as `epsilon_1,epsilon_2`, each equal to
`+1` or `-1`. The six corners away from the splitting cell contribute
`3(epsilon_1+epsilon_2)`. The two actual turns at the splitting cell alternate
and sum to zero. At the original root the polygon's closing corner equals
its actual initial turn, since the return heading is unchanged. Consequently

```text
T = 3(epsilon_1+epsilon_2) in {-6,0,6}.
```

Only zero is divisible by four. Therefore `T=0`, `s=-1`, and `q=0` for
every eight-step positive first-entry wait.

##### Strictness at diagonal drift

If `d=(m,-m)` and equality held in `N>=10m`, the inequalities above would
force `k=2m`, `rho=m`, and length eight at every positive wait. Their charges
would all be zero, giving `g=0`. At growth eight equality is impossible.
Since `N=2m mod 4`, the resulting bound is

```text
N >= 10m+4.
```

For `m=1,2,3` this gives respectively `N>=14,24,34`. For `m=4`, the
growth-eight congruence `N=0 mod 8` raises the bound further to `N>=48`.
These remain lower bounds on period, not all-period exclusions.

#### Two preceding R corners rule out an eight-step wait

The eight-step classification also constrains the preceding selected cycle
vertices. At every geometric `R,R,L` pattern, the wait at the L corner has
length at least twelve. The four-step case was excluded above; the following
argument excludes eight using the actual predecessor visits.

An eight-step positive wait consists of two oppositely oriented unit squares,
as in the charge-zero proof. If the squares coincided, their join would
reverse direction. If they met only at diagonally opposite corners, the join
would be straight. Both are forbidden in a quarter-turn walk. They therefore
share an edge. Both endpoints of that edge repeat, so the first-entry root,
which has no intermediate visit, is a nonshared corner. Its closing turn is
R, placing it on the clockwise square.

There are two such corners. Up to rotation and translation, with root
`v=(0,0)` and initial incoming heading E, they give the two direction words

```text
A: S,W,N,W,S,E,N,E
B: S,W,S,E,N,W,N,E.
```

The selected edge after either wait goes north. Set the first visit to `v`
at time zero. Its physical cycle predecessor is `u=(-1,0)`, whose selected
departure reaches `v` at time zero and hence occurs at time `-1`.

In case B, the wait visits `u` at time seven with an R turn. There is no
intervening visit to `u` after time `-1`, so that selected departure must
have turned L. In particular, `u` cannot be a geometric R corner: such a
corner has zero wait and its selected departure is its first, right turn.

In case A, the visits to `u` at times three and seven turn L and R. Suppose
`u` is a geometric R corner. Its event at time `-1` is then its first visit,
with incoming heading N and outgoing heading E. Thus its physical cycle
predecessor is `z=(-1,-1)`, whose selected north departure occurs at time
`-2`. Case A reaches `z` at time two with incoming heading W and turn R.
The intervening events, at times `-1,0,1`, occur at `u`, `v`, and `(0,-1)`,
none of which is `z`. Same-cell alternation therefore makes the selected
departure from `z` at time `-2` an L turn. Consequently `z` cannot be a
geometric R corner either.

An eight-step wait following an R corner thus forces the corner before that
R to be L. This rules out the pattern `R,R,L`. The argument is on one
physical lift of the cycle; it also applies when these three vertices
straddle the chosen period boundary.

##### A nonzero-growth cycle needs a wait of length at least twelve

Suppose all positive waits of a selected first-entry cycle have length four
or eight. If any cyclic R run had length at least two, its last two corners
and the following L would form `R,R,L`, contradicting the preceding result.
Hence every R run is a singleton.

The geometric turn sum is zero, so the cycle has equal numbers of R and L
corners. Its cyclic R and L runs also have equal counts. It follows that
every L run is a singleton as well: the turn word alternates R,L. Each
positive wait now follows an R corner, so none can have length four. All
have length eight and charge zero, giving `g=0` by the exact charge identity.

Therefore every trace with nonzero growth has a positive wait of length at
least twelve on every selected first-entry cycle. In particular, this holds
for every growth-eight drift orbit. It is a restriction from coupled visit
history, not a sign bound on longer waits or an exclusion of any orbit.

#### Simple positive waits have charge one

Suppose a positive wait is a simple closed physical lattice polygon: no
physical cell repeats before the final return to its root. The root again
finds black at the return, so `s=-1`, the return heading equals the first
heading, and the polygon's closing corner is R.

The infinite forward lift of the selected first-entry cycle starts at this
root, takes the feeding edge, and tends to infinity. Every other vertex on
that forward ray has a strictly later first-visit time than the end of the
wait. Consequently the ray cannot meet any vertex visited during the wait.
Unit lattice edges cannot cross without sharing a vertex, so it cannot
cross the wait polygon either.

If the polygon were counterclockwise, its R corner at the root would be
reflex. The feeding edge, opposite to the wait's first outgoing edge, would
enter its bounded interior. The forward ray would then have to cross the
polygon to reach infinity. This is impossible. The polygon is clockwise,
so its turn sum is `T=4`, and

```text
q=(4-1+1)/4=1.
```

If every positive wait of the chosen cycle is simple, it follows that
`g=2k`. At growth eight this forces `k=4`. Four alternating-axis steps with
nonzero displacement allow only the quarter-turn orbits of `(2,0)` and
`(2,-2)`. Thus the other eight growth-eight drift orbits necessarily require
a nonsimple positive wait on every first-entry cycle. This is a restriction
on their detours, not an exclusion of those orbits.

#### Why root colour and an unvisited future ray do not prove positivity

Start at `v=(1,0)` with incoming heading E. Initially make exactly
`(0,0),(-1,0),(-1,-1)` black among the cells used below. The following
eight-step return is legal:

| time | cell | incoming | turn | outgoing |
|---|---|---|---|---|
| 0 | `(1,0)` | E | R | S |
| 1 | `(1,-1)` | S | R | W |
| 2 | `(0,-1)` | W | R | N |
| 3 | `(0,0)` | N | L | W |
| 4 | `(-1,0)` | W | L | S |
| 5 | `(-1,-1)` | S | L | E |
| 6 | `(0,-1)` | E | L | N |
| 7 | `(0,0)` | N | R | E |
| 8 | `(1,0)` | E | L | N |

The last row is the feeding departure, excluded from the wait's turn sum.
The two repeated interior cells alternate: `(0,-1)` has R,L and `(0,0)`
has L,R. The root is first-white and appears only at times zero and eight.
There are four R and four L turns during the wait, so `T=0` and `q=0`.

The feeding north edge reaches the unvisited cell `(1,1)`. A northeast
unit staircase from there avoids the whole detour, which lies in `y<=0`.
The immediate predecessor can even be a first NR visit to `(0,0)` at
time `-1`; it supplies the required black colour there, with visible
same-cell order R,L,R.

This is a re-rooted domino-transfer example of the type discussed in
`axis_two_exit_cycles_2026-09-03.md`. It does not supply the earlier histories
of the other black cells or a periodic P3 extension. It establishes the
narrow obstruction: first-white root, the right feeding edge, ordinary
alternation, and an unvisited ray to infinity do not force `q>=1`.

A growth-eight closure by this decomposition must use the coupled periodic
histories of the detours. Neither replacing every charge by one nor counting
all temporarily black cells as permanent wake is valid.

<a id="source-research-notes-highway-research-note-md"></a>

## highway_research_note

Source: `research-notes/highway_research_note.md`.

### A rigorous attempt on the finite-support Langton-ant highway conjecture

**Status, 20 July 2026:** I did not obtain a complete proof or a counterexample. This
is a historical working note, not the source of submission claims. Some later sections
preserve exploratory reductions and finite computations that were subsequently
withdrawn, narrowed, or not packaged with publication-grade certificates; they must
not be cited as theorems merely because they remain in this notebook. The canonical
claims and proofs are `../paper/main.tex`; the continuously updated audit trail is
`proof_journal.md`. In particular, the released paper does not claim the old exterior-
dynamics, Hamming-isolation, centered-$3\times3$, or touch-graph-rank statements.

#### 1. Formal statement

Let (c_0:\mathbb Z^2\to\{0,1\}) be an initial coloring, where (0) is white and (1) is black. Assume finite support:

\[
\left|\{z\in\mathbb Z^2:c_0(z)=1\}\right|<\infty.
\]

At a white cell the ant turns right; at a black cell it turns left. It flips the current cell and then moves one unit.

The classical highway conjecture says that after some time the ant's future path and
turn trace agree with the standard period-$104$ highway, up to lattice translation,
quarter-turn rotation, and cyclic phase. Finite stationary debris outside the future
path is allowed; equality of the entire colouring is not asserted. The conjecture
remains open.

There are two possible disproofs:

1. a finite configuration whose trajectory is never eventually periodic; or
2. under the “same period-104 highway” formulation, a finite configuration producing a different highway.

#### 2. What is already rigorously known

##### Unboundedness

Every trajectory visits infinitely many cells. Briefly, if the visited set were finite, reversibility and finiteness would make the trajectory periodic. Every cell is always entered horizontally or always vertically. Choose a visited cell maximizing (x+y). Its north and east neighbors are unvisited. If it is entered horizontally, it must enter from the west and leave south; after its color flips, the next visit from the west makes it leave north, a contradiction. The vertical case is the rotated argument. This is associated with the flipping Lorentz-lattice work of [Bunimovich and Troubetzkoy](https://doi.org/10.1007/BF01049035).

Unboundedness is much weaker than eventual periodic drift.

##### Finite-domain escape bounds

A June 2026 preprint proves that while the ant is confined to a fixed (d)-cell connected domain, the same coloring of that domain cannot occur twice. Consequently it escapes in at most (2^d) steps; stronger shape-dependent bounds are also proved. This controls every fixed box but does not control the geometry as the box grows. [Etse (2026)](https://arxiv.org/abs/2606.26677)

##### Computational complexity

Finite patterns can make the ant evaluate arbitrary Boolean circuits. Periodic backgrounds with finite perturbations can simulate cellular automata and Turing machines. Thus long transients can contain genuine computation, and a proof cannot reasonably rely on a small empirical time cutoff. [Gajardo–Moreira–Goles, *Complexity of Langton's Ant*](https://arxiv.org/abs/nlin/0306022)

#### 3. An exact periodic-trace criterion

The following criterion turns the search for a nonstandard highway into a finite, exact problem.

Let

\[
w=w_0w_1\cdots w_{N-1}\in\{R,L\}^N
\]

be a proposed repeating turn word. Fix an initial direction (q_0), and let (p_i) be the cell occupied immediately before turn (w_i). Calculate the path solely from (w). Suppose after (N) steps the direction is again (q_0) and the displacement is a nonzero vector

\[
d=p_N-p_0\ne0.
\]

Define an equivalence relation on phases by

\[
i\sim j \quad\Longleftrightarrow\quad p_i-p_j\in\mathbb Z d.
\]

For each equivalence class (I), choose a representative point (b_I) and integers (a_i) satisfying

\[
p_i=b_I+a_i d\qquad(i\in I).
\]

For an integer (n\ge \min_{i\in I}a_i), form the word (S_{I,n}) from all (w_i) with (a_i\le n), ordered by the pair

\[
(n-a_i,i).
\]

This is the chronological sequence of turns made at the physical cell (b_I+nd) during the infinite proposed trajectory (w^\omega).

##### Theorem — finite-support periodic-trace criterion

The infinite word (w^\omega) is exactly the trace of Langton's ant from some finite-support initial coloring if and only if, for every class (I):

1. every (S_{I,n}), for
   \(\min a_i\le n\le\max a_i\), alternates strictly between (R) and (L); and
2. the stabilized word (S_{I,\max a_i}) begins with (R).

When these conditions hold, an explicit finite initial black set is

\[
B=\{b_I+nd:\ n<\max a_i\text{ and }S_{I,n}\text{ begins with }L\}.
\]

##### Proof

At a fixed cell, each visit flips its color. Therefore its encountered turn sequence must alternate (R,L,R,L,\ldots) or (L,R,L,R,\ldots). This proves the necessity of condition 1.

The occurrence of phase (i) in period (k\ge0) is at (p_i+kd=b_I+(a_i+k)d). It visits the physical cell (b_I+nd) exactly when (k=n-a_i\ge0), and chronological order is precisely lexicographic order of ((n-a_i,i)). Hence (S_{I,n}) is the complete visit sequence at that cell.

Once (n\ge\max a_i), every phase in (I) is present and the ordering no longer changes with (n); the sequence has stabilized. Infinitely many cells therefore have this same first turn. Since only finitely many cells may initially be black, that stable first turn must be (R), proving the necessity of condition 2.

Conversely, color exactly the finite set (B) black and every other cell white. At each boundary cell the chosen initial color gives the first symbol of (S_{I,n}); strict alternation then gives every later symbol because the cell flips at each visit. At every stabilized cell, condition 2 makes the first encounter (R), matching its white initial state, and condition 1 again supplies all subsequent visits. Induction in chronological time proves that the ant follows (w^\omega) forever. Its position is translated by (d\ne0) every (N) steps, so this is a highway. ∎

There is a useful equivalent one-sequence test. In a fixed class, sort all entries by decreasing (a_i), breaking ties by increasing phase (i). This is the stabilized word. Every boundary word (S_{I,n}) is a suffix of it, obtained by deleting whole high-level blocks. Consequently it is enough to check that this single stabilized word alternates and begins with (R). This reduces the checker to one sort per translation class. A class and its integer level can also be found in constant time by reducing one coordinate modulo the corresponding nonzero coordinate of (d).

This theorem is implemented independently of finite-time pattern matching in [`langton_research.py`](../04_Reproduction/reproduction.zip) (member: `langtons-ant-highway/code/python/langton_research.py`), function `finite_seed_for_periodic_trace`.

#### 4. Exact computational results obtained in this attempt

All calculations use integer coordinates and exact finite sets—no hashes or probabilistic equality tests determine the result.

##### The standard highway has a 13-cell gateway

The blank orbit first enters its repeating trace at step 9,977 under zero-based step indexing. Its 104-symbol word has least period 104 and drift ((-2,2)) when normalized to an initially north-facing ant. Applying the theorem constructs the following 13-cell black seed:

```text
(-6,0), (-5,0), (-5,1), (-4,0), (-4,2),
(-3,-1), (-3,2), (-2,-1), (-2,1), (-1,1),
(0,0), (0,1), (0,2)
```

Starting north at the origin with only those cells black produces the 104-step highway immediately. The code also verifies the equivalent finite gateway induction: after 104 steps the required local pattern and direction recur translated by the drift, and the entire semi-infinite leading corridor is white.

##### All centered (3\times3) patterns are certified

For a north-facing ant at the center, all (2^9=512) possible black/white patterns supported in the centered (3\times3) block were exhaustively simulated. Every one reached an exact gateway certificate by step 43,577. The last-certified pattern was

```text
#.#
#.#
#.#
```

This is a rigorous computer-assisted result for those 512 cases, not evidence for all finite configurations.

##### No finite-support highway of period at most 40

A depth-first enumeration completed the entire legal trace tree through period 32. It is enough to search words beginning with (R): the criterion implies that every finite-support periodic trace contains an (R), and restarting that orbit at such a phase preserves finite support. The 32 length-six prefix shards beginning with (R) contained 25 dynamically legal prefixes, visited 46,185,421 feasible nodes, and all reported zero highways. Periods shorter than six are covered by the earlier searches, and an odd period cannot restore the heading because an odd sum of quarter-turns cannot be divisible by four.

Thus the original periodic-trace search excluded every highway from finite support of nonzero drift and period (1\le N\le32). Independent implementations were cross-checked on all 131,070 binary words through length 16.

After the analytic elimination of zero growth, a new exact positive-growth search completed periods 34, 36, 38, and 40. Its primary runs visited 9,726,176; 19,781,050; 41,972,884; and 201,924,597 nodes and checked 295,495; 1,194,951; 1,469,976; and 10,313,586 exact periodic-criterion leaves, with zero hits. Every rank interval completed without a cap. Independent no-deficit reruns reproduced the zero-hit result at periods 34, 36, and 38; Python/Java per-shard candidate counts agree at periods 16 and 20; and the Java checker positively accepts the known standard word.

Odd lengths cannot restore heading. Combining these computations with the even-winding theorem therefore excludes **every finite-support periodic highway of period at most 40**. This remains a bounded-period computer-assisted theorem and does not exclude aperiodic behavior or periods above 40. The full pruning and coverage audit is in `langton_positive_growth_search_audit.md`.

##### The standard word is isolated through Hamming radius four

All 5,356 distance-two and all 4,598,126 distance-four mutations of the standard 104-symbol word were checked exactly; none passed the criterion. A mutation at odd Hamming distance cannot restore the heading, because every flipped turn changes the net rotation by two quarter-turns modulo four. Hence there is no distinct finite-support periodic highway word within Hamming distance four of the standard word. The compiled distance-four checker was first cross-validated against the Python reference on the complete distance-two score histogram.

A targeted constructive search then checked 265,125 distance-six words obtained by extending every distance-four word with violation score at most five. No highway was found; the best three words had two remaining violations. This is not a complete distance-six exclusion—the full sphere has 1,517,381,580 words.

##### Adversarial transient search

A small evolutionary run over 221 seven-by-seven patterns found no non-highway behavior; its longest heuristic onset was 44,845 steps. This is only exploratory evidence and has no theorem status.

##### Historical computer exclusion at zero-growth period 40

For a repeating trace with zero net black growth, the endpoint decomposition eventually leaves a clean finite translator after its stationary debris separates from the translated path. The proved clean-translator restrictions and the bound $N\ge8|d|$ imply that a nonzero-drift period-40 candidate can have only drift $(\pm4,0)$ or $(0,\pm4)$, and that every drift-translation class of phase positions must have even cardinality.

An exact depth-first search then covered all $2^{11}=2,048$ length-12 prefixes beginning with R. Of those shards, 650 were locally valid; together they visited 16,837,779 legal-prefix nodes. Every shard finished without reaching its node cap, and none produced a finite-support trace certificate. The saved full-shard computation record is `langton_zero_growth_p40_complete_2026-07-14.json`.

A later exhaustive rerun phase-shifted each closed black-count walk to a minimum, so every retained prefix balance was nonnegative. It covered the same 2,048 prefix ranks, retained 342 normalized valid prefixes, visited 5,610,368 nodes, and again found zero hits. The compact source-hash audit is `langton_zero_growth_p40_dyck_audit_2026-07-14.json`.

Thus, conditional on the proved pruning lemmas and the exact implementation, this calculation excluded nonzero-drift zero growth at period 40. The later theorem immediately below now subsumes it at every period. The computation is retained as an independent audit of the exact trace checker.

##### Analytic exclusion of every zero-growth periodic highway

There is no clean finite translator: no finite black pattern and ant state can recur as exactly one nonzero translate of itself with restored heading.

To see this, rotate its already-proved axis-aligned drift to $d=(L,0)$ and quotient the bi-infinite clean orbit by $d$. Every quotient vertex has $2k_v$ visits, with exactly $k_v$ R and $k_v$ L turns, because the corresponding physical cell is white before its first and after its last visit. Let $H$ and $V$ be the horizontal and vertical edge multiplicities of the projected closed trace. At each vertex,

\[
H_-+H_+=V_-+V_+=2k_v.
\]

Horizontal edge parity is therefore constant along each row; call it $h_y$. Vertical edge parity is constant down each column and vanishes outside the finite footprint, so every vertical multiplicity is even: $V_e=2G_e$. The exact local turn-parity formula gives $k_v\equiv h_y\pmod2$ at both HV cell types. Dividing the vertical incidence equation by two gives

\[
k_{x,y}=G_{x,y-1/2}+G_{x,y+1/2}.
\]

Summing over all rows in a fixed column cancels every $G$ twice, so $\sum_yh_y$ is even. But modulo two this sum is exactly the winding number of the closed trace across a cylinder seam. A translator lifted from $p$ to $p+d$ winds once, a contradiction.

Every zero-growth repeating trace with nonzero drift eventually separates into stationary debris plus a clean moving packet, so the theorem excludes it. Zero drift would confine the ant to the finitely many positions of one period. Negative growth cannot continue forever, and heading reset makes growth a multiple of four. Consequently every finite-support periodic highway has strictly positive black growth divisible by four. This still permits the ordinary highway, whose growth is 12.

#### 5. Exact Tait-graph / boundary-loop reformulation

The checkerboard HV partition gives a planar reformulation that exposes more topology than the raw cell colors. Normalize the ant so even cells receive vertical arrivals and odd cells receive horizontal arrivals. In the frozen all-white routing, admissible directed arcs form clockwise four-cycles around one checkerboard class of plaquettes.

There is also a basic modular conservation law. Number headings by (0,1,2,3) so a right turn adds one, and let (|B_t|) be the number of black cells. Every right turn increases both the heading and (|B_t|) by one, while every left turn decreases both by one. Hence

\[
q_t-|B_t|\equiv q_0-|B_0|\pmod 4.
\]

In particular, a heading-resetting period changes the black-cell count by a multiple of four.

Take those plaquettes as vertices of a rotated square lattice. Each ant cell is the crossing of exactly two such white cycles and therefore corresponds to one lattice edge. Explicitly, for an ant cell (z=(x,y)), label a plaquette by its lower-left corner and define

\[
e_z=\begin{cases}
\{(x,y-1),(x-1,y)\},&x+y\text{ even},\\
\{(x-1,y-1),(x,y)\},&x+y\text{ odd}.
\end{cases}
\]

Let (H_B) be the finite edge-subgraph consisting of (e_z) for black cells (z\in B). White and black are the two smoothings of the corresponding directed crossing. Consequently:

1. the frozen routing loops are the boundary components of a regular neighborhood of (H_B), together with untouched four-cycles;
2. the ant moves along its current boundary loop and then toggles the edge (e_z); and
3. every step either merges two frozen loops or splits one frozen loop into two.

This is an exact conjugacy, not a heuristic picture. It is implemented by `tait_edge` and `tait_graph_stats` in the supplied code.

If (E=|B|), (V) is the number of incident Tait vertices, (k) is the number of nonempty components, and

\[
\beta=E-V+k
\]

is the cycle rank, then the regular neighborhood has (k+\beta=E-V+2k) boundary components. Relative to the (V) separate white plaquette cycles, the loop-count change is

\[
\Delta C=E-2V+2k,
\qquad E+\Delta C=2\beta.
\]

Thus adding a white edge between different components merges two loops and leaves (\beta) unchanged; adding an edge within a component splits a loop and increases (\beta) by one. Removing a bridge splits a loop and leaves (\beta) unchanged; removing a nonbridge merges two loops and decreases (\beta) by one.

Once a new bounding-box record lies outside the finite initial black support, its first visit is white; a new east, north, west, or south record then turns respectively south, east, north, or west. In the Tait graph its new edge has an endpoint in a previously untouched plaquette, so it is a bridge: every sufficiently advanced record expansion merges the active loop with a fresh four-cycle and leaves (\beta) unchanged. Therefore any unbounded production of cycle rank must occur strictly inside territory that has already been explored.

This rules out several tempting proof ideas. The active loop length, its signed area/orientation, the black-edge count, the component count, and the cycle rank all fail to be monotone, with explicit failures already on the blank trajectory. The active loop can shrink by hundreds of arcs in one step.

The standard highway has a particularly rigid graph form. Starting from the 13-black-cell immediate seed, after a short finite settling phase its active component is a translated unicyclic graph with 16 vertices and 16 edges. Each 104-step period leaves the active core unchanged up to displacement and sheds a separate 13-vertex, 12-edge tree. The total cycle rank remains two. The existing gateway induction makes this observation exact for all subsequent periods.

#### 6. The attempted universal proof and its exact failure point

The most plausible proof route is to study record frontiers. For a diagonal functional, for example

\[
h(t)=\max_{0\le s\le t}(x_s+y_s),
\]

once (h(t)) exceeds the finite initial support, the half-plane beyond the record frontier is untouched and white.

If the following lemma could be proved, the rest could be made finite and rigorous.

##### Missing bounded-retreat lemma

For every finite-support initial configuration, there exist a diagonal direction, a time (T), and a width (W<\infty) such that after (T):

1. the ant never retreats more than (W) layers behind its current record frontier; and
2. all transverse excursions remain in a width-(W) corridor.

Under this lemma, the colors in a bounded frontier window, the ant's position in that window, and its direction form a finite state modulo translation. Determinism then makes the frontier dynamics eventually periodic. The periodic-trace criterion above can classify the resulting cycles and decide whether each is the standard highway.

No proof of the bounded-retreat lemma is known. Unboundedness and finite-domain escape do not imply it: an orbit may keep expanding a two-dimensional region while escaping every fixed box. Moreover, the symbolic trace system on the square grid has infinite-memory effects, so a finite-state argument cannot hold for arbitrary backgrounds; it would have to exploit finite support in an essential way. See [Gajardo, *A symbolic projection of Langton's Ant*](https://doi.org/10.46298/dmtcs.2312).

This is the central gap. Claiming that “the ant eventually forgets its interior” without proving this lemma would simply assume the difficult part of the conjecture.

In the Tait formulation, the missing lemma can be sharpened: one needs to show that the boundary component carrying the ant eventually has a bounded translating core and that components shed behind it can no longer be reabsorbed. A bound on any single scalar invariant is insufficient.

The most tempting pumping argument fails for a precise reason. Even if the same bounded neighborhood of the ant recurs modulo translation, the two boundary strands visible in that neighborhood may or may not be connected through an arbitrarily distant part of the previously explored Tait graph. That nonlocal connectivity determines whether a later edge toggle merges two loops or splits one. Thus equality of a local core does not by itself determine the future. A valid finite-state proof must first establish permanent separation from the discarded graph (or encode an equivalent finite connectivity summary); assuming that separation is exactly assuming the unresolved part.

##### Exact loop-memory trichotomy

The nonlocal obstruction can now be stated more sharply. Freeze the coloring before a step and let (\Gamma_t) be the frozen routing cycle containing the ant. Toggling the current cell swaps the successors of the two opposite incoming strands. If those strands lie on different frozen cycles, the swap merges them; if they lie on the same cycle, it splits the cycle. Timestamp the inactive daughter created by a split. It remains literally unchanged until a later merge reabsorbs it.

If active-cycle lengths are eventually bounded by (L), and every reabsorbed non-pristine daughter has age at most (A), then the active cycle together with the at most (A+1) recent daughters is a finite packet modulo translation. Every stored loop has length at most (L) and lies within distance (A+L) of the ant. The packet update is deterministic: an opposite strand not belonging to the active or stored loops must belong to the canonical pristine white four-cycle. A packet repeats, yielding a periodic turn word and a fixed nonzero drift; zero drift would contradict unboundedness.

Consequently every finite-support orbit satisfies at least one of:

1. active frozen-cycle lengths are unbounded;
2. reabsorption ages of non-pristine shed cycles are unbounded; or
3. the orbit eventually follows a translating periodic word.

If a length-(L) daughter is reabsorbed after (D) steps, the excursion endpoints are within (L), while the fixed-domain escape bound forces the excursion to visit at least (\lceil\log_2D\rceil) distinct cells. Thus the second obstruction is specifically a sequence of larger and larger near-return excursions, not an unspecified "memory of the interior." Whether bounded active length alone rules out such unbounded ages remains open.

Jordan separation narrows it further. If the active ant is left on the bounded side of a shed length-(L) loop, it is confined to (O(L^2)) cells until reabsorption, giving an explicit finite delay bound. Any unbounded-age sequence must therefore consist of exterior-side excursions around small stationary marker loops. Exact charge-neutral four-cell patterns can store arbitrarily many such markers, so the row/column and mod-four charges do not eliminate this case. A complete proof must use the forced visit/root order to forbid self-generated arbitrarily long exterior returns.

Three later lemmas sharpen this gap. If active frozen-loop length is eventually at most $L$, the opposite partner loop is also at most $L$, and every temporal segment through pairwise distinct cells has length at most $L$. For finite memory it is enough to bound only black-cell lifetimes: if every R visit is followed by that cell's next, necessarily L, visit within a uniform time, the last bounded number of relative positions and turns determines the future and the ant must enter a translating periodic word. Thus a non-highway orbit must leave cells black for arbitrarily long times before revisiting them.

Also, bounded black count bounds all active frozen loops by the total affected boundary length. Combining that fact with the bounded-loop/age theorem and the even-winding obstruction shows that any bounded-black-count orbit must reabsorb non-pristine loops after unboundedly large delays.

The exact Tait split taxonomy leaves two exterior memory carriers: inner hole markers created by cycle-edge additions, and outer island markers created by bridge removals. A bridge can lie in a bounded face, in which case an inner parent splits into an inner and an outer daughter; omitting this case gives a false classification.

There is also an exact root-order anchor. An R visit leaves a fixed successor arc at that black cell until its next L visit. Under active-loop bound $L$, the frozen cycle carrying this seam always has length at most $L$. If every uninterrupted inactive episode of the seam lasts at most $D$, arbitrarily many dock/undock cycles still keep the whole black lifetime inside radius $L+D$; finite-state counting bounds its duration. Consequently a bounded-loop non-highway requires individual non-pristine seam loops to stay inactive for unbounded times. The surviving loophole is now one genuinely long exterior episode, not merely an unbounded count of short dock/undock cycles.

Finally, a quantitative non-isolation theorem shows that, for every $A$, an explicitly sufficiently long black-cell lifetime contains the ending time of another lifetime longer than $A$. The intervals need not be nested—they can cross—so this gives temporal clustering rather than an infinite descent. Controlling those crossing lifetime chains is a new concrete route toward the remaining memory theorem.

The exact diagnostic code reproduces this mechanism. Through 20,000 blank-orbit steps, the maximum active length is 1,388 and the maximum non-pristine reabsorption age is 4,414; neither maximum increases after the step-9,977 highway onset. On the certified immediate gateway, the corresponding maxima are 152 and 90 through 200 periods. These finite measurements are not universal bounds.

A targeted exact search found a substantially stronger exterior witness in the centered $3\times3$ seed `#.#/#.#/#.#`. A length-eight inner marker is shed at step 14,989, remains literally unchanged, and is reabsorbed at step 38,262, for age 23,273. During the exterior-side excursion the ant reaches Manhattan distance 68 from the shed point and returns within distance three. Redundant daughter tracing and the independent reference diagnostic agree on all event counts. This is a finite witness, not an unbounded-delay proof; the same seed is already known to reach the standard highway later.

##### New exact charges and translator restrictions

Let (b_t=|B_t|). Since a white/R step increments both heading and black count and a black/L step decrements both,

\[
q_t-b_t\equiv q_0-b_0\pmod4,
\qquad
p_{t+1}-p_t=u_{q_0-b_0+b_{t+1}}.
\]

Thus the complete spatial path is determined by the one-dimensional black-count walk, subject to the independent cell-alternation constraint.

There are also exact Laurent-polynomial charges over (\mathbf F_2):

\[
\sum_{(x,y)\in B_t}X^x+[q_t\text{ vertical}]X^{x_t},
\qquad
\sum_{(x,y)\in B_t}Y^y+[q_t\text{ horizontal}]Y^{y_t}.
\]

Together with mod-four first-moment charges, they prove that any *clean* finite translator—one whose entire black set and ant recur translated, with no wake—must be axis-aligned, have period divisible by eight and at least 16, and have drift $(4a,0)$ or $(0,4a)$. A complete degree-two additive-charge audit finds one extra quadratic mod-four class, $Q(x,y)=x^2+2xy$, but proves that it gives no stronger endpoint restriction once the drift is an axis multiple of four. This clean-translator theorem does not apply to the ordinary diagonal highway, because that highway continually emits debris.

For an exact repeating word, let (g=\#R-\#L). The stabilized translation classes show that (g) equals the number of odd alternating classes, so (g\ge0) and heading reset makes (g) a multiple of four. Each odd class becomes one solid translation-orbit strand in the wake. If (g>0), the centered first-moment identity proves that some black cells remain at distance at least ((\|d\|/2)n-O(1)) behind the ant after (n) periods. A growing highway therefore cannot have its entire black support in a bounded moving window.

The winding argument also forces every residue modulo each nonzero drift coordinate to carry a positive even number of odd classes. If $d=(a,b)$, then

\[
g\ge2\max(|a|,|b|).
\]

The earlier Laurent charges forced those residue counts to be even but allowed zero; intersection with the translation-cylinder seam forces them to be nonzero. This bound is sharp for static aggregate-flow profiles, although the equality profiles found in the audit are not single chronological ant traces.

More precisely, every repeated trace has a canonical endpoint decomposition into a finite moving widget, a finite stationary correction, and exactly (g) solid (d)-spaced strands. The Laurent charges force an even number of strand bases in every drift-coordinate residue class and determine the moving-widget parity; the mod-four charge then gives a congruence involving only the drift and strand bases. For the normalized standard word this decomposition is exactly two stationary black cells, an 11-cell moving widget, and 12 strands; hence (|B_n|=13+12n) at period boundaries.

If $g=0$, the stationary part eventually separates from the path, and deleting it leaves a genuine clean translator. The even-winding theorem above excludes that translator at every height and period. The earlier corner-free footprint bound $N\ge8|d|$, small-height cylinder algebra, and period-40 search are retained in the proof journal as the route to this stronger result, but they are no longer needed to eliminate zero growth.

The clean first-moment equation also reduces to four residue totals and can be exhaustively enumerated over its unbounded starting black count. Exactly 362 edge-multiplicity profiles survive at period 40 and 4,707 at period 48. Thus every period-48 candidate has a phase with at most 11 moving black cells and never more than 25. An explicit surviving profile exists for every $N=8h\ge24$, so this arithmetic obstruction is useful pruning but cannot prove the conjecture by itself.

##### Collision-chain and lifetime interlacement theorems

There is now an exact endpoint theorem for every finite run. Regard a changed cell $(x,y)$ as the edge between a column vertex $C_x$ and a row vertex $R_y$. Associate to an ant state the column token $C_x$ when its heading is vertical and the row token $R_y$ when its heading is horizontal. Over $\mathbf F_2$, the boundary of the row-column incidence graph of $B_s\mathbin\triangle B_t$ is exactly the sum of the two endpoint tokens. Intermediate tokens telescope across arbitrary collision checkpoints. Hence at most one defect component is non-Eulerian, and a same-pose return has only Eulerian defect components.

This yields a sharp local chronology theorem. If an R visit to a cell is followed by its next, necessarily L, visit, the odd-visit support between them contains the paired cell and has even degree in every exact row and column. It therefore contains at least four distinct cells. Parallel arrivals align the two pre-turn directed poses; opposite arrivals align the two post-move poses. Explicit checker-signed mod-four row and column charges then determine the add/remove signs of a minimum four-corner rectangle from the arrival type and the two side parities. The exact potentials and sign algebra are machine checked in Lean. The theorem forces interlacement but is sharp: the standard highway itself has unit-square four-cell examples.

At an L collision, the occupied Tait edge is a bridge exactly when the live and opposite roots lie on the same frozen boundary; deletion then splits that boundary. A nonbridge puts the roots on distinct boundaries and deletion merges them. This exhaustive local classification still does not control the eventual drift. In the exact obstacle reversal, an ancestral degree-one leaf bridge in a 34-edge component splits a length-120 boundary and ejects the ant onto a pristine live four-cycle, yet the eventual standard drift reverses from $(-2,2)$ to $(2,-2)$. The return stores its 524 changed cells in one endpoint-neutral Eulerian incidence component of cycle rank 444.

An attempted touch-graph/interlacement compression was later found to lose information
under the pushforward from distinct lifetime labels to physical row/column labels.
The labelled cycle-space theorem therefore does not imply a full physical touch-graph
rank theorem, and no such theorem is claimed in the paper. A narrow growth-four port-
matching audit does show that the abstract wake kernel has $\kappa=1$ for axis drift,
$\kappa=2$ for even diagonal drift, and $\kappa\in\{1,2\}$ for primitive diagonal
drift. Natural oriented coordinate functionals are noninjective on this kernel; this
is a negative result, not the signed all-$+1$ wake-residue theorem. Controlling the
physical chronology remains open.

#### 7. Best disproof program

There are two certificate-producing searches worth scaling:

1. **Alternative highways.** Search periodic words with the exact criterion. A hit gives a finite seed and an inductive proof immediately. A non-104 hit—or a nonstandard period-104 hit—disproves the unique-highway formulation.
2. **Self-enlarging widgets.** Search for a finite pattern that returns after (K) steps with one or more repeated boundary widgets added. An algebraic induction on the number of widgets would prove an increasing, nonperiodic trajectory and disprove even the broad “some highway” statement. Generalized ants are now known to have precisely such finite-seed increasing behaviors, but none is known for the classical two-state ant. [Lutfalla (2025)](https://arxiv.org/abs/2505.05426)

Merely running one configuration for (10^{20}) steps without seeing a highway would not be a disproof. A counterexample needs a finite invariant or a parameterized recurrence proving its behavior for all time.

#### 8. Using a large compute cluster

The supplied program supports independent shards.

To divide the periodic-word search, assign every (R/L) prefix of a fixed length to a separate job:

```powershell
python outputs\langton_research.py search-highway-words `
  --max-period 103 `
  --prefix RLLRLRRLLRRL `
  --node-cap 1000000000 `
  --output result_RLLRLRRLLRRL.json
```

The union of all prefixes of the selected length covers the complete tree. Every shard must report `"search_complete": true`; a capped shard proves nothing about its unexplored remainder.

The Hamming-sphere search is also shardable. For example, the distance-six sphere around the standard word contains 1,517,381,580 candidates, so a cluster can divide it by combination rank:

```powershell
python outputs\langton_research.py search-standard-hamming `
  --distance 6 --shards 4096 --shard 0 `
  --output hamming6_shard_0000.json
```

Run shard indices 0 through 4095 and require every output to finish. The implementation un-ranks the first combination in each contiguous interval directly, so a worker does not scan combinations assigned to other shards. Each shard contains about 370,455 candidates; shard zero completed 370,454 candidates in about 90 seconds on the reference machine and found no highway. A zero score is not merely suggestive: the program immediately applies the exact periodic-trace checker and emits the finite black seed.

To divide an exact (4\times4) configuration search, partition the integer interval ([0,65536)):

```powershell
python outputs\langton_research.py exhaustive `
  --side 4 --exact --max-steps 10000000 `
  --start 0 --stop 4096 `
  --output exact_4x4_00000_04096.json
```

Again, an `unresolved_count` greater than zero means only that the time cap was reached. It is not a counterexample.

For serious scaling I would next replace the Python depth-first engine with a compiled, work-stealing implementation and add checkpointed prefix queues. The exact periodic criterion and gateway verifier can remain the trusted reference checker.

#### 9. Current conclusion (superseding the historical list)

There is still no universal proof or counterexample. The release establishes only the
claims proved in `../paper/main.tex`:

- an exact constructive criterion deciding whether a proposed heading-resetting,
  nonzero-drift periodic word is realizable from finite support;
- an exact Tait-graph conjugacy and planar cycle-rank surgery identity;
- an even-winding proof that no clean finite translator exists, implying that every
  finite-support periodic highway has positive growth divisible by four;
- a signed mod-four wake-residue identity and the bound
  $g\ge2\max(|a|,|b|)$;
- a two-endpoint row/column collision-chain parity theorem and the resulting
  four-cell lower bound for a completed black lifetime; and
- a residue-theorem-free, rank-audited computation excluding every finite-support
  periodic highway of nonzero drift and period at most $48$.

Selected algebraic kernels are checked in Lean 4, but the extraction of the required
geometric trace certificate is not formalized end to end. The two unresolved duties
are a universal bounded-active-core/entrance theorem and an unbounded-period
classification of all positive-growth periodic highways. Computation may find a
finite counterexample certificate or extend a bounded exclusion, but cannot by itself
close either infinite gap.

<a id="source-research-notes-line-parity-research-2026-08-18-md"></a>

## line_parity_research_2026-08-18

Source: `research-notes/line_parity_research_2026-08-18.md`.

### Line-parity theorems and the transverse mod-four level law — 18 August 2026

Supersedes `transverse_mod4_theorem_draft.md`, which stated a weaker special case
and leaned on the residue theorem for a step that turns out to be free.

The sections below are dated research checkpoints and include failed routes
and later corrections. Primitive-diagonal growth four was subsequently excluded
by [the computer-assisted top-boundary classification](03_Growth_four.md#source-research-notes-primitive-g4-cap5-symbolic-2026-08-22-md);
its earlier open-case discussions are historical. The growth-eight problem remains open.

#### 0. Summary

Four analytic identities hold at every period for diagonal drift. Use the four
integer linear projections `t=x+y`, `u=x-y`, `x`, and `y`. The first two change
by `+-1` at every ant move; `x` and `y` change by `+-1` on their respective axes
and stay constant on the other axis. On the moves that change it, each projection
gives a signed walk on `Z`. For `t` and `u`, extrema are determined by the turn
and arrival axis; for `x` and `y`, reversals are determined by flanking turn pairs.
Comparing extremum counts with cut flow gives a parity law per line.

The transverse one, `T1`, is the strong one:

```text
T1  at every horizontal-arrival level line:  #L is even
    at every vertical-arrival   level line:  #R is even
```

For finite-support traces, start-R alternation makes this equivalent to
`m_t = +-omega_t (mod 4)`. This refines the growth corollary by giving a
congruence at each transverse level.

`T1` alone re-derives the report's growth congruence, `growth = 0 (mod 4)`,
by an independent route, and at primitive-diagonal growth four it forces the
3-1 checker split of the wake **without** the signed residue theorem.

Status: proved analytically and verified on 26 genuine highways.
Sections 8 and 10 record corrections to the frame and hypotheses. T1, T2 and
the transverse mod-four consequences are promoted in the paper; T3 and T4 remain
audited research-note results.

#### 1. Frame

After a half-turn if necessary, write
the diagonal drift as `d=(m,-m)` with `m>=1`, and put `t(x,y)=x+y`. Rotations are
the only symmetries of the chiral rule, and the four diagonal directions form one
rotation orbit, so this is free. Then `t(d)=0`, every move changes `t` by exactly
`+-1`, and each level line is entirely horizontal or entirely vertical
(Proposition hv).  Normalise the level index so that the **horizontal-arrival
levels are the odd ones**.

Write `u = x - y`; then `u(d) = 2m`, and every move also changes `u` by exactly
`+-1`.  Levels of `x` change only on horizontal moves and levels of `y` only on
vertical moves.

`m_{t,r}` is the number of period events in the translation class `(t, x mod m)`,
`m_t = sum_r m_{t,r}`, and `omega_t` is the number of classes at level `t` with
`m_{t,r}` odd.  The wake is exactly the set of odd classes, so
`sum_t omega_t = growth`.

#### 2. The three inputs

**(I1) Class-to-cell bijection.**  Every cell of the class `(t,r)` is visited
exactly `m_{t,r}` times over the whole bi-infinite trace, and the period events of
the class biject with the visits to any one of its cells: if the period events are
`(i_k, x_k)`, the visits to the cell with longitudinal coordinate `X` are the
`m_{t,r}` times `i_k + ((X-x_k)/m) N`, and `m | X-x_k` because the class
`(t, x mod m)` is exactly one orbit of the translation group generated by `d`.
The visit order is by the key `i_k m - x_k N`, which does **not** depend on `X`, so
all cells of the class carry the *same* turn word.

**This is where a hypothesis enters, and it must be stated.**  We need that word to
be `R,L,R,L,...`, i.e. that the cell is white at its first visit.  For a
bi-infinite periodic trace on its own that is false: it is a free initial condition
at time `-infinity`, not a consequence.  Explicit counterexample, a genuine closed
heading-reset trace of period 10 with drift `(1,-1)`:

```text
w = RLLLLRLRRR      stabilised class words   t=-1: R   t=0: RLRL   t=1: RLRL   t=2: L
w = RRLRLLLLRR      stabilised class words   t=-1: R   t=0: LRLR   t=1: LRLR   t=2: L
```

The singleton class at `t=2` turns `L`, so that cell is black at its first visit,
and T1's mod-four form fails there.  (Both words have `#R-#L = 0`, so they are
excluded as highways by the even-winding theorem, but they are legitimate objects
of the bi-infinite periodic category.)

What rescues the argument is **finite support**: for a periodic highway arising
from a finite initial black set, every cell sufficiently far ahead is untouched and
white, and since all cells of a class share one turn word, that word begins with
`R` for every class.  This is exactly condition (ii) of the paper's periodic
realisability criterion --- the stabilised word begins with `turnR` --- and is the
same hypothesis the paper's extremal-rigidity and width theorems use.  Under it the
class contributes `ceil(m_{t,r}/2)` right turns and `floor(m_{t,r}/2)` left turns
to one period.

The turn-counting forms T1--T4 are kinematic statements about periodic traces and
hold without finite support.  The mod-four consequences obtained by replacing a
class turn count with `ceil(m/2)` or `floor(m/2)` do require (I1), hence finite
support.  This distinction is essential below.

**(I2) Reflect/continue rule.**  In the normalised frame,

```text
odd  level (horizontal arrival, vertical departure):  R  <=>  t reverses
even level (vertical arrival, horizontal departure):  R  <=>  t continues
```

and dually, since each turn flips exactly one of the two diagonal senses,

```text
odd  level:  R  <=>  u continues
even level:  R  <=>  u reverses
```

*Proof.*  At an odd level the incoming heading is `E` or `W` and the outgoing is
`N` or `S`.  Incoming `E` raises `t` and raises `u`; the right turn from `E` is
`S`, which lowers `t` and raises `u`.  So `R` reverses `t` and continues `u`.  The
right turn from `W` is `N`: `W` lowers both, `N` raises `t` and lowers `u` — again
`t` reverses, `u` continues.  At an even level the right turn from `N` is `E`
(`N` raises `t`, lowers `u`; `E` raises both) and from `S` is `W`; in both cases
`t` continues and `u` reverses.  []

**(I3) Extremum/flow parity.**  Two versions are needed, because the four walks
are not all of the same type.

*Bounded case (`t`).*  The `t`-walk is bounded and `N`-periodic, so it visits every
level infinitely often; the right object is the **one-period quotient walk**, which
is closed because `t(d)=0`.  Take `nu_v = m_v` (events per period at level `v`) and
`F_v = 0` (each cut is crossed equally often in both directions per period).

*Drifting case (`u`, `x`, `y`).*  These walks are not monotone step by step.  Rather,
for a period phase `i`, their value at time `qN+i` is the phase value plus `q` times
the corresponding drift coordinate.  They are therefore proper in the period
index: each exact value is visited finitely often over the bi-infinite trace and
each exact cut has algebraic net crossing number `F = +1` for `u` and `x`, and
`F = -1` for `y`, when `d=(m,-m)`.  Only `F mod 2` is used below, so the sign of
`F_y` does not matter.

In either case, with `nu_v` visits, `U`/`D` up- and down-crossing counts, and
`rho_v` the number of visits at which the walk reverses,  Counting the four
in/out combinations at `v` gives

```text
nu_v = U_{v-1} + D_v ,   max_v - min_v = U_{v-1} - U_v ,   rho_v = max_v + min_v,
```

with `U` and `D` the up- and down-crossing counts, `U_v - D_v = F_v`.  Therefore

```text
rho_v = nu_v + F_v   (mod 2).
```

#### 3. The four theorems

Combining (I1)–(I3):

**T1 (transverse).**  The `t`-walk is closed, so `F = 0` and `rho_t = m_t (mod 2)`.
By (I2) the reversals at an odd level are its right turns and at an even level its
left turns, so `rho_t = sum_r ceil(m_{t,r}/2)` resp. `sum_r floor(m_{t,r}/2)`.
Writing `m_{t,r} = 2q+e`:

```text
odd  level:  #L_t = sum_r q  is even,   hence  m_t =  omega_t (mod 4)
even level:  #R_t = sum_r (q+e) is even, hence m_t = -omega_t (mod 4)
```

**T2 (longitudinal).**  The `u`-walk drifts, so `F = 1` and `rho_v = nu_v + 1`.
All cells of one `u`-line lie at levels of one parity, because `t = u (mod 2)` in
the *unshifted* index; with the shift `c` that makes horizontal arrivals odd, the
line `u=v` carries levels of parity `(v+c) mod 2`.  Pairing `u`-parity with the raw
`x+y` parity instead gets the statement backwards on the standard highway, which
needs `c=1`.  By (I2) the `u`-reversals
at an odd level are its left turns and at an even level its right turns, so

```text
u-line at odd  levels:  #R on the line is ODD
u-line at even levels:  #L on the line is ODD
```

**T3, T4 (column and row).**  Because a quarter turn is taken at every step, the
heading axis alternates, so two consecutive horizontal moves are separated by
*exactly one* vertical move and "the two turns between them" is a well-defined pair.
Over all four headings and all four turn pairs, the second horizontal heading equals
the first exactly when the two turns differ; hence an `x`-reversal is a vertical move
whose flanking turns are **equal**.  Counting per residue class `v mod m` over one
period (translation by `d` identifies column `v` with column `v+m`, so this is the
same as counting per actual column over the whole orbit), and writing `nu_v` for the
number of horizontal moves landing in that class,

```text
#{vertical moves in class v with equal flanking turns} = nu_v + 1  (mod 2)
```

and symmetrically for rows and horizontal moves.  The `+1` is the net flow across a
column cut, which is `1` and not `m`: the displacement `m` is spread over `m`
distinct cuts.  Stating the counting class matters --- over a whole trajectory the
identity holds exactly where the net flow across the cut is odd, and it fails by one
parity on the transient columns behind the start, where the net flow is zero.

*Unverified side remark, do not promote:* it looks as though `T3` and `T4` follow
from `T1` and `T2` when `m = 1` and are independent for `m >= 2`, but neither half
has been checked.  No derivation of `T3` from `T1+T2` has been attempted, and no
configuration satisfying `T1,T2` while violating `T3` has been exhibited.  That all
26 genuine highways pass all four is consistency, not independence.

#### 4. Consequences

**(C1) Growth is `0 (mod 4)`, re-derived.**  From `m_t = f_{t-1} + f_t` and
`m_t = (-1)^{t+1} omega_t (mod 4)` one gets, by induction from `f_{T'-1} = 0`,

```text
f_t = (-1)^{t+1} G_t   (mod 4),     G_t = sum_{s <= t} omega_s .
```

At the top cut `f_T = 0` and `G_T = growth`, so `growth = 0 (mod 4)`.  This is a
second route to the paper's growth corollary, using chronology rather than cylinder
homology --- but it is **not** a strengthening: it assumes (I1), i.e. condition (ii)
of the realisability criterion, whereas the even-winding argument does not.  The
period-10 words above are exactly the objects that separate the two routes.

**(C2) `f_t` is never `0 (mod 4)` unless `G_t` is.**  At growth four this gives
`f_t` not divisible by four on every interior cut, but only after C5 below supplies
`f_{T'} = f_{T-1} = 1`, which forces `G_t in {1,2,3}` there; C2 is therefore
downstream of C5, not independent of it.

**(C3) Primitive diagonal, growth four: the 3-1 split is free.**  For `m = 1` each
level is a single class, so `omega_t = m_t mod 2` and

```text
t odd  :  m_t = 0 or 1 (mod 4)
t even :  m_t = 0 or 3 (mod 4)
```

Every level of even multiplicity therefore has `m_t = 0 (mod 4)`, hence `m_t >= 4`.
Let `a` and `b` count the four wake levels at odd and even `t`.  Then
`N = sum_t m_t = a + 3b (mod 4)`.  The `N/2` horizontal moves have net displacement
`1`, so `N/2` is odd and `N = 2 (mod 4)`, giving `a - b = 2 (mod 4)`; with
`a + b = 4` only `(3,1)` and `(1,3)` survive.  The tie is broken by the paper's
extremal-line rigidity, clause (i): **both extremal level lines are horizontal**,
so both are odd levels, and clause (iii) makes their classes singletons, so each
contributes `omega = 1`; hence `a >= 2` and `(a,b) = (3,1)`.
**No appeal to the signed residue theorem is needed** --- but the appeal to
extremal rigidity is essential, and without it the mirror normalisation gives
`(1,3)` and `N = 2 (mod 8)` instead.  (`T2` does *not* give this split a second
way: at `m=1` the two `u`-line classes are the two level-parity classes, so given
T1 the statement of T2 is equivalent to `N/2` odd, which is already an input.)

**(C4) `N = 6 (mod 8)` at primitive-diagonal growth four.**  `sum_{t odd} m_t = N/2`
counts horizontal arrivals and is `a = 3 (mod 4)`.

**(C5) Boundary pinning.**  `f_{T'} = f_{T-1} = 1` from extremal rigidity, and
non-negativity of the extremum counts gives `|f_{t-1} - f_t| <= rho_t`, i.e.
roughly `max <= 3 min` on adjacent cuts.  Hence `f_{T'+1}, f_{T-2} in {2,3}` and
`m_{T'+1}, m_{T-1} in {3,4}`; at most one of them is `3`, because only one even
level is a wake level.

#### 5. What this does *not* do

It does **not** close primitive-diagonal growth four.  The level system
(`code/python/primitive_g4_level_dp.py`) remains feasible for every even
`W >= 4` once the constraints of §4 are imposed; the surviving profiles are thin,
of the shape `f = (1,3,2,2,...,2,2,1)` and its reversals, with `N = 4W - 2` at the
minimum.  Two gaps remain:

1. the level system is finite for each `W` (adjacent cuts differ by at most a
   factor of about three, and `f = 1` at both ends, so `f_t <= 3^{min(t-T', T-t)}`),
   but `W` itself is unbounded;
2. the finer data — the per-level arrival strings and the requirement that the
   induced phase successor be a single `N`-cycle — has not been searched.

The rank-parity sign identity of Sections 41–42 of the journal, transported to the
one-lane primitive case, yields

```text
K = 1 + sum_t ceil(f_t/2) + sum_{t odd} f_t f_{t+1}   (mod 2)
```

and under the growth-four structure this reduces to `W = 0 (mod 2)`, which is
already known.  So that route adds nothing here; the sign identity is the mod-two
shadow of the single-cycle condition and is already saturated.

#### 6. Reproduction

```text
code/python/line_parity_theorems_audit.py    # all four theorems, 26 genuine highways
code/python/line_parity_sublemma_audit.py 14 # exhaustive (I2)/(I3) check, 8,532 words
code/python/primitive_g4_level_dp.py 20      # the level system that remains feasible
```

`line_parity_theorems_audit.py` simulates Langton's ant from the empty plane and
from 25 random finite seeds, locates the period-104 highway in each, rotates it to
the normalised frame, and checks `T1`–`T4` by direct turn counting.  All 26 pass in
every orientation that occurs.  `line_parity_sublemma_audit.py` checks the
reflect/continue rule and the extremum/flow identity on *every* closed
diagonal-drift heading-reset word of every even length up to 14 — 114,520 step
checks, no failures — so those two lemmas are not being taken on trust from a
single example.

#### 7. Second-line rigidity, and where primitive-diagonal growth four actually dies

##### 7.1 A new forcing one level inside the rail (primitive diagonal, proved)

Extremal-line rigidity fixes the extremal level.  For `m=1` it also fixes the
*next* one completely.  Normalise `T'=1`, so level 1 is the bottom rail: one event
per period, at longitudinal coordinate `X`, arriving `W` from the level-2 cell at
`X+1` and leaving `N` to the level-2 cell at `X`.

Level 2 is a vertical-arrival level with `m_2 = 1 + f_2`.  Exactly one of its events
arrives from below and exactly one leaves downward.  At a vertical level T1 gives
`rho_2 = floor(m_2/2)`, so the number of pass-throughs is
`m_2 - rho_2 = ceil(m_2/2)`; these split into up-passes and down-passes, and there is
exactly one of each, so `ceil(m_2/2) = 2` and hence `m_2 in {3,4}`.  (Stating this as
"at most one arrival from below, so `ceil(m_2/2) <= 2`" is not enough on its own ---
that leaves `m_2 in {1,2,3,4}`; exactness, or integrality of `A_0`, is what removes
`{1,2}`.)

T1 also gives `A_0 = ceil(m_2/2)/2 = 1`, so the unique arrival from below sits at an
**even** stabilised rank, and therefore `A_1 = 1 - A_0 = 0`: **no odd rank arrives
from below**.  That is what places the downward departure.  By the reflect/continue
rule at a vertical level, a departure is downward either at an even rank with
`a_r = 0` or at an odd rank with `a_r = 1`; the second set is empty because
`A_1 = 0`.  So the unique downward departure sits at the other even rank.  This uses
only T1 and the reflect/continue rule --- **not** the rank-parity identity of
section 5.  The downward departure is the predecessor of the rail
event, at `x = X+1`; the arrival from below is its successor, at `x = X`.  Since
stabilised rank decreases in `x`, the predecessor outranks the successor, so

```text
a^{level 2} = (0,0,1)      if m_2 = 3,
              (0,0,1,0)    if m_2 = 4,
```

with rank 0 the downward departure, rank 2 the arrival from below, and ranks 1
(and 3) local minima.  ("Rank 0" means the first visit; the predecessor *comes
first*, it does not "outrank" the successor in the colloquial sense.)  Explicitly,
the predecessor has key `i-1-N(X+1)` and the successor `i+1-NX`, differing by
`-(N+2) < 0`, so the predecessor is strictly earlier and ties are impossible.

The top rail gives the same two strings but **not** by mechanically mirroring the
sentence: there the ant arrives `E` from `x = X-1` and departs `S` to `x = X`, so the
predecessor sits at the *smaller* `x` and takes the *larger* rank.  Working it
through gives down-pass at rank 0, up-pass at rank 2, local maxima at ranks 1 and 3,
i.e. `a^{T-1} = (0,1,1)` or `(0,1,1,1)`.

This is new: the paper's rigidity stops at the extremal line.  It also shows the
whole boundary pattern is width- and period-independent.

##### 7.2 The abstract search, and the localisation

`primitive_g4_abstract.py` / `primitive_g4_dfs.py` search the complete
chronological data: level profile, per-level arrival strings, single-tour
condition, and the requirement that the *actual* stabilised rank of every event
equal its assumed rank.  All of these are necessary, so an empty search is an
exclusion.

* **Positive controls.**  `W = 4`: 8 complete systems, none survives.  `W = 6`:
  96,616 complete systems, none survives.  Both agree with the proved width-four and
  width-six theorems.  Two independently written searches (a plain product
  enumeration and a DFS with `O(1)` fragment-based cycle pruning) agree on the count
  96,616 exactly.
* **Third positive control.**  `W = 8` with `f_t <= 5`: 9 admissible profiles,
  128,512 complete systems, none survives — consistent with the paper's
  computer-assisted width-eight theorem, reached here by a completely different
  route (chronological, not a column-block reachability enumeration).  Taken with
  `W = 4` and `W = 6`, these are consistency checks for the three
  computer-assisted width theorems within the tested primitive-diagonal
  growth-four profiles.
* **New.**  `W = 10` with every crossing number `f_t <= 3`: 4 admissible profiles,
  2,048 complete systems, **none survives**.  Width ten is not covered by any
  existing theorem, so this is a genuine new exclusion, but only for bounded
  crossing numbers.  Note `f_t` is never `0 (mod 4)` by C2, so the caps
  `f <= 3` and `f <= 4` define the same profile set.
* The thin profile `f = (1,3,2,...,2,1)` — the one that survives every counting
  constraint at every even width, with `N = 4W-2` — is excluded at `W = 6, 8, 10`.
  Exactly `2^(W-1)` of its systems are single tours; **every one of them has the
  correct drift `(1,-1)` and fails only the stabilised-order condition.**

**Retracted.**  An earlier draft of this section claimed the failure "is always at
level 2 or level 3", and inferred that the obstruction is local to the bottom rail
and width-independent.  That was an artefact: the diagnostic scanned levels in
increasing order and reported only the *first* failing level.  Re-running it to
report *every* failing level gives, at `W = 10` over the 512 single-tour systems,

```text
levels 2..10 all fail : 384 systems
levels 3..10 all fail : 128 systems   (level 2 correct in these)
```

and the same shape at `W = 6` and `W = 8`.  So the stabilised order is wrong at
essentially every level, not just near the rail, and the failure set grows with `W`.
What survives is weaker but still sharp: **level 3 and every level above it fail in
100% of single-tour thin systems**, level 2 in 75%.  There is therefore no evidence
here for a width-uniform *boundary* lemma; the obstruction is global.

##### 7.3 Exactly what is still missing

To turn this into `g >= 8` one needs an argument that is uniform in `W`.  §7.1 is a
genuine width-independent forcing, but it only pins one level, and §7.2 now shows
the thin family's obstruction is *not* concentrated there, so extending §7.1 inward
is not obviously the route.  The remaining freedom after §7.1 is `x_1 in {X, X+1}`
for the first local minimum on level 2 and `x_3 <= X` for the second, together with
the order-preserving linkage into level 3.  A hand analysis rules out the shortest
identification (the level-3 event feeding the rail's predecessor cannot be the one
fed by the rail's successor, since that would force `N = 4`), but does not close the
case.

The other unresolved item is an a priori bound on `f_t`.  The counting constraints
only give `|f_{t-1} - f_t| <= rho_t`, i.e. roughly a factor of three per level, so
the profile space is finite for each `W` but grows like `3^(W/2)`, which is what
stops the full-profile search at `W = 10`.  Any bound of the form `f_t <= c` would
make the whole primitive-diagonal case a finite computation per width.


#### 8. Hostile audit, 18 August 2026 — findings and disposition

The original statements needed the following corrections:

1. **FATAL as written.** (I1) claimed the class turn word is `R,L,R,L,...` on the
   bi-infinite periodic trace "without the zero-growth hypothesis". False: the
   counterexamples are `RLLLLRLRRR` and `RRLRLLLLRR`, genuine closed heading-reset
   traces of period 10 with drift `(1,-1)` whose singleton class at the top level
   turns `L`. Reproduced here independently, and the split was then confirmed on a far larger
   sweep run locally: of the **8,532** closed diagonal-drift heading-reset words of
   even length at most 14, **0** violate T1's turn-counting form and **8,096**
   violate its mod-four form. So the (I2)+(I3) half is unconditional and the (I1)
   half is not, with no ambiguity. *Repaired:* (I1) now
   states finite support explicitly and identifies it with condition (ii) of the
   realisability criterion; the counterexample is recorded in the note.
2. **NOT-A-DEFECT.** `m | (X - x_k)` is guaranteed — the class is one orbit of the
   translation group.
3. **NOT-A-DEFECT.** (I2) brute-forced over all four headings and both arrival
   parities: no failure.
4. **NOT-A-DEFECT.** The suspected sign error from the level shift is absent.
   `a - b = 2 (mod 4)` is shift-invariant, since flipping the shift swaps `a` and
   `b` and `-2 = 2 (mod 4)`. The checked cut identity is
   `net-x = sum_{even cuts} f - sum_{odd cuts} f = +m` on all six highways.
5. **SERIOUS.** C3's tie-break and all of C4 rest on "both extremal levels are at
   odd `t`", which the note used but never stated. *Repaired:* now cited as clauses
   (i) and (iii) of the paper's extremal-line rigidity, with the consequence of
   dropping it (`(1,3)` and `N = 2 (mod 8)`) stated.
6. **SERIOUS.** (I3) was stated with "over all time", which is vacuous for the
   `t`-walk — it is bounded and periodic, so every level is visited infinitely
   often. *Repaired:* (I3) is now split into a bounded case (per-period quotient
   walk, `F = 0`) and a drifting case (all-time counts, `F = +-1`).
7. **MINOR.** `F_y = -1`, not `+1`, for `d = (m,-m)`. *Repaired* (only `F mod 2` is
   used).
8. **MINOR.** T2's pairing of `u`-parity to level parity needs the shifted index;
   the raw `x+y` parity gets it backwards on the standard highway. *Repaired.*
9. **MINOR.** C2 forward-referenced C5. *Repaired* by making the dependence explicit.
10. **MINOR overclaim.** "T2 gives the 3-1 split a second way" is wrong: at `m = 1`
    the two `u`-line classes coincide with the two level-parity classes, so given T1
    the content of T2 is exactly "`N/2` is odd", already an input. *Repaired:* the
    claim is withdrawn.
11. **NOT-A-DEFECT.** All numerics pass: empty plane plus five random finite seeds,
    zero failures for T1, T1 mod-four, T2, the ceil/floor split, level-step
    consistency and cut balance; and on the raw traces, of the 1,692–5,081 cells
    first visited after highway onset, **none** begins with `L`.

Not reached by the auditor: T3/T4, the level-DP feasibility claim, the rank-parity
identity of section 5, and the paper's Proposition hv, which was taken as given.
Those remain to be audited.


#### 9. A sign trap in the stabilised key (recorded 18 August 2026)

The stabilised order within a translation class is by the key `phase - N*ell`,
where `ell` indexes the translate: `x = x_0 + a*ell` with `a` the drift's
*x*-component. For `a = +1` this is `phase - N*x`; for `a = -1` it is
`phase + N*x`. Using `phase - N*x` regardless of the sign of `a` is wrong, and it
fails *silently* — it does not error, it just accepts words it should reject.

Cost of getting this wrong, measured: sweeping every closed diagonal-drift
heading-reset word of even length at most 16 (24,472 words),

```text
naive key  phase - N*x  for every drift :  3 words pass P3   (all with drift (-1,1))
correct key, sign taken from the drift  :  0 words pass P3
```

All three false positives have drift `(-1,1)`, growth four, transverse width four,
and level multiplicities `1,3,5,4,1` — i.e. they look exactly like a
counterexample to the paper's width-four theorem, and are not one. Anyone
re-implementing the criterion should reproduce the `0` above as a regression test.

The searches in this note normalise to `d=(1,-1)` before applying the key, so they
are unaffected; `code/python/primitive_g4_smt.py` likewise fixes `a=+1`. The trap is
recorded because the paper states the criterion for general drift.

#### 10. Second hostile audit, 18 August 2026 (scope: T3/T4 and section 7.1)

The tests below confirm T3/T4 numerically at `m = 2`. In the derivation, the
`+1` is the net flow across a *column* cut, which is 1 and not `m`.
The corrections are:

1. **NOT-A-DEFECT.** The heading claim ("consecutive horizontal headings agree iff
   the two turns differ") verified exhaustively over all 16 heading/turn-pair cases.
2. **MINOR.** The alternation lemma making "the two turns between them" a
   well-defined pair was left implicit. *Repaired.*
3. **PASSES.** T3/T4 numerically on the period-104 highway after rotation to drift
   `(2,-2)`: columns `nu = 26,26` against reversal counts `11,15`; rows `26,26`
   against `17,13`. All four `= nu+1 (mod 2)`. The opposite criterion gives the
   wrong parity, so the test discriminates.
4. **MINOR.** The counting domain was never stated, and the identity is false
   outside it — over a whole trajectory it holds exactly where the net flow across
   the cut is odd and fails by one parity on the transient columns behind the start
   (all 22 of them, against 561 columns where it holds). *Repaired* by stating the
   per-residue-class-mod-`m`, per-period domain.
5. **SERIOUS.** "For `m = 1` T3/T4 follow from T1+T2; for `m >= 2` they are
   separate" was asserted in the same voice as the theorems, with no derivation of
   the first half and no separating witness for the second. Passing on 26 genuine
   highways is consistency, not independence. *Repaired:* demoted to an explicitly
   unverified remark.
6. **MINOR.** Section 7.1's step `ceil(m_2/2) <= 2 => m_2 in {3,4}` is not valid on
   its stated premise ("at most one"). *Repaired* using the pass-count form.
7. **SERIOUS.** Section 7.1's "the unique downward departure sits at the other even
   rank" was load-bearing and uncited; the auditor suspected it needed the
   unaudited rank-parity identity of section 5. It does not: `A_0 = 1` forces
   `A_1 = 0`, and the reflect/continue rule then leaves only even ranks with
   `a_r = 0` as downward departures. *Repaired* by giving that one-line argument
   explicitly.
8. **NOT-A-DEFECT.** The ordering direction in 7.1 is right, and ties are
   impossible: the two keys differ by `-(N+2)`.
9. **MINOR.** "outranks" is ambiguous, and the top-rail statement is true but is
   *not* a verbatim mirror — there the predecessor sits at the smaller `x` and takes
   the larger rank. *Repaired.*

Still not reached by either audit: the rank-parity identity of section 5, the
level-DP feasibility claim, and any test of T3/T4 at `m >= 3`.

#### 11. Bounded-crossing primitive diagonal: a candidate width-uniform obstruction

Restrict to primitive-diagonal growth four with every crossing number `f_c <= 3`.
This is a real restriction (fat profiles exist and produce complete tours), but it
makes the counting layer rigid: `f_c` is never `0 (mod 4)`, so `f_c in {1,2,3}`, and
every non-wake level has `m_c = f_{c-1}+f_c = 4` exactly, forcing `f_c = 4-f_{c-1}`
between wake levels. The profile is then a walk on a three-letter alphabet, i.e. a
finite automaton in the level index, and the number of admissible profiles is tiny:
2 at `W=6`, 3 at `W=8`, 4 at `W=10`.

##### 11.1 Where the tours die, by level

Over *all* `f<=3` profiles, the fraction of complete single tours whose stabilised
order is wrong at each level:

```text
level      2     3     4     5     6     7     8     9    10
W= 6      75%   87%  100%  100%  100%
W= 8      75%   83%  100%  100%  100%  100%  100%
W=10      75%   81%  100%  100%  100%  100%  100%  100%  100%
```

Level 2 fails in exactly three quarters of tours at every width, level 3 in about
four fifths, and **every level from 4 upward fails in 100% of tours at every width
tested**. A 100% rate that does not move with `W` is what a width-uniform local
obstruction looks like, and level 4 is the first level where it is total.

##### 11.2 What the level-4 failure looks like, and what is *not* yet established

Recording, for each complete tour, the triple (multiplicity at level 4, the assumed
ranks in true stabilised order, the relative `x` coordinates):

```text
W= 6   2 profiles     64 tours    6 distinct patterns
W= 8   3 profiles    384 tours   10 distinct patterns
W=10   4 profiles   2048 tours   10 distinct patterns
```

`W=8` and `W=10` give **exactly the same ten patterns**, set-equal, despite `W=10`
having an extra profile and five times the tours. That is the encouraging part.

Two things must be said against it. First, `W=6` is **not** a subset of `W=8`: the
union over the three widths has twelve patterns, so the family is not monotone and
the agreement of `W=8` with `W=10` is not yet stabilisation. Second, an earlier
reading of this data --- that the event of assumed rank zero never holds the maximum
`x` at level 4 --- is **false**: it holds on the `W=8` and `W=10` patterns but fails
on one of the `W=6` patterns, so it was a description fitted to two widths rather
than a property. Both statements were withdrawn as soon as `W=6` was added.

`W=12` is running and is what decides between the two readings: if its pattern set
again equals the `W=8` set, the family has stabilised from `W=8` and `W=6` is a
small-width boundary effect; if not, there is no local obstruction here and this
route should be dropped.

##### 11.3 Why this would be worth having

A proof that the level-4 configuration is confined to a finite, width-independent
case list, together with the observed fact that every case fails the stabilised
order, would give: **no primitive-diagonal growth-four highway has all crossing
numbers at most three, at any transverse width.** That is conditional on `f<=3` and
so does not give `g >= 8`, but it would be the first statement in this direction
that is uniform in `W` rather than proved width by width, which is the barrier every
other approach here has run into.

#### 12. The transfer-matrix route is dead (18 August 2026)

Section 11 and the handoff proposed a transverse transfer matrix, and identified its
load-bearing step: that the relative `x`-offsets of the strands crossing a cut stay
inside a bounded window. **That step is false, and the route should not be
pursued.**

For `f<=3` the admissible profiles are completely regular. There are exactly
`W/2 - 1` of them at width `W`, every one has period `N = 4W-2`, and every one has
the shape

```text
1,3,(1,3)^j,  2,2,...,2,  (3,1)^k, 3,1
```

--- a run of alternating `1,3` at the bottom, a run of `2`s in the middle, and a run
of alternating `3,1` at the top, parameterised by where the two interior wake levels
sit. The two extremes of that family are the all-`2`s profile (one wake level next
to each rail) and the maximally alternating profile (the two interior wake levels
adjacent in the middle).

Measuring the maximum `x`-spread of the up-crossings over every complete single
tour, on the **maximally alternating** profile:

```text
W= 8   f=(1,3,1,3,2,1,3,1)                    128 tours   max spread 2
W=10   f=(1,3,1,3,1,2,3,1,3,1)                512 tours   max spread 3
W=12   f=(1,3,1,3,1,3,2,1,3,1,3,1)          2,048 tours   max spread 4
W=14   f=(1,3,1,3,1,3,1,2,3,1,3,1,3,1)      8,192 tours   max spread 5
```

The spread is exactly `W/2 - 2`. It grows linearly and without bound, so the state
of any left-to-right sweep carrying the offsets is unbounded, and there is no finite
automaton over the level index. The route is closed.

**Why the earlier measurement misled.** Sections 7 and 11 measured the spread on the
thin profile `f=(1,3,2,...,2,1)` and found it constant at 2 across `W = 6` to `18`,
over 131,072 tours at the top end. That looked like strong evidence. It was not:
the thin profile is precisely the all-`2`s member, the *least* alternating of the
family, and it is the one member whose spread does not grow. Generalising from it
was the error. The lesson for anything similar: when a family is parameterised,
measure at the extreme of the parameter, not at the most convenient member.

This is consistent with the mechanism guessed earlier. The `x`-displacement across
an excursion is an alternating sum over cuts of alternating parity, so it telescopes
when the crossing numbers are constant --- which is exactly the all-`2`s case --- and
does not telescope when they alternate `3,1,3,1`, which is exactly the case that
grows.

**Status of Section 11.** Its empirical content stands: every level from four upward
fails the stabilised order in 100% of `f<=3` tours at `W = 6,8,10`, and the level-4
pattern sets at `W=8` and `W=10` are set-equal. But the mechanism proposed for
turning that into a width-uniform theorem is now excluded, so Section 11 is a
recorded observation with no route attached, not a programme.

#### 13. Longitudinal mod-four refinement (20 August 2026)

T2 has a finite-support refinement on each exact longitudinal line. On a far-ahead
line `u=v`, let `nu_v` be the total number of visits and let `Omega_v` be the number
of physical cells on the line visited an odd number of times. Equivalently,
`Omega_v` is the number of odd wake strands in the residue `u=v (mod 2m)`. Every
complete cell word starts with `R` and alternates, so

```text
#R_v = (nu_v+Omega_v)/2,       #L_v = (nu_v-Omega_v)/2.
```

T2 therefore gives the proved congruences

```text
horizontal u-line:  nu_v = 2-Omega_v (mod 4),
vertical   u-line:  nu_v = 2+Omega_v (mod 4).
```

Finite support is essential for this mod-four form. The period-ten trace
`RLLLLRLRRR` with initial heading north and drift `(1,-1)` has on the vertical line
`u=0` five visits in two cell words, `RLRL` and the singleton `L`. Thus T2 itself
holds (`#L=3` is odd), while `nu=5`, `Omega=1` violates the displayed finite-support
congruence.

For primitive drift `m=1`, the two exact-line visit counts are both `N/2` and
`Omega_H=alpha`, `Omega_V=beta`. The refinement is then exactly the congruence
already obtained by summing T1; at growth four it is equivalent to
`N=6 (mod 8)`. It supplies no new primitive obstruction. For `m>=2` it is a
genuinely finer grouping, by `u=2r-t (mod 2m)`, than either a transverse level or an
`x mod m` residue.

On the archived standard word (`N=104`, `m=2`), the four `u mod 4` residues have
`(nu,Omega)=(27,1),(20,6),(25,3),(32,2)` and satisfy the four congruences exactly.

It is useful pruning, but not an exclusion. A corrected explicit `m=4`, `g=8`,
`W=10`, `N=64` counting/flow skeleton satisfies T1, both P22 residue families, both
new u-line laws, singleton horizontal extrema, phase balance, and all local
reflect-flow inequalities. Its level totals are
`(1,4,7,8,8,8,8,8,7,4,1)` and its cut counts are
`(1,3,4,4,4,4,4,4,3,1)`. The eight odd classes are

```text
(t,r,m) = (1,3,1), (3,2,7), (5,0,5), (5,1,3),
          (7,0,5), (7,3,3), (9,2,7), (11,1,1).
```

For reproducibility, the complete nonzero table (including the even filler
classes) is

```text
t= 1: r3=1                 t= 2: r1=2, r2=2
t= 3: r2=7                 t= 4: r0=8
t= 5: r0=5, r1=3           t= 6: r0=8
t= 7: r0=5, r3=3           t= 8: r0=8
t= 9: r2=7                 t=10: r0=2, r3=2
t=11: r1=1
```

Each `x mod 4` and each `y mod 4` residue contains two same-checker odd classes,
so both P22 sums are `-2=2 (mod 4)`. This is only an abstract skeleton, not a linked
tour or highway; it proves that the enlarged arithmetic system still does not prove
`g>=12`.

One limited numerical consequence is

```text
N >= g + 2m + 2 E_H,
```

where `E_H` counts horizontal `u mod 2m` residues with even `Omega_v`. This is only
a period lower bound; no upper bound on `N` is known.
