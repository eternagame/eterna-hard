# Eterna Hard
Come solve the hardest puzzles on Eterna!

This repository contains a list of Eterna player puzzles (2013-2025) that at most one player besides the author had solved as of Aug 2026. 

- These have been further filtered to be single-state puzzles, length <=400 nt, and using the Vienna 1 or 2 folding engine. 
- Includes the in-game constraints (locked bases, pair-type limits).
- Released 100 at a time, as each group opens on eternagame.org.
- Every released puzzle is solvable: each has a player solution that passes the validator.

## Files
- `groups/eterna-hard-group{N}.csv`: one row per puzzle, columns below.

## Validation
Once you have solutions, you (or your agent) can go directly to the puzzles at the puzzle links and paste in the solutions. 

To check designs offline first, use [eterna-validator](https://github.com/eternagame/eterna-validator), which scores a design exactly as the game does and has ViennaRNA install instructions:

```sh
RNAFOLD_V1=/path/to/ViennaRNA-1.8.5/Progs/RNAfold \
  python3 check_design.py groups/eterna-hard-group1.csv designs.tsv
```

`designs.tsv` should be tab-separated with columns `puzzle_id` and `sequence`. 

The CSVs already have the columns needed by the validator script.

Links to each group are available at:

- [Eterna Hard Group 1](https://eternagame.org/labs/16022932)
- [Eterna Hard Group 2](https://eternagame.org/labs/16529751)

with more to come.

## Easier tests
These Eterna Hard puzzles are, by definition, hard! If you're testing computational approaches, you may want to start with the standard benchmark for RNA secondary structure design, Eterna100. Both original and modernized versions are available in the [Eterna100 repo](https://github.com/eternagame/eterna100-benchmarking), along with guidance for offline validation.

## Columns
- `group` - release group (1-5)
- `puzzle_id` - Eterna ID: eternagame.org/puzzles/<id>
- `title` - puzzle title
- `description` - author's description (may hold HTML)
- `author_uid` - Eterna user ID of the puzzle author
- `author_name` - Eterna username of the puzzle author
- `solvers` - non-author solvers as of Aug 2026
- `folder` - Vienna = ViennaRNA 1.8.5, Vienna2 = 2.1.8
- `created_time` - when the puzzle was published
- `structure` - target structure, dot-bracket
- `constraints` - raw Eterna constraint string
- `max_gc` - most GC pairs allowed
- `min_au` - fewest AU pairs allowed
- `min_gu` - fewest GU pairs allowed
- `locks` - `x` = locked base (see `begin_sequence`), `o` = designable
- `begin_sequence` - starting sequence
- `objective` - raw Eterna objective JSON (redundant with above information)
