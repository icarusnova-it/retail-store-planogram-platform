# Product Placement Rules

## Overview

This document defines the rules and constraints that govern product placement in planograms. Rules are codified and automated to ensure consistent, optimal placement across stores.

## Rule Categories

### 1. Height-Based Rules

**Purpose**: Optimize product placement based on shelf height and customer visibility.

#### Eye-Level Rule

**Rule**: High-rotation and premium products should be placed at eye level (typically shelf 4-5).

**Implementation:**
- Identify high-rotation products
- Identify premium products
- Place on shelves 4-5 (eye level)
- Validate placement

**Example**: Coca-Cola (high rotation) → Shelf 4-5, not shelf 1-2.

#### Weight-Based Height Rule

**Rule**: Heavy products must be on lower shelves (shelf 1-2).

**Implementation:**
- Check product weight
- If weight > threshold → lower shelves
- Validate weight capacity
- Safety consideration

**Example**: 2L soda bottles (heavy) → Shelf 1-2, not shelf 4-5.

#### Category Height Rules

**Rule**: Certain categories have preferred height ranges.

**Implementation:**
- Category-specific height rules
- Apply to all products in category
- Override for specific products if needed

**Examples:**
- **Candy**: Eye level (shelf 4-5) - impulse purchase
- **Cereal**: Waist to eye level (shelf 3-5) - family products
- **Cleaning Products**: Lower shelves (shelf 1-3) - heavy, less frequent purchase

### 2. Rotation-Based Rules

**Purpose**: Place products based on sales velocity (rotation).

#### High-Rotation Placement

**Rule**: High-rotation products get premium placement (eye level, more facings).

**Implementation:**
- Calculate product rotation (sales velocity)
- Classify as high/medium/low rotation
- Apply placement rules based on rotation
- More facings for high rotation

**Example**: Product with 100 units/week rotation → Eye level, 4 facings.

#### Low-Rotation Placement

**Rule**: Low-rotation products on lower shelves, fewer facings.

**Implementation:**
- Identify low-rotation products
- Place on lower shelves (shelf 1-3)
- Reduce facings (1-2 facings)
- Optimize space

**Example**: Product with 5 units/week rotation → Shelf 2, 1 facing.

### 3. Category Rules

**Purpose**: Organize products by category and subcategory.

#### Category Grouping

**Rule**: Products of same category should be grouped together.

**Implementation:**
- Group products by category
- Place category blocks together
- Maintain category flow
- Validate category adjacency

**Example**: All soft drinks together, all juices together, all waters together.

#### Subcategory Grouping

**Rule**: Products of same subcategory should be grouped within category.

**Implementation:**
- Group by subcategory within category
- Maintain subcategory blocks
- Logical subcategory flow

**Example**: Within beverages: colas, lemon-limes, root beers grouped separately.

#### Category Flow

**Rule**: Categories should flow logically (related categories adjacent).

**Implementation:**
- Define category relationships
- Place related categories adjacent
- Follow customer shopping patterns
- Validate category flow

**Example**: Breakfast items (cereals, milk, bread) in same area.

### 4. Brand Rules

**Purpose**: Manage brand placement and visibility.

#### Brand Blocking

**Rule**: All products of same brand should be grouped together.

**Implementation:**
- Group products by brand
- Create brand blocks
- Maintain brand visibility
- Validate brand blocking

**Example**: All Coca-Cola products (Coke, Diet Coke, Sprite) grouped together.

#### Brand Exclusivity

**Rule**: Certain brands may have exclusivity requirements.

**Implementation:**
- Check brand exclusivity rules
- Ensure exclusivity compliance
- Handle exceptions
- Validate exclusivity

**Example**: Premium brand requires exclusive placement, no competing brands adjacent.

#### Brand Positioning

**Rule**: Brand positioning within category (leading brands first).

**Implementation:**
- Identify leading brands
- Place leading brands first (left side)
- Follow brand hierarchy
- Validate positioning

**Example**: Leading brand (Coca-Cola) first, then other brands.

### 5. Physical Constraints

**Purpose**: Ensure products fit physically and safely.

#### Weight Constraints

**Rule**: Products must not exceed shelf weight capacity.

**Implementation:**
- Check product weight
- Check shelf weight capacity
- Validate total weight on shelf
- Prevent overloading

**Example**: Shelf capacity 500 lbs, products total 450 lbs → Valid.

#### Height Constraints

**Rule**: Products must fit within shelf height.

**Implementation:**
- Check product height
- Check shelf height
- Validate fit
- Handle overhanging products

**Example**: Product height 10 inches, shelf height 12 inches → Valid.

#### Depth Constraints

**Rule**: Products must not hang over shelf edge.

**Implementation:**
- Check product depth
- Check shelf depth
- Validate fit
- Safety consideration

**Example**: Product depth 16 inches, shelf depth 18 inches → Valid.

### 6. Compliance Rules

**Purpose**: Ensure regulatory and policy compliance.

#### Age-Restricted Products

