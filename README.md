# Model Link Evaluator:

Have you ever had to deal with a task which required you to find a relation between stock.move.line and account.move which made you feel like it’s a repetitive and time consuming process to check fields to find a relation between these (or any two) models?

This tool will make it much easier to find such relations between ANY 2 models by taking help of graph traversal algorithms!

## Input:

Model 1 Name: model1 <br/>
Model 2 Name: model2 <br/>
[Optional] List of Installed Modules

## Output:

=> Relation between the two models: <br/>
Model1.relational_field_name.other_field.model2

[Not sure how complex but possibly also a list of installed modules that were used for this link]

## How would this work?

1. We navigate through all model.py files in the list of installed modules (or all modules if left blank) and find all one2many, many2one, many2many fields and the model that they are associated with
2. We map all these relationships as a Graph data structure with details such as modules that define the link and the type like one2many, many2many, many2one etc
3. Use BFS algorithm to find all links given a start and end model and return the link in the form of a python expression

## Future Extensions:

1. VS Code Extension
2. Convert Python program to WASM: https://wasmer.io/posts/py2wasm-a-python-to-wasm-compiler and then build a SPA (single page application) which can be hosted on github.io pages
3. Ask input for API username and password of a client's database and then find the link between the two models in the client's database. For this we can use the ir.model and ir.model.fields tables to construct graph to find the link between the two models
4. Support for multiple odoo versions