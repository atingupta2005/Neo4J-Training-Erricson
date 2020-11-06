# Java Documentation for create Nodes from Java code
 - https://github.com/neo4j/neo4j-documentation/tree/4.1/embedded-examples


# Neo4j - Match by multiple relationship types
 - Refer:  https://stackoverflow.com/questions/46132345/neo4j-match-by-multiple-relationship-types
 - match (Yoav:Person{name:"Yoav"})-[:liked]->(movie:Movie), (Yoav)-[:watched]->(movie), (Yoav)-[:other]->(movie) return movie

# Setup Neo4J using Docker
 - Refer
	- https://neo4j.com/docs/operations-manual/current/docker/
	- https://github.com/atingupta2005/Neo4J-Training-Erricson/blob/master/Day%203/12-Causal%20Clustering%20in%20Neo4j-A-Via%20Docker.txt
 

# How to take help of all available commands in Cypher-shell. We need to take help like linux man pages
 - Need to explore
 
# Undo last Cypher Query if passed by mistake:
 - Currently its not feasible
  - Refer:
    -  https://stackoverflow.com/questions/19885901/undo-the-last-neo4j-cypher-query
    - https://community.neo4j.com/t/how-to-undo-write-operations/6490


# How to take backup of system database
 - We can use the same method:
	 - neo4j-admin dump --database=system  --to=/usr/local/dumps/system


# How to create procedure in Neo4J
 - Refer https://neo4j.com/docs/java-reference/current/extending-neo4j/procedures-and-functions/introduction/#extending-neo4j-procedures-and-functions-introduction

# How to fix database inconsistency? Can copy of database fix inconsistency?
 - neo4j-admin copy does not copy inconsistent nodes. Refer to below blog:
  - https://neo4j.com/developer/kb/database-compaction-in-40-using-neo4j-admin-copy/
  - https://medium.com/neo4j/new-neo4j-4-0-features-copy-a-database-and-more-c51d1744a7e3
  
  # Features of copy tool:
   - Reduce DB size (which was growing through continuous writes and deletes) through ID reuse and reorganisation of relationships and properties
   - It defragmented and co-located nodes and relationships
   - Able to skip defect records in case you somehow got inconsistencies in your store
   - Store-utils also allowed you to skip nodes with certain labels or skip certain labels, properties and relationship-types entirely during the process.
   - Has a number of fine-grained options to configure how the copy is created
     - Filtering out nodes with a specific label
	 - Ignoring certain labels
	 - Ignoring specified relationship types
	 - Skipping over property keys
	 
  
# How to redicrect output from Cypher-Shell to text file?
 - There is no specific way provided from neo4j for this feature.

# neo4j-admin dump vs neo4j-admin backup, which one to chose over the other?
 - Offline can be performed on any edition of the Neo4j database, including the free Community edition
 - For the cases where you really can’t afford for the database to be offline, the online backup functionality comes into play, but this is available only in the Neo4j Enterprise edition
 - Offline backup process will work on any edition of the Neo4j database, but it will most probably only be used on the Community edition
 - If you have access to the Enterprise edition, you may as well make use of the online backup functionality
 - The online backup functionality is available only in the Enterprise edition of Neo4j, but it’s a robust and reliable way to back up your single, or clustered, Neo4j environment without requiring any downtime

# Show database sizes of all the databases in one commands
  - No command is available for this in Neo4J
  - For single database in Neo4J Browser:
    - :USE neo4j
	- :sysinfo

# Some exta material
  - Data Profiling: A Holistic View of Data using Neo4j
    - https://neo4j.com/blog/data-profiling-holistic-view-neo4j/


# Checkpoint:
https://neo4j.com/developer/kb/checkpointing-and-log-pruning-interactions/#:~:text=Overview,time%20after%20an%20improper%20shutdown.

# Space Reclaim:
https://neo4j.com/docs/operations-manual/current/performance/space-reuse/

