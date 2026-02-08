# mermaid_excel
A simple excel based tool to generate a relationship graph out of tables.

How It Works
The workbook contains two tables:

1. Entities Table (Entities)
Each row represents a node in the Mermaid diagram.

Required columns:

NodeID — unique identifier used in Mermaid

DisplayName — human‑readable label

CssClass — optional Mermaid class for styling

Class — a property displayed under the node

Comment — a property displayed under the node

You can add any additional columns, and they will automatically appear as + property: value inside the node.

2. Relationships Table (Relationships)
Each row represents an edge in the Mermaid diagram.

Columns:

SourceNodeID

RelationshipLabel

TargetNodeID

These generate Mermaid edges like:

Code
A-->|" relates_to "|B
Power Query Output
Power Query reads both tables and produces a complete Mermaid diagram wrapped in:

markdown
```mermaid
graph TD
  ...
```
The script:

Builds nodes dynamically

Includes all non‑excluded columns as properties

Skips empty values

Builds edges from the relationships table

Outputs a single Markdown‑ready Mermaid block

You can copy/paste the output directly into:

GitHub Markdown

GitHub Pages

Azure DevOps Wiki

Mermaid Live Editor

Any Mermaid‑compatible renderer

Example Model (Star Wars Mini‑Ontology)
Entities:

NodeID	CssClass	DisplayName	Class	Comment
Luke_Skywalker	hero-node	Luke Skywalker	Jedi	Trained by Yoda
Darth_Vader	villain-node	Darth Vader	Sith Lord	Former Jedi Knight
Yoda	mentor-node	Yoda	Jedi Master	Trains young Jedi
The_Force	concept-node	The Force	Energy Field	Binds the galaxy together
Lightsaber	object-node	Lightsaber	Weapon	Elegant weapon for a civilized age
Relationships:

SourceNodeID	RelationshipLabel	TargetNodeID
Luke_Skywalker	trained_by	Yoda
Darth_Vader	opposes	Luke_Skywalker
Luke_Skywalker	uses	Lightsaber
Darth_Vader	uses	Lightsaber
Yoda	teaches	Luke_Skywalker
The_Force	empowers	Luke_Skywalker
The_Force	empowers	Darth_Vader
This produces a fully rendered Mermaid graph.
