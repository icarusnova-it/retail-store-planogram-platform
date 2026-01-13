# ADR 0003: Store-Specific Variants

## Status
Accepted

## Context

Retail chains operate multiple stores with different characteristics:
- Different store sizes
- Different layouts
- Different constraints (ceiling height, aisle width)
- Different formats (supermarket, hypermarket, convenience)
- Regional variations

The question arises: should planograms be generic (one-size-fits-all) or store-specific (adapted to each store)?

## Decision

We will support **store-specific planogram variants** that are adapted from master planograms to fit each store's unique characteristics, constraints, and requirements.

## Rationale

### 1. Store Diversity

**Reality:**
- Stores have different sizes (20,000 - 100,000 sq ft)
- Different layouts (standard, custom)
- Different constraints (ceiling height, aisle width)
- Different formats (supermarket, hypermarket, convenience)

**Generic Approach:**
- Same planogram for all stores
- Doesn't fit store characteristics
- Execution issues
- Poor performance

**Store-Specific Approach:**
- Planogram adapted to each store
- Fits store characteristics
- Better execution
- Better performance

**Example**: Store A (small, 8-foot ceiling) vs Store B (large, 12-foot ceiling)
- **Generic**: Same planogram, doesn't fit either well
- **Store-Specific**: Adapted to each store, fits perfectly

### 2. Constraint Management

**Store Constraints:**
- Physical constraints (ceiling height, aisle width)
- Space constraints (store size)
- Format constraints (format type)
- Regional constraints (regulations, preferences)

**Store-Specific Approach:**
- Constraints defined per store
- Planogram adapted to constraints
- Constraint validation
- Compliance ensured

**Example**: Store with 8-foot ceiling
- **Generic**: Planogram assumes 12-foot ceiling, doesn't fit
- **Store-Specific**: Adapted to 8-foot ceiling, fits perfectly

### 3. Execution Quality

**Store-Specific Approach:**
- Planogram fits store
- Easier to execute
- Better compliance
- Higher quality execution

**Generic Approach:**
- Planogram doesn't fit
- Difficult to execute
- Poor compliance
- Lower quality execution

**Example**: Planogram execution
- **Store-Specific**: Fits store, easy to execute, high compliance
- **Generic**: Doesn't fit, difficult to execute, low compliance

### 4. Performance Optimization

**Store-Specific Approach:**
- Optimized for each store
- Better sales performance
- Space optimization
- Performance gains

**Generic Approach:**
- Not optimized
- Suboptimal performance
- Wasted space
- Missed opportunities

**Example**: Sales performance
- **Store-Specific**: Optimized per store, better sales
- **Generic**: Not optimized, lower sales

### 5. Master Planogram Benefits

**Master Planogram:**
- Template for category/product group
- Not store-specific
- Used as starting point
- Adapted to stores

**Benefits:**
- Consistency in approach
- Efficiency in creation
- Standardization
- Easy updates

**Example**: Master planogram for "Beverages"
- Created once
- Adapted to 100 stores
- Consistent approach
- Easy to update

## Implementation

### Master Planogram

**Definition:**
- Template planogram
- Category or product group based
- Not tied to specific store
- Used as starting point

**Characteristics:**
- Generic layout
- Standard rules
- Category-based
- Versionable

### Store-Specific Planogram

**Definition:**
- Planogram adapted from master
- Tied to specific store
- Adapted to store constraints
- Ready for execution

**Adaptation Process:**
1. Start with master planogram
2. Load store constraints
3. Apply store constraints
4. Adapt layout to store
5. Validate against constraints
6. Generate store-specific planogram

### Constraint Management

**Store Constraints:**
- Physical constraints (ceiling, aisle width)
- Space constraints (store size)
- Format constraints (format type)
- Regional constraints

**Constraint Application:**
- Constraints defined per store
- Constraints applied during adaptation
- Constraint validation
- Exception handling

## Consequences

### Positive

✅ **Better Fit**: Planograms fit store characteristics
✅ **Better Execution**: Easier execution, higher compliance
✅ **Better Performance**: Optimized per store, better sales
✅ **Constraint Management**: Systematic constraint handling
✅ **Master Benefits**: Consistency and efficiency

### Negative

❌ **Complexity**: More complex than generic
❌ **Maintenance**: More planograms to maintain
❌ **Adaptation Process**: Need adaptation process
❌ **Validation**: Need to validate adaptations

### Mitigations

- **Automated Adaptation**: Automate adaptation process
- **Template System**: Use master planograms as templates
- **Validation Tools**: Automated validation
- **Management Tools**: Tools for managing variants

## Alternatives Considered

### 1. Generic Planograms

**Rejected because:**
- Doesn't fit store diversity
- Poor execution
- Suboptimal performance
- Constraint issues

### 2. Fully Custom Planograms

**Rejected because:**
- Too much work
- No consistency
- Difficult to maintain
- No efficiency

### 3. Master with Store Adaptations

**Accepted:**
- Best of both worlds
- Consistency from master
- Fit from adaptations
- Efficient process

## Related Decisions

- ADR 0001: Planogram as Data
- ADR 0002: Rule-Driven Placement
- ADR 0004: Auditability Required

## References

- `docs/04-store-layout-model.md` - Store layout model
- `docs/06-constraints-and-compliance.md` - Constraints and compliance
