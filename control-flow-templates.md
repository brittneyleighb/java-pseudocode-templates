# Control Flow Templates

> Navigate program execution with confidence

## Overview

Control flow structures are the traffic management system of your programs. These templates provide proven patterns for directing the flow of execution based on conditions, loops, and decision points.

## Table of Contents
- [Basic Conditional Templates](#basic-conditional-templates)
- [Advanced Conditional Patterns](#advanced-conditional-patterns)
- [Loop Templates](#loop-templates)
- [Advanced Loop Patterns](#advanced-loop-patterns)
- [Switch/Case Templates](#switchcase-templates)
- [Control Flow Combination Patterns](#control-flow-combination-patterns)

---

## Basic Conditional Templates

### Simple If Statement

**Purpose**: Execute code only when a condition is true  
**When to Use**: Simple validation, feature toggles, basic decision making

```
IF condition THEN
    // statements when condition is true
END IF
```

**Example**:
```
IF temperature > 100 THEN
    PRINT "Water is boiling"
END IF
```

---

### If-Else Statement

**Purpose**: Choose between two execution paths  
**When to Use**: Binary decisions, handling success/failure cases

```
IF condition THEN
    // statements when true
ELSE
    // statements when false
END IF
```

**Example**:
```
IF age >= 18 THEN
    PRINT "Eligible to vote"
ELSE
    PRINT "Not eligible to vote"
END IF
```

---

### Multi-Branch If-Else Chain

**Purpose**: Handle multiple related conditions in order  
**When to Use**: Grade calculation, priority-based decisions, categorization

```
IF primary_condition THEN
    // handle primary case
ELSE IF secondary_condition THEN
    // handle secondary case
ELSE IF tertiary_condition THEN
    // handle tertiary case
ELSE
    // handle all other cases
END IF
```

**Example**:
```
IF score >= 90 THEN
    SET grade = "A"
ELSE IF score >= 80 THEN
    SET grade = "B"
ELSE IF score >= 70 THEN
    SET grade = "C"
ELSE
    SET grade = "F"
END IF
```

---

### Nested Conditionals

**Purpose**: Handle complex decision trees with dependent conditions  
**When to Use**: Multi-factor authentication, complex business rules

```
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
```

**Example**:
```
IF user_logged_in THEN
    IF user_has_permission THEN
        DISPLAY sensitive_data
    ELSE
        DISPLAY "Access denied"
    END IF
ELSE
    REDIRECT to_login_page
END IF
```

---

## Advanced Conditional Patterns

### Guard Clauses (Early Returns)

**Purpose**: Handle edge cases and errors early to reduce nesting  
**When to Use**: Input validation, error handling, method entry checks

> [!TIP]
> Guard clauses make your code more readable by handling the "what could go wrong" scenarios upfront

```
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
```

**Example**:
```
METHOD calculateDiscount(customer, order)
    IF customer is null THEN
        RETURN 0
    END IF
    
    IF order.total < 50 THEN
        RETURN 0
    END IF
    
    IF NOT customer.isPremium() THEN
        RETURN order.total * 0.05
    END IF
    
    // Premium customer logic
    RETURN order.total * 0.15
END METHOD
```

---

### Ternary-Style Decision

**Purpose**: Compact conditional assignment  
**When to Use**: Simple value assignment based on condition

```
SET result = (condition) ? value_if_true : value_if_false

// In pseudocode form:
IF condition THEN
    SET result = value_if_true
ELSE
    SET result = value_if_false
END IF
```

**Example**:
```
SET status = (age >= 18) ? "Adult" : "Minor"

// Equivalent to:
IF age >= 18 THEN
    SET status = "Adult"
ELSE
    SET status = "Minor"
END IF
```

---

## Loop Templates

### Basic For Loop (Counter-Controlled)

**Purpose**: Repeat actions a specific number of times  
**When to Use**: Array processing, counting operations, fixed iterations

```
FOR counter FROM start TO end STEP increment DO
    // repeated actions using counter
END FOR
```

**Example**:
```
FOR i FROM 0 TO array.length-1 STEP 1 DO
    PRINT "Element " + i + ": " + array[i]
END FOR
```

---

### Enhanced For Loop (Collection Iteration)

**Purpose**: Process each element in a collection  
**When to Use**: Data processing, validation of all items

```
FOR EACH element IN collection DO
    // process each element
END FOR
```

**With index tracking**:
```
SET index = 0
FOR EACH element IN collection DO
    PROCESS element at index
    INCREMENT index
END FOR
```

**Example**:
```
FOR EACH student IN class_roster DO
    IF student.grade < 60 THEN
        ADD student TO failing_list
    END IF
END FOR
```

---

### While Loop (Condition-Controlled)

**Purpose**: Repeat while a condition remains true  
**When to Use**: Input validation, processing until completion, event loops

```
WHILE condition DO
    // repeated actions
    // must update variables that affect condition
END WHILE
```

**Example**:
```
WHILE input is invalid DO
    PROMPT "Enter a number between 1-100: "
    READ input
    VALIDATE input
END WHILE
```

---

### Do-While Loop (Post-Test)

**Purpose**: Execute at least once, then repeat while condition is true  
**When to Use**: Menu systems, input prompts, game loops

```
DO
    // actions (guaranteed to execute at least once)
    // update condition variables
WHILE condition
```

**Example**:
```
DO
    DISPLAY menu_options
    READ user_choice
    PROCESS user_choice
WHILE user_choice != "quit"
```

---

### Infinite Loop with Break Conditions

**Purpose**: Continuous processing with multiple exit conditions  
**When to Use**: Server loops, real-time systems, event processing

```
LOOP FOREVER
    // continuous processing
    
    IF break_condition THEN
        BREAK  // exit the loop
    END IF
    
    IF continue_condition THEN
        CONTINUE  // skip to next iteration
    END IF
    
    // remaining loop body
END LOOP
```

**Example**:
```
LOOP FOREVER
    READ message FROM network
    
    IF message == "SHUTDOWN" THEN
        BREAK
    END IF
    
    IF message is malformed THEN
        LOG error
        CONTINUE
    END IF
    
    PROCESS message
END LOOP
```

---

## Advanced Loop Patterns

### Nested Loops

**Purpose**: Process multi-dimensional data or perform combinations  
**When to Use**: Matrix operations, searching pairs, generating combinations

```
FOR outer_counter FROM start1 TO end1 DO
    FOR inner_counter FROM start2 TO end2 DO
        // actions using both counters
    END FOR
END FOR
```

**Example - Matrix Processing**:
```
FOR row FROM 0 TO matrix.height-1 DO
    FOR col FROM 0 TO matrix.width-1 DO
        SET matrix[row][col] = row + col
    END FOR
END FOR
```

---

### Loop with Multiple Exit Conditions

**Purpose**: Complex loops with various termination scenarios  
**When to Use**: Search operations, network protocols, retry mechanisms

```
WHILE true DO
    // processing
    
    IF normal_exit_condition THEN
        BREAK
    END IF
    
    IF error_condition THEN
        HANDLE error
        BREAK
    END IF
    
    IF skip_condition THEN
        CONTINUE
    END IF
    
    // main loop body
END WHILE
```

---

### Controlled Loop with Counters

**Purpose**: Limit retry attempts or bounded processing  
**When to Use**: Network retries, user input attempts, resource allocation

```
SET attempts = 0
SET max_attempts = 3
SET success = false

WHILE attempts < max_attempts AND NOT success DO
    TRY operation
    
    IF operation successful THEN
        SET success = true
    ELSE
        INCREMENT attempts
        IF attempts < max_attempts THEN
            WAIT before retry
        END IF
    END IF
END WHILE

IF NOT success THEN
    HANDLE final failure
END IF
```

---

## Switch/Case Templates

### Basic Switch Statement

**Purpose**: Multi-way branch based on a single value  
**When to Use**: Menu handling, state processing, command interpretation

```
SWITCH variable
    CASE value1:
        // actions for value1
        BREAK
    CASE value2:
        // actions for value2
        BREAK
    CASE value3:
        // actions for value3
        BREAK
    DEFAULT:
        // default actions when no cases match
        BREAK
END SWITCH
```

**Example**:
```
SWITCH day_of_week
    CASE "Monday":
        PRINT "Start of work week"
        BREAK
    CASE "Friday":
        PRINT "TGIF!"
        BREAK
    CASE "Saturday":
    CASE "Sunday":
        PRINT "Weekend!"
        BREAK
    DEFAULT:
        PRINT "Regular day"
        BREAK
END SWITCH
```

---

### Switch with Fall-Through Cases

**Purpose**: Group related cases that share common actions  
**When to Use**: Grade grouping, category handling, similar treatments

```
SWITCH grade
    CASE 'A':
    CASE 'B':
        SET performance = "Good"
        BREAK
    CASE 'C':
        SET performance = "Average"
        BREAK
    CASE 'D':
    CASE 'F':
        SET performance = "Poor"
        BREAK
    DEFAULT:
        SET performance = "Invalid Grade"
        BREAK
END SWITCH
```

---

### Switch with Complex Actions

**Purpose**: Handle different cases with substantial logic  
**When to Use**: Command processors, calculators, state machines

```
SWITCH operation_type
    CASE ADD:
        SET result = operand1 + operand2
        LOG "Addition performed"
        BREAK
        
    CASE SUBTRACT:
        SET result = operand1 - operand2
        LOG "Subtraction performed"
        BREAK
        
    CASE MULTIPLY:
        IF operand2 == 0 THEN
            SET result = 0
        ELSE
            SET result = operand1 * operand2
        END IF
        LOG "Multiplication performed"
        BREAK
        
    DEFAULT:
        THROW UnsupportedOperationException
        BREAK
END SWITCH
```

---

## Control Flow Combination Patterns

### State Machine Pattern

**Purpose**: Manage complex state transitions and behaviors  
**When to Use**: Game development, workflow systems, protocol handling

```
SET current_state = INITIAL_STATE

WHILE current_state != FINAL_STATE DO
    SWITCH current_state
        CASE STATE_A:
            PERFORM actions for state A
            IF condition_for_B THEN
                SET current_state = STATE_B
            ELSE IF condition_for_C THEN
                SET current_state = STATE_C
            END IF
            BREAK
            
        CASE STATE_B:
            PERFORM actions for state B
            IF condition_for_final THEN
                SET current_state = FINAL_STATE
            ELSE IF condition_for_A THEN
                SET current_state = STATE_A
            END IF
            BREAK
            
        DEFAULT:
            HANDLE unexpected state
            SET current_state = INITIAL_STATE
            BREAK
    END SWITCH
END WHILE
```

---

### Search with Early Termination

**Purpose**: Find item and stop processing immediately  
**When to Use**: Linear search, validation checks, first-match scenarios

```
SET found = false
SET result = null

FOR i FROM 0 TO collection.size-1 DO
    IF collection[i] matches search_criteria THEN
        SET result = collection[i]
        SET found = true
        BREAK  // early termination
    END IF
END FOR

IF found THEN
    PROCESS result
ELSE
    HANDLE not found case
END IF
```

---

### Input Validation Loop

**Purpose**: Ensure valid input before proceeding  
**When to Use**: User interfaces, data entry, configuration setup

```
SET valid_input = false
SET input = null

WHILE NOT valid_input DO
    PROMPT "Enter value: "
    READ input
    
    IF input is null OR input.isEmpty() THEN
        PRINT "Input cannot be empty"
        CONTINUE
    END IF
    
    IF input does not match expected format THEN
        PRINT "Invalid format. Please try again."
        CONTINUE
    END IF
    
    IF input is out of range THEN
        PRINT "Value out of range"
        CONTINUE
    END IF
    
    SET valid_input = true
END WHILE

PROCESS input
```

---

## Best Practices

> [!IMPORTANT]
> Keep these principles in mind when using control flow patterns:

**For Conditionals:**
- Use guard clauses to reduce nesting
- Keep conditions readable and simple
- Avoid deeply nested if statements (max 3-4 levels)

**For Loops:**
- Always ensure loop termination conditions
- Be careful with loop variable modifications
- Consider performance for nested loops

**For Switch Statements:**
- Always include a DEFAULT case
- Don't forget BREAK statements
- Group related cases using fall-through

**General Guidelines:**
- Prefer early returns over deep nesting
- Use meaningful variable names for conditions
- Comment complex control flow logic
- Test edge cases and boundary conditions

---

## Quick Navigation
[⬆️ Back to top](#control-flow-templates) | [🏠 Home](../README.md) | [➡️ Next: Data Structures](../data-structures/README.md)
