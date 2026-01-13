# Placement Rules Example

## Overview

This document provides concrete examples of product placement rules used in planogram systems.

## Rule Examples

### Example 1: High-Rotation Eye Level Rule

```yaml
Rule:
  ID: HIGH_ROTATION_EYE_LEVEL
  Name: High-Rotation Products at Eye Level
  Category: ROTATION
  Priority: MEDIUM
  Description: High-rotation products should be placed at eye level (shelf 4-5) for maximum visibility and sales
  
  Condition:
    - product.rotation > 50 units/week
    - OR product.rotationCategory == "HIGH"
  
  Action:
    - Place on shelf level 4 or 5
    - Ensure minimum 2 facings
    - Prefer shelf 4 (optimal eye level)
  
  Validation:
    - Check shelf level is 4 or 5
    - Check facings >= 2
    - Verify height from floor is 60-72 inches
  
  Exception:
    - If product weight > 10 lbs, use shelf 2-3 (weight constraint overrides)
    - Exception requires approval
  
  Example:
    Product: Coca-Cola 2L
    Rotation: 150 units/week (HIGH)
    Placement: Shelf 4, Position 1, 3 facings
    Status: ✅ Compliant
```

### Example 2: Brand Blocking Rule

```yaml
Rule:
  ID: BRAND_BLOCKING
  Name: Group Products by Brand
  Category: BRAND
  Priority: MEDIUM
  Description: All products of the same brand should be grouped together within a category
  
  Condition:
    - Products in same category
    - Products have same brand
  
  Action:
    - Group products by brand
    - Place brand blocks together
    - Maintain brand visibility
  
  Validation:
    - Check brand grouping
    - Verify no competing brands between brand blocks
    - Check brand block continuity
  
  Exception:
    - If space constraint prevents grouping, allow mixing
    - Exception requires approval
  
  Example:
    Category: Soft Drinks
    Brands: Coca-Cola, Pepsi, Sprite
    Placement:
      - Coca-Cola products: Positions 1-4
      - Pepsi products: Positions 5-7
      - Sprite products: Positions 8-9
    Status: ✅ Compliant (brands grouped)
```

### Example 3: Weight Constraint Rule

```yaml
Rule:
  ID: WEIGHT_CONSTRAINT
  Name: Shelf Weight Capacity
  Category: PHYSICAL
  Priority: HIGH
  Description: Products must not exceed shelf weight capacity (safety requirement)
  
  Condition:
    - Product weight
    - Shelf weight capacity
    - Total weight on shelf
  
  Action:
    - Ensure product weight <= shelf capacity
    - Ensure total shelf weight <= shelf capacity
    - Heavy products on lower shelves (shelf 1-2)
  
  Validation:
    - Check product weight <= shelf capacity
    - Check total shelf weight <= shelf capacity
    - Verify heavy products on lower shelves
  
  Exception:
    - None (safety requirement, no exceptions allowed)
  
  Example:
    Product: 2L Soda Bottle
    Weight: 4.4 lbs
    Shelf: Shelf 1
    Shelf Capacity: 1000 lbs
    Current Shelf Weight: 450 lbs
    Status: ✅ Compliant (weight within capacity)
```

### Example 4: Category Flow Rule

```yaml
Rule:
  ID: CATEGORY_FLOW
  Name: Logical Category Flow
  Category: CATEGORY
  Priority: MEDIUM
  Description: Categories should flow logically, with related categories adjacent
  
  Condition:
    - Category placement
    - Category relationships
    - Customer shopping patterns
  
  Action:
    - Place related categories adjacent
    - Follow logical flow
    - Optimize customer journey
  
  Validation:
    - Check category adjacency
    - Verify category flow
    - Check customer shopping patterns
  
  Exception:
    - If space constraint prevents optimal flow, document exception
    - Exception requires approval
  
  Example:
    Categories: Cereals, Milk, Bread
    Placement: All in same area (breakfast items)
    Flow: Cereals → Milk → Bread (logical breakfast flow)
    Status: ✅ Compliant
```

### Example 5: Age-Restricted Product Rule

```yaml
Rule:
  ID: AGE_RESTRICTED_PLACEMENT
  Name: Age-Restricted Product Placement
  Category: COMPLIANCE
  Priority: HIGH
  Description: Age-restricted products (alcohol, tobacco) must comply with placement regulations
  
  Condition:
    - Product is age-restricted
    - Regulatory requirements
  
  Action:
    - Place on lower shelves (shelf 1-2)
    - Not at eye level
    - Not near entrance
    - Comply with regulations
  
  Validation:
    - Check shelf level (must be 1-2)
    - Check distance from entrance
    - Verify regulatory compliance
  
  Exception:
    - None (regulatory requirement, no exceptions)
  
  Example:
    Product: Beer 6-pack
    Type: Age-restricted (alcohol)
    Placement: Shelf 1, Position 5 (lower shelf, not near entrance)
    Status: ✅ Compliant (regulatory compliance)
```

## Rule Execution Example

### Rule Execution Flow

```json
{
  "product": {
    "productId": "PROD-001",
    "name": "Coca-Cola 2L",
    "rotation": 150,
    "rotationCategory": "HIGH",
    "weight": 4.4,
    "brand": "Coca-Cola",
    "category": "BEVERAGES"
  },
  "rulesApplied": [
    {
      "ruleId": "HIGH_ROTATION_EYE_LEVEL",
      "status": "APPLIED",
      "compliant": true,
      "result": "Placed on Shelf 4 (eye level)"
    },
    {
      "ruleId": "BRAND_BLOCKING",
      "status": "APPLIED",
      "compliant": true,
      "result": "Grouped with other Coca-Cola products"
    },
    {
      "ruleId": "WEIGHT_CONSTRAINT",
      "status": "APPLIED",
      "compliant": true,
      "result": "Weight within capacity"
    }
  ],
  "placement": {
    "shelfLevel": 4,
    "position": "POS-013",
    "facings": 3,
    "depth": 2
  },
  "validation": {
    "valid": true,
    "violations": [],
    "warnings": []
  }
}
```

## Rule Violation Example

### Violation Scenario

```json
{
  "product": {
    "productId": "PROD-002",
    "name": "Premium Brand Product",
    "rotation": 20,
    "rotationCategory": "LOW"
  },
  "rulesApplied": [
    {
      "ruleId": "HIGH_ROTATION_EYE_LEVEL",
      "status": "VIOLATED",
      "compliant": false,
      "violation": "Low-rotation product placed at eye level",
      "recommendation": "Move to shelf 2-3 (lower shelf)"
    }
  ],
  "placement": {
    "shelfLevel": 4,
    "position": "POS-014"
  },
  "validation": {
    "valid": false,
    "violations": [
      {
        "ruleId": "HIGH_ROTATION_EYE_LEVEL",
        "severity": "MEDIUM",
        "message": "Low-rotation product should not be at eye level",
        "recommendation": "Move to shelf 2-3"
      }
    ]
  }
}
```

## Related Documents

- `docs/05-product-placement-rules.md` - Product placement rules
- `docs/06-constraints-and-compliance.md` - Constraints and compliance
