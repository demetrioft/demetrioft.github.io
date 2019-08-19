
## Complex network analysis (CNA)

**CNA** is the study of complex networks—their structure, properties, and dynamics. You can think of CNA as a generalization of social network analysis (SNA) to include non-social networks.
                 
## Basics of networks
NCA offer Insights on:

● Important entities: influencers in social network
● Pathfinding: most efficient transport path
● Clustering: finding communities

### Levels of Analysis
Social network analysis addresses social networks at three levels: microscopic, mesoscopic, and macroscopic.
                
- **Microscopic level**, we view a network as an assembly of individual nodes, dyads (pairs of connected nodes; essentially, edges), triads (triples of nodes, connected in a triangular way), and subsets (tightly knit groups of nodes). 

- **Mesoscopic level** view focuses on exponential random graph models (ERGMs), scale-free and small-world networks, and network evolution. Finally, at the 

- **Macroscopic level**, the more general complex network analysis fully absorbs SNA, abstracting from the social origins of social networks and concentrating on the properties of very large real-world graphs, such as degree distribution, assortativity, and hierarchical structure
                
##  CNA packages

**NetworkX**—a powerful Python library for network analysis and visualization. You know how to construct a simple graph incrementally, add node attributes, do some simple visualization, and save the networks to and restore from files. Of these tasks, it is visualization that NetworkX does not handle well. NetworkX’s performance is acceptable up to about 100,000 nodes.               

**Networkit** - 

NetworkX and NetworKit are compatible at the graph level. If you are in a rush, construct a network in NetworkX and convert it to NetworKit for further analysis.
                
## Networkx API Examples

- creating a graph:
```
In [1]: import networkx as nx 
In [2]: G = nx.Graph() 
In [4]: G.add_nodes_from([1, 2, 3]) 
In [5]: G.nodes() 
Out[5]: [1, 2, 3] 
In [6]: G.add_edge(1, 2) 
In [7]: G.edges() 
Out[7]: [(1, 2)]
```

- drawing a network:
```
In [10]: nx.draw(G)
 In [11]: import matplotlib.pyplot as plt 
 In [12]: plt.show()
```
## Creating a Network
NetworkX provides several mechanisms for adding nodes and edges to an existing graph: one by one, from a list or another graph. Likewise, you can remove nodes or edges one by one or by using a list.
               

G.nodes and G.edges store all nodes and edges, respectively, in the form of NodeView and EdgeView.
                
The second option is to call methods G.nodes and G.edges. If called without any parameters, the methods return the same views as their attribute counterparts.
           
NetworkX provides method nx.relabel_nodes that takes a graph and a dictionary of old and new labels and either creates a relabeled copy of the graph (copy=True, default) or modifies the graph in place
              

you can use selection operator [] to access the AtlasView: the edges incident to the node, and their attributes:
                
An attribute is implemented as a dictionary associated with the node or edge. The dictionary keys are attribute names. As such, they must be immutable: int, float, bool, str, and so on. There are no limitations on the values.
                


Define attributes at the time of adding nodes or edges:
                


There is a method G.add_weighted_edges_from for adding weighted edges.
                


Define or change an attribute of existing nodes and edges by calling nx.set_node_attributes or nx.set_edge_attributes:

 ```              
nutrients = set((​"B12"​, ​"Zn"​, ​"D"​, ​"B6"​, ​"A"​, ​"Se"​, ​"Cu"​, ​"Folates"​, ​  ​"Ca"​, ​"Mn"​, ​"Thiamin"​, ​"Riboflavin"​, ​"C"​, ​"E"​, ​"Niacin"​)) ​  
nutrient_dict = {node: (node ​in​ nutrients) ​for​ node ​in​ G} ​
  nx.set_node_attributes(G, nutrient_dict, ​"nutrient"​)

```
Define or change an attribute of individual existing nodes and edges directly through the dictionary interfaces G.node (indexed by node labels) and G.edge (double indexed by start and end node labels):

```                
In [8]: G.node[1]['label'] = 'blue' 
In [9]: G.nodes(data=True) 
Out[9]: [(1, {'label': 'blue'}), (2, {}), (3, {})
```
  
                

## Network Visualization 
The process of network visualization consists of two phases: layout and rendering. At the layout phase, the software selects geometric positions of each node according to a layout algorithm.
                

At the rendering phase, NetworkX draws the nodes, labels, and edges at the prescribed positions, using the default or specified shapes, fonts, and colors. You can see the graphical output on the screen, save it into a file (supported formats include PNG, PDF, PostScript, EPS, and SVG), or both.
                

For most complex networks, the spring layout (the default layout for nx.draw_networkx) produces the most pleasing output. Note that Matplotlib does not accurately place node labels (to the extent that I preferred not to show them in the figure at all). Some of them badly overlap.
                

**graphviz** is an open source graph visualization tool written in C. Among other things, it provides yet another layout engine, which is typically better than any of the engines mentioned previously.
                
**Gephi**  is an excellent network construction and analysis tool, but it is interactive. Gephi cannot be programmed to execute batches of tedious analysis tasks, vary parameters automatically, or integrate with machine learning or predictive analytics software.

GraphML is the best interchange format between NetworkX and Gephi. Sometimes, Gephi is the quickest way to analyze a not-so-large network once or twice.
                
               

There is no implicit integration between Gephi and NetworkX. However, you can use Gephi graph file exporter (File > Export > Graph file…) to save your network into a file that could be imported by NetworkX. GraphML is the preferred interchange format because it preserves all calculated measures (such as centralities and modularity classes) as node attributes. This way you could use Gephi to perform a quick-and-dirty interactive analysis of a network and save it into a graphml file for further processing.



> Written with [StackEdit](https://stackedit.io/).
