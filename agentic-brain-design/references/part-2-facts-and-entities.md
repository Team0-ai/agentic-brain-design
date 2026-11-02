# Part 2: facts and entities

Full article: [Facts and entities](https://team0.ai/learn/facts-and-entities.md).

Read when the user is implementing the representation exercise in /learn or reviewing identity mistakes.

Identify the people, companies and work items their questions actually need. Help implement a representation with stable identifiers, readable names, source-backed statements and attribution. This can be files, a database or an existing memory system. Use the article's starter schema if it fits; avoid introducing a graph or a large ontology without a demonstrated need.

Separate names used for discovery from evidence of identity. A shared inbox is not necessarily a person, a free-mail domain is not an employer, and a similar name alone is insufficient to merge records. Keep uncertain cases separate or ask. Support aliases and other scripts where the user's sources require them.

When extracting statements, take identifiers from source structure where available, preserve who said the words and which input supports them, and resolve relative dates against the source date. Do not let a model invent keys or turn a question into a fact. In SQLite, enable foreign keys on every connection if using references.

Test one person appearing in two sources, two people sharing a name, an uncertain alias, a relative date and a statement that has no identifiable subject. Inspect a small sample before processing real collections.

Ask the same test questions and score again. Check identity errors and omissions. Changed values and unsupported claims still require the choices in later parts. Let measured results determine whether more structure is helpful.
