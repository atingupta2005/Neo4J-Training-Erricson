# Java Documentation
 - https://github.com/neo4j/neo4j-documentation/tree/4.1/embedded-examples


# Neo4j - Match by multiple relationship types
 - https://stackoverflow.com/questions/46132345/neo4j-match-by-multiple-relationship-types
 - match (Yoav:Person{name:"Yoav"})-[:liked]->(movie:Movie), (Yoav)-[:watched]->(movie), (Yoav)-[:other]->(movie) return movie

# Setup Neo4J using Docker
 - https://neo4j.com/docs/operations-manual/current/docker/

# How to take help of all available commands in Cypher-shell. We need to take help like linux man pages
 - Need to explore
 
# Undo last Cypher Query if passed by mistake:
 - Currently its not feasible
  - https://stackoverflow.com/questions/19885901/undo-the-last-neo4j-cypher-query
  - https://community.neo4j.com/t/how-to-undo-write-operations/6490


# How to take backup of system database
 - We can use the same method:
	 - neo4j-admin dump --database=system  --to=/usr/local/dumps/system


