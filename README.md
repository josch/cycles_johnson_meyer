Finding all the elementary circuits of a directed graph
-------------------------------------------------------

Algorithm by D. B. Johnson

    Finding all the elementary circuits of a directed graph.
    D. B. Johnson, SIAM Journal on Computing 4, no. 1, 77-84, 1975.
    http://dx.doi.org/10.1137/0204007

Usage
-----

    make
    java de.normalisiert.utils.graphs.TestCycles 4 0,1 0,2 1,0 1,3 2,0 3,0 3,1 3,2

First argument is the number of vertices. Subsequent arguments are ordered
pairs of comma separated vertices that make up the directed edges of the
graph.

DOT file input
--------------

For simplicity, there is no DOT file parser included but the following allows
to create a suitable argument string for simple DOT graphs.

Given a DOT file of a simple (no labels, colors, styles, only pairs of
vertices...) directed graph, the following line produces commandline
arguments in the above format for that graph.

	echo `sed -n -e '/^\s*[0-9]\+;$/p' graph.dot | wc -l` `sed -n -e 's/^\s*\([0-9]\) -> \([0-9]\);$/\1,\2/p' graph.dot`

The above line works on DOT files like the following:

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

It would produce the following output:

    3 0,1 0,2 1,0 2,0 2,1
