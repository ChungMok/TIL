## Common Queries  
Match (n) Return n  
Match (p:Person) return p  
CALL db.schema.visualization  
CALL db.propertyKeys  
Match (n:Indicator) Return properties(n), ID(n)  
Match (m:Movie {released:2006}) RETURN m.title  
Match (m:Movies) <--(:Person {name: 'Tom Hanks'}) RETURN m.title  
Match (a:Person)-[:ACTED_IN]->(m.Movie) WHERE a.name = 'Tom Cruise' RETURN m.title as Movie  
