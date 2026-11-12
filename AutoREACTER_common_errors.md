AutoREACTER Common Errors and their Solutions

The following errors originate from running AutoREACTER with new functional groups and/or reactions to add to AutoREACTER's functional group and/or reaction libraries. By default, the following errors do not occur with reactions currently supported by AutoREACTER. For the full list of supported reactions, please visit AutoREACTER documentation (https://autoreacter.org/supported-reactions.html). 

Common Errors

1. 'AutoREACTER.detectors.reaction_detector.EmptyReactionListError: No reaction instances found for the specified monomer combination'

    If the functional groups and/or reactions you would like to add to the AutoREACTER libraries require creating new Python files, this error is thrown as the registries do not include the new files. 
    Solution: resolving this error involves updating two registry files in your local directory: './AutoREACTER/detectors/functional_groups_library/registry.py' and './AutoREACTER/detectors/reactions_library/registry.py'. The 'registry.py' files are formatted similarly. In the beginning of both registry files, the functional groups or reactions in the new Python files need to be imported; they need to be added to the import section of the file. The format is,

            from .{py_file_name} import {FUNCTIONAL_GROUPS, REACTIONS} as {GROUPS, REACTION}

    where the options in brackets are replaced with the name of the python file (minus the file extension), whether the functional group or reaction registry is being updated, and how the functional group or reaction is being defined as in the file. Afterwards, the modules section is updated in both registries. For example, if a polyether reaction is being added, the import statement in the registry would be:

            from .polyethers import REACTIONS as POLYETHERS

    where 'POLYETHERS' will be added to the '_REACTION_MODULES' list. 

    For the 'registry.py' file in the reaction library directory, the import error section needs to be updated with the new Python file, too. 

2. 'AutoREACTER.reaction_preparation.ff_wrapper.ff_validator.ForceFieldValidationError:
All zeros in line {} of {} coeffs.' 

    As stated in the error statement, there are coefficients in the force field data file that are zero. In the case that the atoms are correctly typed, the 'pcff.frc' file needs to be edited such that the molecular structure is parameterized. The use of equivalent atom types is useful to obtaining non-zero coefficients. The PCFF file can be found in the following directory: './AutoREACTER/reaction_preparation/ff_wrapper/FF_files/pcff.frc'. If the atoms are incorrectly typed, the error is caused by LUNAR. Submit an issue to the LUNAR Github to resolve the error. 
