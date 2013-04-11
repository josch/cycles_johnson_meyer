Finding all the elementary circuits of a directed graph
-------------------------------------------------------

Algorithm by D. B. Johnson

    Finding all the elementary circuits of a directed graph.
    D. B. Johnson, SIAM Journal on Computing 4, no. 1, 77-84, 1975.
    http://dx.doi.org/10.1137/0204007

Usage
-----

    make
    echo "0 1\n0 2\n1 0\n1 3\n2 0\n3 0\n3 1\n3 2" | java de.normalisiert.utils.graphs.TestCycles 4

First argument is the number of vertices. Ordered pairs of space separated
vertices are given via standard input and make up the directed edges of the
graph.

DOT file input
--------------

For simplicity, there is no DOT file parser included but the following allows
to create a suitable argument string and standard input for simple DOT graphs.

Given a DOT file of a simple (no labels, colors, styles, only pairs of
vertices...) directed graph, the following lines generate the number of
vertices as well as the edge list expected on standard input.

        sed -n -e '/^\s*[0-9]\+;$/p' graph.dot | wc -l
        sed -n -e 's/^\s*\([0-9]\) -> \([0-9]\);$/\1 \2/p' graph.dot

The above lines work on DOT files like the following:

    digraph G {
      0;
      1;
      2;
      0 -> 1;
      0 -> 2;
      1 -> 0;
      2 -> 0;
      2 -> 1;
      }

They would produce the following output:

    3
    0 1
    0 2
    1 0
    2 0
    2 1
