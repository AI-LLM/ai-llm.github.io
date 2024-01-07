1. Refactoring
    1. Inheritance
        1. Forbid overriding: add final to method
        2. Invoke overridden method instead of inherited one
        3. Abstract an existing method using the “abstract” keyword
    2. Methods Interaction
        1. Add parameter & remove variable from method body
        2. Use ? in generics as return type
    3. Readability
        1. Add braces to if statement
        2. Merge variable definition & initialization        3. Add/Remove “this” qualifier        4. Remove redundant initialization        5. Replace generic specification with diamond operator        6. Remove redundant “else” keyword
        7. Replace anonymous class with lambda expression        8. Simplify if condition
        9. Merge 2 catch blocks capturing both exceptions in 1 catch expression
    4. Naming
        1. Rename parameter        2. Rename method        3. Rename variable
    5. Encapsulation
        1. Broad method visibility
        2. Narrow method visibility
2. Bug fix
    1. Exceptions
        1. Remove thrown exception
        2. Add try block
        3. Move existing statements in try block
        4. Move existing statements out of try block
        5. Change exception type in catch clause
    2. Conditional statements
        1. Add null check
        2. Modify if condition
            1. Add/Remove operand from condition
            2. Change comparison operator (e.g., >) in condition            3. Change operands order in if condition
        3. Replace if statement with assert statement
    3. Values
        1. Change method return value
    4. Lock mechanism
        1. Remove synchronized keyword from method
        2. Remove synchronized block
        3. Move synchronized keyword from signature to code block or vice versa
    5. Methods invocation
        1. Change parameters order in method invocation
        2. Change parameter value of invoked method
3. Performance improvement
    1. HighLevelChanges: algorithmic changes that require modifications to the overall code structure. 
        1. Memoize results using Dictionary/ConcurrentDictionary,
        2. Hoist computation/allocation to outer scope (loop, method, class, etc.)
        3. Cache and re-use types like List, Dictionary, StringBuilder, etc. 
        4. Introduce fast-path to avoid unnecessary computation, etc.
    2. Suggesting Different API/Data Structure: language/API specific changes to replace or remove an existing API or data structure usage in favor of a better alternative. 
    3. ImprovingExistingAPI/DataStructureUsage: also language/API specific changes, but suggest modifications to existing usage of an API or data structure when deemed incorrect or sub-optimal.
4. Other
    1. Method signature
        1. Add/Remove parameter        2. Change parameter type        3. Change return type
    2. Type
        1. Remove type casting in method body        2. Remove type casting in method signature        3. Change type of a variable
    3. Replace code
        1. Replace statement        2. Replace invoked method
    4. Initialization
        1. Forbid multiple assignments: add final to variable
    5. Add code        1. Add condition
        2. Add statement
        3. Add invoked method        4. Add parameter in method/constructor invocation
    6. Delete code
        1. Remove if condition
        2. Remove “finally” from try/catch
        3. Remove try/catch
        4. Remove invoked method
        5. Remove statement
        6. Remove parameter from the method invocation
    7. Triggered by other changes
        1. Change qualified name in response to a move class refactoring
        2. Class is not static anymore. Add object instance to invoke its methods
        3. Class becomes static. Delete object instance to invoke its methods
        4. Change method invocation as result of a move method
