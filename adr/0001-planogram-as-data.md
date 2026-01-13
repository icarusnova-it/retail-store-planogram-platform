# ADR 0001: Planogram as Data

## Status
Accepted

## Context

Planograms in retail have traditionally been created as static documents (PDFs, images, drawings) that represent a snapshot of product placement. This approach has limitations:
- Cannot be queried or analyzed programmatically
- Difficult to version and track changes
- No integration with other systems
- Manual updates required
- Limited automation capabilities

The question arises: should planograms be treated as static visual artifacts or as structured, versionable data?

## Decision

We will treat **planograms as structured data**, not static images. Planograms will be represented as versionable, queryable data structures that can be programmatically accessed, validated, and integrated.

## Rationale

### 1. Queryability and Analysis

**Data-Driven Approach:**
- Planograms stored as structured data (JSON, database)
- Can be queried: "Find all products in aisle 5"
- Can be filtered: "Show all high-rotation products at eye level"
- Can be analyzed programmatically

**Static Approach:**
- Planograms as images/PDFs
- Cannot query or filter
- Manual analysis only
- Limited insights

**Example**: Need to find all products in "Beverages" category
- **Data-Driven**: Query database, get results instantly
- **Static**: Manually search through PDF/image

### 2. Version Control and Tracking

**Data-Driven Approach:**
- Planograms versioned like code
- Track all changes over time
- Compare versions
- Rollback capabilities
- Complete audit trail

**Static Approach:**
- Version control difficult
- Changes require recreating entire document
- Limited tracking
- No rollback

**Example**: Planogram changed, need to see what changed
- **Data-Driven**: Compare versions, see exact changes
- **Static**: Compare two PDFs manually

### 3. Integration Capabilities

**Data-Driven Approach:**
- APIs for integration
- Real-time updates
- Integration with POS, inventory, analytics
- Automated processes

**Static Approach:**
- No programmatic access
- Manual data entry
- Limited integration
- No automation

**Example**: Update inventory system when planogram changes
- **Data-Driven**: Automated integration, real-time updates
- **Static**: Manual update required

### 4. Automated Validation

**Data-Driven Approach:**
- Automated rule validation
- Constraint checking
- Compliance validation
- Real-time validation

**Static Approach:**
- Manual validation
- Error-prone
- Time-consuming
- Inconsistent

**Example**: Validate planogram against business rules
- **Data-Driven**: Automated validation, instant results
- **Static**: Manual review, time-consuming

### 5. Analytics and Optimization

**Data-Driven Approach:**
- Performance analytics
- Sales impact analysis
- Optimization algorithms
- Data-driven decisions

**Static Approach:**
- Limited analytics
- Manual analysis
- No optimization
- Intuition-based decisions

**Example**: Analyze planogram performance
- **Data-Driven**: Automated analytics, insights, optimization
- **Static**: Manual analysis, limited insights

### 6. Store Execution

**Data-Driven Approach:**
- Digital planograms on mobile devices
- Interactive execution guides
- Real-time validation
- Photo evidence linked to data

**Static Approach:**
- Printed planograms
- Manual execution
- No real-time validation
- Photos not linked to data

**Example**: Store manager executes planogram
- **Data-Driven**: Digital guide on tablet, step-by-step, real-time validation
- **Static**: Printed planogram, manual execution

## Implementation

### Data Model

**Structured Representation:**
- Store hierarchy (Store → Aisle → Gondola → Module → Shelf → Position)
- Product placements (Product, Position, Facings, Depth)
- Planogram metadata (Version, Status, Dates, Approvals)
- Rules and constraints

**Format:**
- JSON for API and mobile
- Database for storage
- APIs for access

### Versioning

**Version Control:**
- Each planogram versioned
- Track all changes
- Compare versions
- Rollback capability

### APIs

**Programmatic Access:**
- RESTful APIs
- Query capabilities
- Filter and search
- Real-time updates

## Consequences

### Positive

✅ **Queryability**: Can query and filter planograms
✅ **Version Control**: Proper versioning and tracking
✅ **Integration**: Easy integration with other systems
✅ **Automation**: Automated validation and processes
✅ **Analytics**: Programmatic analytics and optimization
✅ **Mobile Execution**: Digital execution on mobile devices

### Negative

❌ **Complexity**: More complex than static images
❌ **Learning Curve**: Team needs to understand data model
❌ **Migration**: Need to migrate from static to data-driven

### Mitigations

- **Visualization**: Provide visual representation of data
- **Tools**: User-friendly tools for working with data
- **Migration**: Gradual migration path
- **Training**: Training on data model and tools

## Alternatives Considered

### 1. Static Images with Metadata

**Rejected because:**
- Still cannot query images
- Limited integration
- No automated validation
- Manual processes remain

### 2. Hybrid Approach

**Considered:**
- Data-driven with visual rendering
- Best of both worlds
- **Accepted**: This is our approach - data-driven with visual representation

## Related Decisions

- ADR 0002: Rule-Driven Placement
- ADR 0003: Store-Specific Variants
- ADR 0004: Auditability Required

## References

- `docs/04-store-layout-model.md` - Store layout data model
- `examples/planogram-data-model-example.md` - Data model examples
