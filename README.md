# Recommender — Computer Labs III (LI3)

Academic project implemented in C for the Computer Labs III course (2nd year, Software Engineering degree, University of Minho).

The goal is to manage and query records related to music: users, tracks, albums, artists and interaction history — using modular C code with GLib support and a textual interface (ncurses) for interactive mode.

This project obtained a final grade of 17/20 💎

## Summary
The project implements an in-memory "database" engine to store domain entities (User, Track, Album, Artist, History) and answer queries (batch or interactive). The code is organized into modules: parsers, entities, managers, queries and an interactive interface.

Main features
- Robust parsing of dataset files to populate internal structures.
- Data structures and indices (using GLib and custom collections) for efficient access.
- Batch mode: executes a file containing commands/queries.
- Interactive mode: textual UI for running queries and exploring results.
- Makefile and Dockerfile for reproducible builds and environment.

## Requirements
- OS: Linux (tested on Ubuntu 22.04)
- Tools: `gcc`, `make`
- Libraries: `libglib2.0-dev`, `libncurses-dev`
- (Optional) `valgrind` for memory debugging

Install dependencies on Debian/Ubuntu:

```bash
sudo apt update
sudo apt install build-essential libglib2.0-dev libncurses-dev valgrind -y
```

## Build
Run all commands from the project root directory.

To build the project:

```bash
make
```

The Makefile should produce the main executable, typically `recomendador-linux-x86_64.o`. If your build produces a different binary name, replace it in the examples below.

## Run

Interactive mode (text UI):

```bash
./recomendador-linux-x86_64.o
```

Batch mode (dataset + commands file):

```bash
./recomendador-linux-x86_64.o <path-to-dataset> <commands-file>
```

Tests (if provided in Makefile):

```bash
make tests
```

## Running with Docker
A `Dockerfile` is included to create a build environment. Example steps:

```bash
# build image
docker build -t li3-recommender .

# run container mounting the project directory
docker run --rm -it -v $(pwd):/workspace li3-recommender bash
# inside container:
cd /workspace
make
./recomendador-linux-x86_64.o
```

The Dockerfile installs the required build dependencies (`gcc`, `make`, `libglib2.0-dev`, `libncurses-dev`, `valgrind`).

## Repository layout (short)
- `src/` — source code (modules, entities, parsers, managers, queries)
- `include/` — public headers (module interfaces)
- `interativo/` — interactive UI files (ncurses)
- `parsers/` — dataset parsing code
- `gestores/` — modules that manage collections of entities
- `entities/` — domain structures (Album, Track, User, Artist, History)
- `tests/` — tests (if any)
- `Makefile` — build rules
- `Dockerfile` — build environment
- `relatorio-fase1.pdf`, `relatorio-fase2.pdf` — project reports
- `recomendador-linux-x86_64.o` — (possible) compiled executable included in repo

## File formats and supported queries
Add concrete examples of dataset formats and the syntax of supported queries here. If you want, I can:
- automatically extract the supported queries from `src/Queries.c` and `interativo/queries.c` and add a "Supported queries" section;
- create an `examples/` folder with a small sample dataset and a `queries.txt` file for testing batch mode.

## Development notes and best practices
- Keep public interfaces in headers (`include/`) and implementations in `src/`.
- Validate all input while parsing (empty fields, special characters).
- Use `valgrind --leak-check=full ./recomendador-linux-x86_64.o ...` during development.
- Document public functions in headers and keep consistent allocation/free policies.

## Authors / Group
Update this section with your team members and contributions:

- A104100 — Student 1 (replace)
- A104356 — Student 2 (replace)
- A104439 — Student 3 (replace)

## Suggested improvements
- Add an `EXAMPLES.md` with datasets and queries samples.
- Precisely document query formats and accepted parameters for each supported query.
- Implement unit tests for parsers and managers.
- Consider simple persistence (dump/load) for very large datasets.

---

If you want, I can perform one of the following next steps (pick one):
1. Fill the "Authors" section with the real names and student IDs if you provide them.
2. Extract supported queries automatically from `src/Queries.c` and `interativo/queries.c` and append a "Supported queries" section.
3. Create an `examples/` directory with a small sample dataset and `queries.txt` to test batch mode.

Tell me which option you want next (or request another change to the README).# LI3-Spotifum
