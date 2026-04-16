# AI for Redistricting – Gerrymandering Analysis with Markov Chains
                                                                                                                                                                                       
  ## Overview     
  This project analyzes Pennsylvania's 2022 State Senate redistricting map using algorithmic and statistical methods to detect potential gerrymandering.                                               
                                                                                                                                                                                                       
  We generate ensembles of alternative districting plans using a Markov Chain approach and compare them to the enacted map using fairness metrics. The goal is to determine whether the observed map is
   typical or an outlier relative to neutral alternatives.                                                                                                                                             
                                                                                                                                                                                                       
  ## Key Concepts 
  - Redistricting and gerrymandering
  - Markov Chains and random walks on graphs
  - Ensemble analysis of districting plans                                                                                                                                                             
  - Quantitative fairness metrics
  - Short Burst optimization (graduate analysis)                                                                                                                                                       
                  
  ## Approach                                                                                                                                                                                          
  The project follows a structured pipeline:
                                                                                                                                                                                                       
  1. Data Preparation
     - Collect precinct-level geographic and election data from multiple elections                                                                                                                     
     - Clean and validate data using MAUP (Modifiable Areal Unit Problem toolkit)                                                                                                                      
     - Nest precincts within counties where possible
     - Fix small rook lengths and verify maup.doctor returns true                                                                                                                                      
                                                                                                                                                                                                       
  2. Graph Modeling                                                                                                                                                                                    
     - Model Pennsylvania using a dual graph representation, where each node represents a precinct and edges represent geographic adjacency                                                            
     - Construct adjacency using rook contiguity (shared boundaries)                                                                                                                                   
     - This graph defines the state space for redistricting and enables valid transitions during sampling                                                                                              
                                                                                                                                                                                                       
  3. Ensemble Generation                                                                                                                                                                               
     - Use a Markov Chain Monte Carlo (MCMC) approach with the ReCom algorithm                                                                                                                         
     - Generate at least 2 independent ensembles using different election datasets                                                                                                                     
     - Generate large ensembles of valid districting plans under constraints such as contiguity and population balance
     - Explore the space of possible districting maps through stochastic sampling                                                                                                                      
     - Verify chain convergence before drawing conclusions                                                                                                                                             
                                                                                                                                                                                                       
  4. Metric Evaluation                                                                                                                                                                                 
     Each generated map is evaluated using:
     - Efficiency Gap                                                                                                                                                                                  
     - Seat distribution (Democratic/Republican wins)
     - Compactness (Polsby-Popper) or Cut edges (boundary complexity)                                                                                                                                  
                                                                                                                                                                                                       
  5. Short Burst Analysis                                                                                                                                                                
     - Run Short Burst optimization to explore extreme regions of the plan space                                                                                                                       
     - Assess Pennsylvania's capacity for VRA districts                                                                                                                                                
     - Evaluate partisan responsiveness under swing scenarios                                                                                                                                          
                                                                                                                                                                                                       
     - Compare the enacted map to the ensemble distribution                                                                                                                                            
     - Identify whether it behaves as a statistical outlier relative to neutral alternatives
     - Produce marginal box plots (signature of gerrymandering)                                                                                                                                        
                                                                                                                                                                                                       
  ## Results                                                                                                                                                                                  
  The analysis produces:                                                                                                                                                                              
  - Histograms of metric distributions (per ensemble)                                                                                                                                                  
  - Marginal box plots (signature of gerrymandering) 
  - Convergence trace plots                                                                                                                                                                            
  - Visual comparisons between enacted and generated maps
                                                                                                                                                                                        
  These results provide a quantitative basis for evaluating whether Pennsylvania's districting plan is typical or potentially gerrymandered.                                                           
                                                                                                                                                                                                       
  ## Acknowledgments                                                                                                                                                                                   
  We would like to thank the Redistricting Data Hub for providing accessible and well-structured datasets that made this analysis possible.                                                            
                                                                                                                                           
 ## Team
- Guillermo R.  
- Kelly C.  
- Elyas Y.                                                                                                                                                                         
            
  ## Notes                                                                                                                                                                                  
  - At least 2 election datasets are used to strengthen analysis
  - Chains are run long enough to ensure convergence                                                                                                                                                   
  - Focus is on comparing observed outcomes to neutral baselines