**Rule**: Age-restricted products (alcohol, tobacco) have placement restrictions.

**Implementation:**
- Identify age-restricted products
- Apply placement restrictions
- Validate compliance
- Regulatory requirement

**Example**: Alcohol products not at eye level, not near entrance.

#### Regulatory Compliance

**Rule**: Products must comply with regulatory placement requirements.

**Implementation:**
- Check regulatory requirements
- Apply placement rules
- Validate compliance
- Handle violations

**Example**: Certain products require specific placement per regulations.

#### Brand Guidelines

**Rule**: Products must comply with brand placement guidelines.

**Implementation:**
- Check brand guidelines
- Apply brand rules
- Validate compliance
- Handle violations

**Example**: Brand requires minimum facings, specific height.

### 7. Store-Specific Rules

**Purpose**: Handle store-specific constraints and variations.

#### Store Size Constraints

**Rule**: Adapt planogram to store size.

**Implementation:**
- Check store size
- Adjust planogram accordingly
- Handle size constraints
- Validate fit

**Example**: Small store → Fewer gondolas, condensed layout.

#### Store Format Rules

**Rule**: Different formats (supermarket, hypermarket, convenience) have different rules.

**Implementation:**
- Identify store format
- Apply format-specific rules
- Handle format variations
- Validate format compliance

**Example**: Convenience store → Different layout, fewer products.

#### Regional Variations

**Rule**: Regional preferences and regulations affect placement.

**Implementation:**
- Check regional rules
- Apply regional variations
- Handle regional preferences
- Validate regional compliance

**Example**: Regional preference for local brands, regional regulations.

## Rule Engine

### Rule Definition

**Structure:**
```yaml
Rule:
  ID: RULE_ID
  Name: Rule Name
  Category: HEIGHT | ROTATION | CATEGORY | BRAND | PHYSICAL | COMPLIANCE | STORE
  Priority: HIGH | MEDIUM | LOW
  Condition: Condition to check
  Action: Action to take
  Validation: Validation logic
  Exception: Exception handling
```

### Rule Execution

**Process:**
1. Load rules for planogram
2. Evaluate conditions
3. Apply rules
4. Validate results
5. Handle exceptions
6. Generate report

### Rule Priority

**Priority Levels:**
- **HIGH**: Must comply (regulatory, safety)
- **MEDIUM**: Should comply (business rules)
- **LOW**: Nice to have (optimization)

**Conflict Resolution:**
- Higher priority rules override lower priority
- Exceptions documented
- Approval required for exceptions

### Rule Validation

**Validation Process:**
1. Check rule conditions
2. Validate rule compliance
3. Identify violations
4. Report violations
5. Require approval for exceptions

## Exception Handling

### Exception Types

**Regulatory Exceptions:**
- Regulatory requirements override business rules
- Documented and approved
- Compliance maintained

**Business Exceptions:**
- Business reasons for exceptions
- Approved by authorized person
- Documented and tracked

**Technical Exceptions:**
- Technical constraints prevent rule compliance
- Documented and approved
- Alternative solutions

### Exception Process

1. **Identify Exception**: Rule cannot be complied with
2. **Document Reason**: Why exception needed
3. **Request Approval**: Submit for approval
4. **Approve/Reject**: Authorized person decides
5. **Track Exception**: Exception tracked and reported

## Rule Examples

### Example 1: High-Rotation Eye Level

```yaml
Rule:
  ID: HIGH_ROTATION_EYE_LEVEL
  Name: High-Rotation Products at Eye Level
  Category: ROTATION
  Priority: MEDIUM
  Condition: product.rotation > 50 units/week
  Action: Place on shelf 4 or 5
  Validation: Check shelf level is 4 or 5
  Exception: If weight > 10 lbs, use shelf 2-3
```

### Example 2: Brand Blocking

```yaml
Rule:
  ID: BRAND_BLOCKING
  Name: Group Products by Brand
  Category: BRAND
  Priority: MEDIUM
  Condition: Products in same category
  Action: Group products by brand
  Validation: Check brand grouping
  Exception: If space constraint, allow mixing
```

### Example 3: Weight Constraint

```yaml
Rule:
  ID: WEIGHT_CONSTRAINT
  Name: Shelf Weight Capacity
  Category: PHYSICAL
  Priority: HIGH
  Condition: Shelf total weight
  Action: Ensure total weight <= shelf capacity
  Validation: Check weight <= capacity
  Exception: None (safety requirement)
```

## Best Practices

1. **Codify Rules**: All rules codified and automated
2. **Priority Management**: Clear priority levels
3. **Exception Handling**: Systematic exception process
4. **Validation**: Automated validation
5. **Documentation**: Rules well-documented
6. **Testing**: Rules tested thoroughly
7. **Monitoring**: Rule compliance monitored

## Next Steps

- Review `docs/06-constraints-and-compliance.md` for detailed constraints
- Check `examples/placement-rules-example.md` for rule examples
- Study `docs/08-analytics-and-optimization.md` for optimization
