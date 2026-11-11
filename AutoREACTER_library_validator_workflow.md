AutoREACTER Library Validator Workflow

1. Install AutoREACTER Library Validator from Github repository

2. open Jupyter notebook in Interpreter (must be compatible to open and edit '.ipynb' files). Create a virtual environment

3. The Python library RDKit must be imported before testing reactions. 

4. Obtain SMILES strings of monomers and other reactant structures. 

5. Run cells 1-3 to ensure the SMILES strings have correct syntax

6. Next, define the monomer functionality. For each monomer, each functional group that participates in the reaction must be identified using a SMARTS string. The 'functionality_type' determines whether there is one, multiple of the same group, multiple of different groups, or a vinyl structure are in the monomer. Currently, the 'functionality_type' options are mono, di_identical, di_different, and vinyl. 

7. Run cells 4-7 to validate the SMARTS strings functionality. An image of the two structures will be generated of all defined monomers. In order for the cells to run without errors, the contents of cell 4 needs to be inserted into an appropriate Python file in the functional groups library, found in the directory './AutoREACTER/detectors/functional_groups_library'. If none of the current Python files are fit the tested chemistry, create a new Python file with the contents of cell 4 of the Library Validator. 

8. Next, define the reaction definitions in cell 8, 'Define reaction defintions.' If there are multiple steps in the reaction, each reaction will need to be defined. The following needs to be defined when creating a reaction: 
    1. 'same_reactants': a binary that determines if two of the same reactant react with each other.
    2. 'reactant_1', 'reactant_2', etc.: a string describing the reactants
    3. 'product': a string describing the product
    4. 'delete_atom': a binary determining whether atoms are removed during the reaction. For example, in reactions using the REACTER protocol that generate side products like polycondensation, side product water molecules are removed from the simulation box.
    5. 'reaction': the SMARTS reaction string
    6. 'reference': a dictionary of references of the SMARTS strings and reaction mechansims. 

9. Run cells 9-12 to validate the defined reactions. Images identifying the functional groups and the products of the reactions are generated at the end. 

10. If all cells run without errors, either add the SMARTS reaction string(s) to the appropriate Python file in the reactions library found in the directory './AutoREACTER/detectors/reactions_library' or create a new Python file with the contents of cell 8. 

11. Create a JSON file to setup a system with the newly created functional groups and reactions. If new functional groups or reaction type files were created, add to 'registry.py' files found in the directories './AutoREACTER/detectors/functional_groups_library' and './AutoREACTER/detectors/reactions_library'.

12. Run AutoREACTER with the JSON file to generate all files required to simulate the defined reaction using 'fix bond/react'. It is best to test the defined reaction in the './examples' directory. View reactions modeled in the images folder in the directory './examples/AutoREACTER_outputs/[name_of_reaction]/images'. If there are missing reactions, return to the Library Validator Jupyter notebook and add or edit reactions and/or functional groups. 