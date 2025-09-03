Basic Conditional Templates
Simple If Statement
IF condition THEN
    // statements when condition is true
END IF
If-Else Statement
IF condition THEN
    // statements when true
ELSE
    // statements when false
END IF
Multi-Branch If-Else Chain
IF primary_condition THEN
    // handle primary case
ELSE IF secondary_condition THEN
    // handle secondary case
ELSE IF tertiary_condition THEN
    // handle tertiary case
ELSE
    // handle all other cases
END IF
Nested Conditionals
IF outer_condition THEN
    IF inner_condition THEN
        // both conditions true
    ELSE
        // outer true, inner false
    END IF
ELSE
    // outer condition false
    IF another_inner_condition THEN
        // outer false, inner true
    END IF
END IF
Advanced Conditional Patterns
Guard Clauses (Early Returns)
METHOD processData(input)
    // Guard clauses - handle edge cases first
    IF input is null THEN
        RETURN error_result
    END IF
    
    IF input.isEmpty() THEN
        RETURN empty_result
    END IF
    
    IF input.isInvalid() THEN
        RETURN invalid_result
    END IF
    
    // Main processing logic here
    RETURN successful_result
END METHOD
Ternary-Style Decision
SET result = (condition) ? value_if_true : value_if_false

// In pseudocode form:
IF condition THEN
    SET result = value_if_true
ELSE
    SET result = value_if_false
END IF
