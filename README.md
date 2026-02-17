# AutoREACTER-LibraryValidator Toolkit

This repository validates and populates `functional_groups_library.py` and `reaction_library.py` for the **NanoCIPHER-Lab/AutoREACTER** project.

It provides a controlled environment to test SMARTS patterns, reaction definitions, and atom mapping logic before integration into the main engine.

## The toolkit ensures:

- Functional group SMARTS are syntactically valid  
- Reaction SMARTS parse correctly in RDKit  
- All atoms are properly mapped  
- Substructure matching behaves as expected  

This repository does **not** perform polymer simulations — it is strictly a library validation layer.
