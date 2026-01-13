# Product Placement Flow

## Overview

This diagram shows the flow of product placement, including rule application, validation, and exception handling.

## Mermaid Diagram

```mermaid
flowchart TD
    Start([Product to Place]) --> LoadRules[Load Placement Rules]
    LoadRules --> CheckRules{Apply Rules}
    
    CheckRules --> HeightRule[Height-Based Rule]
    CheckRules --> RotationRule[Rotation-Based Rule]
    CheckRules --> CategoryRule[Category Rule]
    CheckRules --> BrandRule[Brand Rule]
    CheckRules --> ConstraintRule[Constraint Rule]
    
    HeightRule --> ValidateHeight{Height<br/>Valid?}
    RotationRule --> ValidateRotation{Rotation<br/>Valid?}
    CategoryRule --> ValidateCategory{Category<br/>Valid?}
    BrandRule --> ValidateBrand{Brand<br/>Valid?}
    ConstraintRule --> ValidateConstraint{Constraint<br/>Valid?}
    
    ValidateHeight -->|Invalid| HeightException[Height Exception]
    ValidateRotation -->|Invalid| RotationException[Rotation Exception]
    ValidateCategory -->|Invalid| CategoryException[Category Exception]
    ValidateBrand -->|Invalid| BrandException[Brand Exception]
    ValidateConstraint -->|Invalid| ConstraintException[Constraint Exception]
    
    ValidateHeight -->|Valid| CheckAll{All Rules<br/>Valid?}
    ValidateRotation -->|Valid| CheckAll
    ValidateCategory -->|Valid| CheckAll
    ValidateBrand -->|Valid| CheckAll
    ValidateConstraint -->|Valid| CheckAll
    
    HeightException --> RequestApproval{Request<br/>Approval?}
    RotationException --> RequestApproval
    CategoryException --> RequestApproval
    BrandException --> RequestApproval
    ConstraintException --> RequestApproval
    
    RequestApproval -->|Yes| Approval[Submit for Approval]
    RequestApproval -->|No| Reject[Reject Placement]
    
    Approval --> ApprovalCheck{Approved?}
    ApprovalCheck -->|Yes| CheckAll
    ApprovalCheck -->|No| Reject
    
    CheckAll -->|All Valid| PlaceProduct[Place Product]
    CheckAll -->|Some Invalid| CollectExceptions[Collect Exceptions]
    
    CollectExceptions --> CriticalCheck{Critical<br/>Exceptions?}
    CriticalCheck -->|Yes| Reject
    CriticalCheck -->|No| RequestApproval
    
    PlaceProduct --> ValidatePlacement[Validate Placement]
    ValidatePlacement --> PlacementCheck{Placement<br/>Valid?}
    
    PlacementCheck -->|Invalid| PlacementException[Placement Exception]
    PlacementCheck -->|Valid| Complete[Placement Complete]
    
    PlacementException --> RequestApproval
    
    Reject --> End([End - Rejected])
    Complete --> End([End - Placed])
    
    style CheckRules fill:#fff4e1
    style ValidateHeight fill:#ffe1e1
    style ValidateRotation fill:#ffe1e1
    style ValidateCategory fill:#ffe1e1
    style ValidateBrand fill:#ffe1e1
    style ValidateConstraint fill:#ffe1e1
    style RequestApproval fill:#e1f5ff
    style ApprovalCheck fill:#e1f5ff
    style PlaceProduct fill:#e8f5e9
    style Complete fill:#e8f5e9
```

## Flow Description

### 1. Rule Loading

**Process:**
- Load all applicable placement rules
- Rules include: height, rotation, category, brand, constraints
- Rules prioritized by importance

### 2. Rule Application

**Rules Applied:**
- **Height Rule**: Check height-based placement
- **Rotation Rule**: Check rotation-based placement
- **Category Rule**: Check category rules
- **Brand Rule**: Check brand rules
- **Constraint Rule**: Check physical constraints

### 3. Rule Validation

**Validation:**
- Each rule validated
- Rule compliance checked
- Violations identified
- Exceptions collected

### 4. Exception Handling

**Exception Types:**
- **Height Exception**: Height rule violation
- **Rotation Exception**: Rotation rule violation
- **Category Exception**: Category rule violation
- **Brand Exception**: Brand rule violation
- **Constraint Exception**: Constraint violation

**Exception Process:**
- Identify exception
- Classify severity
- Request approval if needed
- Handle exception

### 5. Approval Process

**Approval:**
- Exception submitted for approval
- Authorized person reviews
- Approve or reject
- If approved, proceed with placement

### 6. Product Placement

**Placement:**
- Product placed at position
- Placement validated
- If valid, placement complete
- If invalid, exception handling

### 7. Completion

**Completion:**
- Placement validated
- Product placed successfully
- Placement recorded
- Planogram updated

## Key Decision Points

1. **Rule Validation**: All rules must be valid
2. **Exception Approval**: Exceptions require approval
3. **Placement Validation**: Placement must be valid
4. **Critical Exceptions**: Critical exceptions reject placement

## Best Practices

1. **Comprehensive Rules**: All rules applied
2. **Systematic Validation**: Validate all rules
3. **Exception Management**: Systematic exception handling
4. **Approval Process**: Clear approval process
5. **Validation**: Validate placement before completion
