# ADR 0002: Rule-Driven Placement

## Status
Accepted

## Context

Product placement in planograms has traditionally been done manually by designers who apply business rules and best practices based on experience and intuition. This approach has limitations:
- Inconsistent application of rules
- Time-consuming manual placement
- Difficult to scale to many stores
- Rules not codified or automated
- Limited validation

The question arises: should product placement be manual (designer-driven) or automated (rule-driven)?

## Decision

We will use a **rule-driven approach** for product placement, where business rules are codified and automated, enabling consistent, scalable, and validated placement.

## Rationale

### 1. Consistency

**Rule-Driven Approach:**
- Rules applied consistently across all planograms
- Same rules, same results
- No human variation
- Standardized placement

**Manual Approach:**
- Rules applied inconsistently
- Different designers, different results
- Human variation
- Inconsistent placement

**Example**: Rule "high-rotation products at eye level"
- **Rule-Driven**: Always applied consistently
- **Manual**: Applied sometimes, inconsistently

### 2. Scalability

**Rule-Driven Approach:**
- Automated placement
- Scales to many stores
- Fast placement
- Efficient process

**Manual Approach:**
- Manual placement for each store
- Doesn't scale
- Time-consuming
- Inefficient

**Example**: Create planogram for 100 stores
- **Rule-Driven**: Automated, fast, consistent
- **Manual**: 100 manual placements, time-consuming, inconsistent

### 3. Validation

**Rule-Driven Approach:**
- Automated rule validation
- Real-time validation
- Comprehensive checking
- Consistent validation

**Manual Approach:**
- Manual validation
- Error-prone
- Time-consuming
- Inconsistent

**Example**: Validate planogram against rules
- **Rule-Driven**: Automated, instant, comprehensive
- **Manual**: Manual review, time-consuming, may miss issues

### 4. Rule Management

**Rule-Driven Approach:**
- Rules codified and managed
- Rules versioned
- Rules testable
- Rules documented

**Manual Approach:**
- Rules in people's heads
- Not documented
- Not testable
- Not versioned

**Example**: Update placement rule
- **Rule-Driven**: Update rule code, test, deploy, all planograms updated
- **Manual**: Tell all designers, hope they remember, inconsistent application

### 5. Exception Handling

**Rule-Driven Approach:**
- Systematic exception handling
- Exception approval process
- Exception tracking
- Exception documentation

**Manual Approach:**
- Ad-hoc exceptions
- No approval process
- Not tracked
- Not documented

**Example**: Exception to rule needed
- **Rule-Driven**: Submit exception, approval process, tracked, documented
- **Manual**: Designer decides, no tracking, no documentation

### 6. Optimization

**Rule-Driven Approach:**
- Rules can be optimized based on data
- Test rule variations
- Measure rule impact
- Optimize rules

**Manual Approach:**
- Rules not optimized
- No testing
- No measurement
- Intuition-based

**Example**: Optimize placement rules
- **Rule-Driven**: Test variations, measure impact, optimize based on data
- **Manual**: Guess, hope it works

## Implementation

### Rule Engine

**Components:**
- Rule repository (store rules)
- Rule executor (execute rules)
- Rule validator (validate compliance)
- Exception handler (handle exceptions)

### Rule Types

**Categories:**
- Height-based rules
- Rotation-based rules
- Category rules
- Brand rules
- Physical constraints
- Compliance rules
- Store-specific rules

### Rule Definition

**Format:**
- Rules defined in code or configuration
- Versioned
- Testable
- Documented

## Consequences

### Positive

✅ **Consistency**: Consistent rule application
✅ **Scalability**: Scales to many stores
✅ **Validation**: Automated validation
✅ **Rule Management**: Systematic rule management
✅ **Exception Handling**: Systematic exception handling
✅ **Optimization**: Data-driven optimization

### Negative

❌ **Complexity**: More complex than manual
❌ **Rule Definition**: Need to codify all rules
❌ **Exception Management**: Need exception process
❌ **Learning Curve**: Team needs to understand rules

### Mitigations

- **Visual Editor**: User-friendly rule definition
- **Rule Templates**: Pre-defined rule templates
- **Exception Tools**: Tools for exception management
- **Training**: Training on rule system

## Alternatives Considered

### 1. Pure Manual Placement

**Rejected because:**
- Inconsistent
- Doesn't scale
- No validation
- No optimization

### 2. Hybrid Approach

**Considered:**
- Rule-driven with manual override
- Best of both worlds
- **Accepted**: This is our approach - rule-driven with manual override capability

## Related Decisions

- ADR 0001: Planogram as Data
- ADR 0003: Store-Specific Variants
- ADR 0004: Auditability Required

## References

- `docs/05-product-placement-rules.md` - Product placement rules
- `examples/placement-rules-example.md` - Rule examples
