# AutoREACTER-LibraryValidator Toolkit

This repository validates and populates `functional_groups_library.py` and `reaction_library.py` for the **https://github.com/NanoCIPHER-Lab/AutoREACTER** project.

It provides a controlled environment to test SMARTS patterns, reaction definitions, and atom mapping logic before integration into the main engine.

## The toolkit ensures:

- Functional group SMARTS are syntactically valid  
- Reaction SMARTS parse correctly in RDKit  
- All atoms are properly mapped  
- Substructure matching behaves as expected  

This repository does **not** perform polymer simulations — it is strictly a library validation layer.

## How to Contribute

1. Add your new functional groups and/or reactions to `functional_groups_library.py` and/or `reaction_library.py`.  
2. Run the provided notebook to validate and generate the updated files.  
3. Run **AutoREACTER** and verify that the reaction works with the relevant monomers.  
4. If AutoREACTER encounters an issue or error, open an issue at:  
   https://github.com/NanoCIPHER-Lab/AutoREACTER  
5. If the reaction runs successfully, open an issue in the same repository and attach all validated files. Including simulation files (e.g., LAMMPS input/output) is strongly encouraged.

**https://colab.research.google.com/drive/1DEfe_0sZL604LmEGahb5vuUhEtSBu7-v?usp=sharing**

We will review submissions and integrate approved functional groups and/or reactions into the main library.
