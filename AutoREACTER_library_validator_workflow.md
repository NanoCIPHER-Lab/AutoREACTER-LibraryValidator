AutoREACTER Library Validator Workflow

1. Install AutoREACTER Library Validator from Github repository

2. Open Jupyter notebook in an Interpreter (must be compatible to open and edit '.ipynb' files). 

3. Obtain SMILES strings of monomers and other reactant structures. The SMILES Generator and Checker available at https://www.cheminfo.org/flavor/malaria/Utilities/SMILES_generator___checker/index.html can be used to generate or verify SMILES strings. 

4. Run cells 1-3 to ensure the SMILES strings have correct syntax

5. Define the monomer functionality. Identify every functional group in the monomer that participates in the reaction using an appropriate SMARTS pattern. The `functionality_type` specifies how the reactive groups are arranged within the monomer. Currently supported options are `mono` for a single reactive functional group, `di_identical` for two identical reactive groups, `di_different` for two different reactive groups, and `vinyl` for vinyl-based reactive structures.  

6. Run cells 4-7 to validate the functional-group SMARTS. The generated images show successful monomer/functionality matches, not necessarily every supplied monomer. Check every intended monomer/group combination is represented, since these cells can finish without errors even when some inputs do not match. 

7. Next, define the reaction definitions in cell 8, 'Define reaction definitions.' If there are multiple steps in the reaction, each reaction will need to be defined. The following needs to be defined when creating a reaction: 
    1. 'same_reactants': a binary that determines if two of the same reactant react with each other.
    2. 'reactant_1', 'reactant_2', etc.: a string describing the reactants
    3. 'product': a string describing the product
    4. 'delete_atom': a binary determining whether atoms are removed during the reaction. For example, in reactions using the REACTER protocol that generate side products like polycondensation, side product water molecules are removed from the simulation box.
    5. 'reaction': the SMARTS reaction string
    6. 'reference': a dictionary of references of the SMARTS strings and reaction mechanisms. 

8. Run cells 9-12 to validate the defined reactions. Each definition is tested independently using `sample_smiles[0]` and, when `same_reactants` is `False`, `sample_smiles[1]`; products are not passed to later definitions. Reactant images are displayed for each definition, but the final product visualization shows only the last definition's products. To inspect every step of a multi-step reaction, test one definition at a time with the appropriate input SMILES, including intermediate structures where needed, and inspect its products before proceeding. 

9. After checking the validation results, integrate the definitions into the appropriate AutoREACTER Python files. Merge the reaction entries from cell 8 into a `REACTIONS` dictionary under './AutoREACTER/detectors/reactions_library'. Similarly, merge the functional-group entries from cell 4 into a `FUNCTIONAL_GROUPS` dictionary under './AutoREACTER/detectors/functional_groups_library'. If the validated reactions and functional groups do not fit into current Python files, create new files with the reactions and functional groups dictionary.  

10. Create a JSON file to setup a system with the newly created functional groups and reactions. If new functional groups or reaction type files were created, add to 'registry.py' files found in the directories './AutoREACTER/detectors/functional_groups_library' and './AutoREACTER/detectors/reactions_library'.

11. Run AutoREACTER with the JSON file to generate all files required to simulate the defined reaction using 'fix bond/react'. It is best to test the defined reaction in the './examples' directory. View reactions modeled in the images folder in the directory './examples/AutoREACTER_outputs/[name_of_reaction]/images'. If there are missing reactions, return to the Library Validator Jupyter notebook and add or edit reactions and/or functional groups. 
