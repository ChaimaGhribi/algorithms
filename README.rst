#### 
Algorithms
####


This guide describes a set of algorithm dealing with the problems of VNF placement, SFC/VNF-FG placement and chaining, VNF scaling....
Then we describe the inputs and output of these algorithms.


===============================

**Authors:**

Copyright (C) `Marouane Mechteri <https://www.linkedin.com/in/mechtri>`_


================================

.. contents::


Placement algorithm
==============================================================================


The objective of these optimization algorithms is to place VMs or VNFs intelligently in underlying NFVIs and to steer traffic flows across the VNFs while using efficiently the infrastructure resources. 

These algorithms are: 

============================================================= ===================================================== =======
Folders                                                       Algorithms                                            Publications
============================================================= ===================================================== =======
`SFC_placement_DP_algos <SFC_placement_DP_algos>`_            Dynamic Programming algorithms                        1
`SFC_placement_Eigen_algo <SFC_placement_Eigen_algo>`_        An Eigendecomposition-based algorithm                 2
`SFC_placement_MCTS_algo <SFC_placement_MCTS_algo>`_          An algorithm based on Monte Carlo Tree Search (MCTS)  3
`SFC_placement_ILP_algo <SFC_placement_ILP_algo>`_            An Integer Linear Programming (ILP) model             4
`SFC_placement_Greedy_algo <SFC_placement_Greedy_algo>`_      A Greedy algorithm                                    5
============================================================= ===================================================== =======

1. A Dynamic Programming algorithm: `A Dynamic Programming Algorithm for Joint VNF Placement and Chaining <https://www.researchgate.net/publication/311313588_A_Dynamic_Programming_Algorithm_for_Joint_VNF_Placement_and_Chaining>`_
2. An Eigendecomposition-based algorithm: `A Scalable Algorithm for the Placement of Service Function Chains <https://www.researchgate.net/publication/305821223_A_Scalable_Algorithm_for_the_Placement_of_Service_Function_Chains>`_
3. An algorithm based on the Monte Carlo Tree Search (MCTS): `An Efficient Algorithm for Virtual Network Function Placement and Chaining <https://www.researchgate.net/publication/318579373_An_efficient_algorithm_for_virtual_network_function_placement_and_chaining>`_
4. An Integer Linear Programming (ILP) model: `A green VNFs placement and chaining algorithm <https://www.researchgate.net/publication/326275787_A_green_VNFs_placement_and_chaining_algorithm>`_ , `A Green VNF-FG Embedding Algorithm <https://www.researchgate.net/publication/327635874_A_Green_VNF-FG_Embedding_Algorithm>`_
5. A Greedy algorithm: `VNF Placement and Chaining in Distributed Cloud <https://www.researchgate.net/publication/312570696_VNF_Placement_and_Chaining_in_Distributed_Cloud>`_


Inputs and Output of the placement algorithms
=============================================


The inputs of each placement algorithm are:

* The client request is modeled by a graph composed by a set of virtual nodes representing VNF and a set of virtual links connecting them. `instanceIG3-0 <https://raw.githubusercontent.com/MarouenMechtri/algorithms/master/SFC_placement_DP_algos/instanceIG3-0>`_ is an example of a request composed by 3 VNFs and 2 links and representing a service chain::

   Number of Servers
   3 1 1
   Nodes
   0 0 2 3 1 0
   1 1 2 3 1 0
   2 2 2 3 1 0
   EDGES
   0 1 100
   1 2 100

* The substrate graph is modeled also by a graph. `instanceRG15-0 <https://raw.githubusercontent.com/MarouenMechtri/algorithms/master/SFC_placement_DP_algos/instanceRG15-0>`_ is an example of a substrate infrastructure.

The output of the algorithms is a file containing the mapping result of the client request on the substrate infrastructure. The file name of the algorithm output has this format: 

SolutionMappingALGO-SUBSTRATE_FILE_NAME-REQUEST_FILE_NAME. 

For example, when executing the dynamic programming algorithm the output file name is SolutionMappingDP-instanceRG13-0-instanceIG3-0.


