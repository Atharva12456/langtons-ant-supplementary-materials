# Bounded period searches

These notes retain their original dates and hypotheses. Later status
pointers distinguish superseded checkpoints from the current report.
Individual source files and linked records are preserved in
[research_notes_sources.zip](research_notes_sources.zip).

## Contents

- [growth8_period50_exclusion_2026-08-22](#source-research-notes-growth8-period50-exclusion-2026-08-22-md)
- [growth8_period52_exclusion_2026-08-22](#source-research-notes-growth8-period52-exclusion-2026-08-22-md)
- [growth8_period54_exclusion_2026-08-23](#source-research-notes-growth8-period54-exclusion-2026-08-23-md)
- [growth8_period56_exclusion_2026-08-23](#source-research-notes-growth8-period56-exclusion-2026-08-23-md)
- [growth8_period58_exclusion_2026-08-23](#source-research-notes-growth8-period58-exclusion-2026-08-23-md)
- [growth8_period60_exclusion_2026-08-25](#source-research-notes-growth8-period60-exclusion-2026-08-25-md)

<a id="source-research-notes-growth8-period50-exclusion-2026-08-22-md"></a>

## growth8_period50_exclusion_2026-08-22

Source: `research-notes/growth8_period50_exclusion_2026-08-22.md`.

### Growth eight does not occur at period 50

The existing residue-free search excludes every finite-support periodic highway
through period 48.  The next possible period for some growth-eight residue types
is 50.  This note records a complete targeted search of that single period.

#### Statement

There is no finite-support periodic highway with ant period `N=50` and growth
`g=8`.

This is a finite computer-assisted exclusion, and it does not close any
growth-eight drift family by itself.  Period 52 was subsequently excluded by a
separate run recorded in `growth8_period52_exclusion_2026-08-22.md`.

#### Search

`PositiveGrowthResidueSearch.java` was run with
`--period 50 --target-growth 8 --prefix-length 12 --deficit-depths 0`.  The
normalization rotates a positive-growth cyclic word to a global minimum of its
turn balance.  The normalized word begins with `R`, so the remaining eleven
prefix symbols give exactly `2^11=2048` prefix ranks.

The ranks were divided into eight disjoint half-open intervals of length 256.
No shard used a node cap or the optional deficit rule.  At a leaf the program
first checks the signed mod-four wake-residue identity and then applies the exact
periodic-realisability criterion to every survivor.  Thus the computation uses
the proved residue theorem as a pruning lemma; it is not the residue-free search
used for the period-at-most-48 result.

The aggregate counts are

```text
prefix ranks                  2,048
search nodes         15,488,130,188
endpoint prunes       2,593,511,002
growth prunes         2,994,063,495
residue checks          327,932,571
residue prunes          313,638,967
P3 checks                14,293,604
accepted words                    0
```

Here an accepted word is a normalized turn word that passes the exact P3 test,
not merely a trace satisfying the arithmetic filters.

#### Audit record

`code/python/aggregate_target_growth_shards.py` reconstructs the expected prefix
and independently recomputes its normalization/alternation validity for every
rank, checks that the rank intervals cover `0,...,2047` exactly
once, rejects a shard with a node cap or active deficit rule, compares every
top-level count with the sum of its per-rank counts, and compares the per-rank
and per-shard hit lists.  It also hashes the eight raw shard files.

The checked aggregate is
`results/growth8_period50_exclusion.json`.  It reports
`ranks_covered_exactly_once=true`, `all_checks_passed=true`, and an empty hit
list.  Its SHA-256 digest is

```text
e0b9e7637061ebfa317c4abb019e5ad3da654716b652709803aa901d791f789c
```

The search engine digest at the time of the run and the digest of the current
aggregate audit are

```text
PositiveGrowthResidueSearch.java
315c18bd3f7749750fc8c618d5b3f464756d2ddd64bda5dd9be4cbb1f33e9c23

aggregate_target_growth_shards.py
c4db9da60a9b19e634a51d552420528e1cf43868d4754bf3d633cf951f920925
```

The fixed-growth branch was also compared with the original all-growth traversal
on every even period from 4 through 18.  At each period, the sum of the separate
fixed-growth leaf, residue, and P3 counts equals the original count, and the hit
lists partition exactly.  The audit and its output are

```text
code/python/audit_target_growth_mode.py
76c62d8a893045064b5fdbc3d61c525c11a969758b383e8c634e529705b1d4ad

results/target_growth_mode_cross_check.json
1fe944da4d7903084d3b9ccffc26921c97367799cef168520ec794fcfa42fe54
```

This cross-check tests the new restriction against the prior search mode.  It
does not independently prove the residue theorem or the P3 criterion.

The raw shards are reproducible from the following command pattern, with the
eight consecutive intervals `[0,256)`, `[256,512)`, ..., `[1792,2048)`:

```text
java -cp build/residue PositiveGrowthResidueSearch \
  --period 50 --prefix-length 12 \
  --rank-start START --rank-stop STOP \
  --deficit-depths 0 --target-growth 8 \
  --output shard.json

python code/python/aggregate_target_growth_shards.py SHARD_DIRECTORY \
  --output results/growth8_period50_exclusion.json
```

Together with the residue-free period-at-most-48 computation, this run moved the
shortest possible growth-eight period to 52.  The later period-52 computation
moved it again to 54.  The all-period problem is unchanged.

<a id="source-research-notes-growth8-period52-exclusion-2026-08-22-md"></a>

## growth8_period52_exclusion_2026-08-22

Source: `research-notes/growth8_period52_exclusion_2026-08-22.md`.

### Growth eight does not occur at period 52

The fixed-growth search used at period 50 has now been run at period 52.  This
note records the completed run and its audit.  It is a finite exclusion of one
period, not an argument about every period in any drift family.

#### Result

There is no finite-support periodic highway with ant period `N=52` and growth
`g=8`.

The command-line settings were

```text
--period 52 --target-growth 8 --prefix-length 12 --deficit-depths 0
```

The first turn of a normalized positive-growth word is fixed, leaving 2,048
length-12 prefix ranks.  Eight half-open rank intervals of length 256 cover that
set exactly once.  No node cap was imposed, and the optional deficit rule was
disabled.  The combined counts are

```text
prefix ranks                  2,048
search nodes         38,465,607,042
endpoint prunes       6,051,510,823
growth prunes         7,227,635,776
residue checks        1,441,579,326
residue prunes        1,346,376,021
P3 checks                95,203,305
accepted words                    0
```

The residue test is used only as a proved pruning lemma.  Every leaf that passes
it is sent to the exact periodic-realisability test.

#### Audit trail

The raw records are in `records/g8_p52_shards`.  The aggregate checker rebuilds
each prefix from its rank, checks the normalization directly, verifies exact rank
coverage and every per-rank counter sum, rejects capped or deficit-pruned runs,
compares both copies of the hit lists, and records a SHA-256 digest for every
shard.  Its output is

```text
results/growth8_period52_exclusion.json
bb8948dec0448e583d80785a800504747316ec1a65feb46c9696d7728888f54e
```

The relevant source digests are

```text
code/java/PositiveGrowthResidueSearch.java
315c18bd3f7749750fc8c618d5b3f464756d2ddd64bda5dd9be4cbb1f33e9c23

code/python/aggregate_target_growth_shards.py
c4db9da60a9b19e634a51d552420528e1cf43868d4754bf3d633cf951f920925
```

The aggregate can be rebuilt with

```text
python code/python/aggregate_target_growth_shards.py records/g8_p52_shards \
  --output results/growth8_period52_exclusion.json
```

The separate mode audit through period 18 remains the regression check for the
fixed-growth branch; it confirms that the target-growth runs partition the
original all-growth leaf, residue, P3, and hit records exactly.

Together with the general exclusion through period 48 and the targeted period-50
run, this made period 54 the first possibility left by those computations. Later
runs extend the exclusion through period 60; see
[growth8_period60_exclusion_2026-08-25.md](07_Period_searches.md#source-research-notes-growth8-period60-exclusion-2026-08-25-md).

<a id="source-research-notes-growth8-period54-exclusion-2026-08-23-md"></a>

## growth8_period54_exclusion_2026-08-23

Source: `research-notes/growth8_period54_exclusion_2026-08-23.md`.

### Growth eight does not occur at period 54

The fixed-growth search has now been completed at period 54.  This is the third
targeted run after the general residue-free exclusion through period 48.

#### Result

There is no finite-support periodic highway with ant period `N=54` and growth
`g=8`.

The search used

```text
--period 54 --target-growth 8 --prefix-length 12 --deficit-depths 0
```

A normalized positive-growth word starts with `R`, so there are 2,048 possible
length-12 prefixes.  Sixty-four half-open intervals of 32 ranks cover them
exactly once.  Every shard completed without a node cap, and the optional
deficit rule was disabled.  The aggregate counts are

```text
prefix ranks                   2,048
search nodes          99,180,610,230
endpoint prunes       16,912,730,914
growth prunes         18,882,824,613
residue checks         2,123,298,784
residue prunes         2,018,813,540
P3 checks                104,485,244
accepted words                     0
```

The residue test is a proved pruning lemma.  Every leaf that passes it is sent
to the exact periodic-realisability test.

#### Audit trail

The raw records are archived in `records/g8_p54_shards`.  The aggregate checker
reconstructs every prefix from its rank, checks the normalization directly,
verifies exact rank coverage and every per-rank counter sum, rejects capped or
deficit-pruned shards, compares the two copies of the hit lists, and records a
SHA-256 digest for each shard.  Rebuilding the aggregate from the archive gives

```text
results/growth8_period54_exclusion.json
e906fbf3f7cd06d3a4a21977e679514ad611b052edce475744f1776fd2279fb8
```

The relevant source digests are

```text
code/java/PositiveGrowthResidueSearch.java
315c18bd3f7749750fc8c618d5b3f464756d2ddd64bda5dd9be4cbb1f33e9c23

code/python/aggregate_target_growth_shards.py
c4db9da60a9b19e634a51d552420528e1cf43868d4754bf3d633cf951f920925
```

The fixed-growth branch was previously compared with the original all-growth
mode at every even period through 18.  Those runs partition the original leaf,
residue, P3, and hit records exactly.  That regression checks the new search
restriction; it does not replace the proof of the residue theorem or the P3
criterion.

The aggregate can be rebuilt with

```text
python code/python/aggregate_target_growth_shards.py records/g8_p54_shards \
  --output results/growth8_period54_exclusion.json
```

Together with the general period-at-most-48 result and the targeted period-50
and period-52 runs, this excludes growth eight through period 54. Period 56 was
the first possibility left by those runs; later computations extend the exclusion
through period 60. The result is finite: all ten drift orbits retain open cases.
See [the period-60 record](07_Period_searches.md#source-research-notes-growth8-period60-exclusion-2026-08-25-md).

<a id="source-research-notes-growth8-period56-exclusion-2026-08-23-md"></a>

## growth8_period56_exclusion_2026-08-23

Source: `research-notes/growth8_period56_exclusion_2026-08-23.md`.

### Growth eight does not occur at period 56

The fixed-growth search has now been completed at period 56. This is the fourth
targeted run after the general residue-free exclusion through period 48.

#### Result

There is no finite-support periodic highway with ant period `N=56` and growth
`g=8`.

The search used

```text
--period 56 --target-growth 8 --prefix-length 12 --deficit-depths 0
```

A normalized positive-growth word starts with `R`, so there are 2,048 possible
length-12 prefixes. Two hundred fifty-six half-open intervals of eight ranks
cover them exactly once. Every shard completed without a node cap, and the
optional deficit rule was disabled. The aggregate counts are

```text
prefix ranks                    2,048
search nodes          246,883,217,080
endpoint prunes        39,482,207,076
growth prunes          45,748,124,938
residue checks          9,343,985,497
residue prunes          9,333,168,099
P3 checks                  10,817,398
accepted words                      0
```

The residue test is a proved pruning lemma. Every leaf that passes it is sent
to the exact periodic-realisability test.

#### Audit trail

The raw records are archived in `records/g8_p56_shards`. The aggregate checker
reconstructs every prefix from its rank, checks the normalization directly,
verifies exact rank coverage and every per-rank counter sum, rejects capped or
deficit-pruned shards, compares the two copies of the hit lists, and records a
SHA-256 digest for each shard. Rebuilding the aggregate from the archive gives

```text
results/growth8_period56_exclusion.json
4b7b2ec752ce9fd24a9e0dcceb604a1ab44209f848f6fe28f51b580b9ffa8afa
```

The relevant source digests are

```text
code/java/PositiveGrowthResidueSearch.java
315c18bd3f7749750fc8c618d5b3f464756d2ddd64bda5dd9be4cbb1f33e9c23

code/python/run_target_growth_shards.py
6c0e1db9b6ca7d6a34a9528cdf2905d9ddfd98bd995765bddef675ca894b1cc7

code/python/aggregate_target_growth_shards.py
c4db9da60a9b19e634a51d552420528e1cf43868d4754bf3d633cf951f920925
```

The fixed-growth branch was previously compared with the original all-growth
mode at every even period through 18. Those runs partition the original leaf,
residue, P3, and hit records exactly. That regression checks the new search
restriction; it does not replace the proof of the residue theorem or the P3
criterion.

The run and aggregate can be reproduced with

```text
python code/python/run_target_growth_shards.py --period 56 --target-growth 8 \
  --prefix-length 12 --chunk-size 8 --workers 4 \
  --output-dir tmp/g8_p56_shards_v1 \
  --summary results/growth8_period56_exclusion.json

python code/python/aggregate_target_growth_shards.py records/g8_p56_shards \
  --output results/growth8_period56_exclusion.json
```

Together with the general period-at-most-48 result and the targeted period-50,
period-52, and period-54 runs, this excludes growth eight through period 56.
Period 58 was the first possibility left by those runs; later computations
extend the exclusion through period 60. The result is finite: all ten drift
orbits retain open cases. See
[the period-60 record](07_Period_searches.md#source-research-notes-growth8-period60-exclusion-2026-08-25-md).

<a id="source-research-notes-growth8-period58-exclusion-2026-08-23-md"></a>

## growth8_period58_exclusion_2026-08-23

Source: `research-notes/growth8_period58_exclusion_2026-08-23.md`.

### Growth eight does not occur at period 58

#### Result

There is no finite-support periodic highway with ant period `N=58` and growth
`g=8`.

The fixed-growth search used a normalized length-12 prefix. Its 2,048 ranks
were divided into 256 half-open intervals of eight ranks. Every interval was
searched to completion, no node cap was present, and the optional deficit rule
was disabled. The aggregate counters are

```text
prefix ranks                    2,048
search nodes          638,341,904,284
endpoint prunes       110,337,123,373
growth prunes         120,193,469,311
residue checks         13,798,101,325
residue prunes         13,060,756,064
P3 checks                 737,345,261
accepted words                      0
aggregate core time       74,789.300 s
```

The residue filter is a proved necessary condition. Every leaf that passes it
is checked by the exact stabilized translation-class criterion P3.

#### Certificate audit

The 256 raw shards and their manifest are archived in
`records/g8_p58_shards`. The aggregate auditor reconstructed each prefix from
its rank, checked every interval and per-rank counter sum, required uncapped
completion, compared the two copies of every hit list, and recorded a SHA-256
digest for every shard. Re-aggregating the archive reproduced the result file
byte for byte:

```text
results/growth8_period58_exclusion.json
c823cf229a5204e9d8ff34ea4dd8b65738aaf023cd5d712199101fba77c17e1f
```

The source digests used by the archived audit are

```text
code/java/PositiveGrowthResidueSearch.java
315c18bd3f7749750fc8c618d5b3f464756d2ddd64bda5dd9be4cbb1f33e9c23

code/python/run_target_growth_shards.py
6c0e1db9b6ca7d6a34a9528cdf2905d9ddfd98bd995765bddef675ca894b1cc7

code/python/aggregate_target_growth_shards.py
c4db9da60a9b19e634a51d552420528e1cf43868d4754bf3d633cf951f920925
```

The archive can be re-audited with

```text
python code/python/aggregate_target_growth_shards.py records/g8_p58_shards \
  --output results/growth8_period58_exclusion.json
```

Together with the exclusions through period 56, this removes growth eight
through period 58. It is a finite-period result; all ten drift orbits retain
open cases. The subsequent [period-60 record](07_Period_searches.md#source-research-notes-growth8-period60-exclusion-2026-08-25-md)
extends the finite exclusion through period 60.

<a id="source-research-notes-growth8-period60-exclusion-2026-08-25-md"></a>

## growth8_period60_exclusion_2026-08-25

Source: `research-notes/growth8_period60_exclusion_2026-08-25.md`.

### Growth eight does not occur at period 60

#### Result

There is no finite-support periodic highway with ant period `N=60` and growth
`g=8`.

The search covered all 2,048 normalized length-12 prefix ranks exactly once.
It combined four disjoint sets of completed shards:

```text
original engine       57 eight-rank shards      456 ranks
endpoint reuse 0     116 one-rank shards        116 ranks
endpoint reuse 1     109 one-rank shards        109 ranks
endpoint engine    1,367 one-rank shards      1,367 ranks
total              1,649 shards               2,048 ranks
```

No shard used a node cap. The aggregate counters are

```text
search nodes              594,889,763,705
endpoint prunes           107,827,678,241
growth prunes              96,145,468,458
deficit checks              4,203,887,773
deficit prunes              4,203,344,162
deficit endpoints tested   12,834,070,625
residue checks             18,848,141,274
residue prunes             16,975,250,784
P3 checks                   1,872,890,490
accepted words                          0
aggregate core time           345,889.321 s
```

The endpoint engine uses the eight period-60 endpoints allowed by heading
reset, growth eight, P16, and parity. Its suffix table records exact simultaneous
reachability in heading, displacement, and growth. An independent brute-force
enumeration checked that table for every suffix of length at most ten. The
endpoint-specific deficit test retains a prefix whenever at least one exact
suffix can reach an allowed endpoint without violating cyclic-minimum
normalization. Leaves passing the residue condition are sent to the same exact
P3 test used by the original engine.

#### Certificate audit

The raw archive is `records/g8_p60_hybrid_shards`. Its four subdirectories
contain 1,649 shard files and four manifests. The hybrid auditor checked the
engine-specific deficit settings and endpoint declaration, reconstructed every
prefix, verified exact rank coverage and all per-rank counter sums, rejected
incomplete or capped shards, and compared every hit list. A second audit from
the archive matched every shard digest stored in the certificate.

```text
results/growth8_period60_exclusion.json
bbf3c624f679d654c6994e80d0fe46c34f7a142bd99b7779c54c401e30aa606c
```

The principal source digests are

```text
code/java/PositiveGrowthResidueSearch.java
315c18bd3f7749750fc8c618d5b3f464756d2ddd64bda5dd9be4cbb1f33e9c23

tmp/PositiveGrowthP60EndpointSearch.java
ea006745d901c8a67a0156d4d28021a379456f18323b0b08455519bfcc717444

tmp/run_p60_endpoint_hybrid.py
a218c294e8e954a014f0c3c27941f51f946e285328ca6a4812dd8284982a7cae

tmp/audit_hybrid_target_growth_shards.py
08e794e6d9547e0cbfcaecb1cbe302de58cc7486c9669f53cc485d84bad027b7
```

This completes the finite exclusion through period 60. Period 62 is the first
period not covered by the exact word searches. The all-period classification is
unchanged: all ten drift orbits remain open. At `(4,-4)`, only the full-rail and
mixed-checker subfamilies are excluded analytically; the pure partial-rail branch
remains.
