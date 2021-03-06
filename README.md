# Libgraph

[![Build](https://github.com/asimos-bot/libgraph/workflows/Build/badge.svg)](https://github.com/asimos-bot/libgraph/actions/workflows/build.yml)
[![Tests](https://github.com/asimos-bot/libgraph/workflows/Tests/badge.svg)](https://github.com/asimos-bot/libgraph/actions/workflows/tests.yml)
![Test Coverage Badge](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/asimos-bot/1062ce0f390bb2b6458d29f225cc08b5/raw/libgraph__heads_main_coverage.json)
![Lines of Code Badge](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/asimos-bot/1062ce0f390bb2b6458d29f225cc08b5/raw/libgraph__heads_main_loc.json)

Graph library for C. Features:

* General graph structure management. Using adjency lists internally.
* Convert graph to matrix representation.
* Conversion from and back `.dot` files.
* Algorithms like:
  * Topological ordering

## Todo

- [x] Get matrix representation of the graph structure
- [x] Add stack struct to lib
- [x] Add set struct to lib
- [x] Topological sorting
- [ ] Build graph from DOT file
- [ ] Mealy machine implementation
  - [ ] Mealy machine struct and data
- [ ] Moore machine implementation
  - [ ] Moore machine struct and data
- [ ] Convert mealy machine to moore machine
- [ ] Convert moore machine to mealy machine
- [ ] NFA
  - [ ] NFA struct and data
  - [ ] Build from matrix
  - [ ] Build from csv
  - [ ] Write to csv
- [ ] DFA
  - [ ] DFA struct and data
  - [ ] Build from matrix
  - [ ] Build from csv
  - [ ] Write to csv
  - [ ] DFA minimization
  - [ ] EBNF 
- [ ] Convert NFA to DFA
- [ ] Convert DFA to NFA
- [ ] EBNF to DFA - Scanner

## API notation

* Struct initialization functions (`*_init`):
  * Must have an argument for an address where the struct can be initialized at
    * If NULL a struct will be dynamically allocated
    * return the address of the struct, no matter if it was statically or dynamically allocated
    * exception: stack and hashmap are always dynamically allocated, so no optional field
  * If struct contains a DATA struct as a field
    * There must be an argument for the data format being used for initialization
    * There must be an argument for the constructor parameter

* Struct destructor functions (`*_free`):
  * Don't deallocate struct itself
    * User must call `free(struct_ptr)` himself
    * Exception: edge, stack and hashmap

* Memory layout
  * edges are stored in a linked list pointed by the node struct
  * nodes are dynamically allocated and have their pointers stored in the graph struct
