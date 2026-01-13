# Store Layout Model

## Overview

This document defines the logical data model for representing retail store layouts and planograms. The model treats planograms as structured data, enabling programmatic access, validation, and analytics.

## Design Principles

### 1. Hierarchical Structure

Store layout follows a natural hierarchy from store to individual product positions:

```
Store
  └── Aisle
      └── Gondola
          └── Module (Left/Right)
              └── Shelf
                  └── Position
                      └── Product Placement
```

### 2. Data-Driven, Not Visual

Planograms are represented as structured data, not static images:
- Queryable and filterable
- Versionable and trackable
- Validatable programmatically
- Integratable with other systems

### 3. Store-Specific Variations

Model supports store-specific adaptations:
- Store constraints (size, layout)
- Local variations
- Format-specific rules
- Regional differences

## Core Entities

### Store

**Definition**: A physical retail location.

**Attributes:**
- `storeId`: Unique identifier
- `name`: Store name
- `address`: Physical address
- `format`: Store format (supermarket, hypermarket, convenience)
- `size`: Store size (square feet/meters)
- `layout`: Store layout type
- `constraints`: Store-specific constraints

**Example:**
```json
{
  "storeId": "STORE-001",
  "name": "Supermarket Downtown",
  "address": "123 Main St, City, State",
  "format": "SUPERMARKET",
  "size": 50000,
  "layout": "STANDARD",
  "constraints": {
    "maxGondolaHeight": 84,
    "aisleWidth": 8,
    "ceilingHeight": 12
  }
}
```

### Aisle

**Definition**: A major walkway in the store.

**Attributes:**
- `aisleId`: Unique identifier
- `storeId`: Parent store
- `number`: Aisle number or name
- `name`: Aisle name (e.g., "Beverages")
- `category`: Primary category
- `length`: Aisle length (feet/meters)
- `width`: Aisle width
- `gondolas`: List of gondolas in aisle

**Example:**
```json
{
  "aisleId": "AISLE-001",
  "storeId": "STORE-001",
  "number": 5,
  "name": "Beverages",
  "category": "BEVERAGES",
  "length": 60,
  "width": 8,
  "gondolas": ["GONDOLA-001", "GONDOLA-002"]
}
```

### Gondola

**Definition**: A freestanding display unit with shelves on both sides.

**Attributes:**
- `gondolaId`: Unique identifier
- `aisleId`: Parent aisle
- `number`: Gondola number within aisle
- `type`: Gondola type (standard, endcap, etc.)
- `width`: Width (typically 4 feet)
- `depth`: Depth
- `height`: Maximum height
- `modules`: Left and right modules

**Example:**
```json
{
  "gondolaId": "GONDOLA-001",
  "aisleId": "AISLE-001",
  "number": 3,
  "type": "STANDARD",
  "width": 48,
  "depth": 24,
  "height": 84,
  "modules": {
    "left": "MODULE-001-L",
    "right": "MODULE-001-R"
  }
}
```

### Module

**Definition**: One side (left or right) of a gondola.

**Attributes:**
- `moduleId`: Unique identifier
- `gondolaId`: Parent gondola
- `side`: Left or right
- `width`: Module width (typically 2 feet)
- `depth`: Shelf depth
- `shelves`: List of shelves

**Example:**
```json
{
  "moduleId": "MODULE-001-L",
  "gondolaId": "GONDOLA-001",
  "side": "LEFT",
  "width": 24,
  "depth": 18,
  "shelves": [
    {"shelfId": "SHELF-001", "level": 1, "height": 12},
    {"shelfId": "SHELF-002", "level": 2, "height": 12},
    {"shelfId": "SHELF-003", "level": 3, "height": 12}
  ]
}
```

### Shelf

**Definition**: A horizontal level within a module.

**Attributes:**
- `shelfId`: Unique identifier
- `moduleId`: Parent module
- `level`: Shelf level (1 = bottom, increasing upward)
- `height`: Shelf height from floor
- `depth`: Shelf depth
- `width`: Shelf width
- `maxWeight`: Maximum weight capacity
- `positions`: List of positions on shelf

**Example:**
```json
{
  "shelfId": "SHELF-003",
  "moduleId": "MODULE-001-L",
  "level": 3,
  "height": 60,
  "depth": 18,
  "width": 24,
  "maxWeight": 500,
  "positions": [
    {"positionId": "POS-001", "index": 1, "x": 0, "width": 6},
    {"positionId": "POS-002", "index": 2, "x": 6, "width": 6}
  ]
}
```

### Position

**Definition**: A specific location on a shelf where a product can be placed.

**Attributes:**
- `positionId`: Unique identifier
- `shelfId`: Parent shelf
- `index`: Position index (left to right)
- `x`: X coordinate (left position in inches/cm)
- `width`: Position width
- `depth`: Position depth
- `productPlacement`: Product placed at this position

**Example:**
```json
{
  "positionId": "POS-001",
  "shelfId": "SHELF-003",
  "index": 1,
  "x": 0,
  "width": 6,
  "depth": 18,
  "productPlacement": {
    "productId": "PROD-001",
    "facings": 3,
    "depth": 2
  }
}
```

### Product Placement

**Definition**: A product placed at a specific position.

**Attributes:**
- `productId`: Product identifier
- `positionId`: Position where placed
- `facings`: Number of facings
- `depth`: Number of units deep
- `startDate`: Placement start date
- `endDate`: Placement end date
- `rules`: Rules applied to this placement

**Example:**
```json
{
  "productId": "PROD-001",
  "positionId": "POS-001",
  "facings": 3,
  "depth": 2,
  "startDate": "2024-01-15",
  "endDate": "2024-03-15",
  "rules": [
    "HIGH_ROTATION_EYE_LEVEL",
    "BRAND_BLOCKING"
  ]
}
```

## Planogram Structure

### Planogram Entity

**Definition**: A complete planogram for a store or category.

**Attributes:**
- `planogramId`: Unique identifier
- `name`: Planogram name
- `storeId`: Store (if store-specific)
- `category`: Category
- `version`: Version number
- `status`: Status (DRAFT, APPROVED, PUBLISHED, ARCHIVED)
- `createdDate`: Creation date
- `approvedDate`: Approval date
- `publishedDate`: Publication date
- `createdBy`: Creator
- `approvedBy`: Approver
- `productPlacements`: List of product placements

**Example:**
```json
{
  "planogramId": "PLANO-001",
  "name": "Beverages Aisle 5 - Q1 2024",
  "storeId": "STORE-001",
  "category": "BEVERAGES",
  "version": 1,
  "status": "PUBLISHED",
  "createdDate": "2024-01-01",
  "approvedDate": "2024-01-05",
  "publishedDate": "2024-01-10",
  "createdBy": "merchandising@retail.com",
  "approvedBy": "operations@retail.com",
  "productPlacements": [
    {
      "productId": "PROD-001",
      "positionId": "POS-001",
      "facings": 3,
      "depth": 2
    }
  ]
}
```

## Relationships

### Store → Aisle → Gondola → Module → Shelf → Position

**Hierarchical Relationship:**
- Each entity has one parent
- Each entity can have multiple children
- Navigation follows hierarchy
- Queries can filter at any level

### Position → Product Placement

**One-to-One Relationship:**
- Each position can have one product placement
- Product placement references position
- Can be empty (no product)

### Planogram → Product Placements

**One-to-Many Relationship:**
- Planogram contains multiple product placements
- Product placements reference positions
- Positions reference store hierarchy

## Store Constraints

### Physical Constraints

**Store-Level:**
- Ceiling height
- Aisle width
- Floor space
- Fire code requirements

**Gondola-Level:**
- Maximum height
- Weight capacity
- Width constraints

**Shelf-Level:**
- Height from floor
- Depth
- Weight capacity
- Visibility requirements

### Business Constraints

**Category Constraints:**
- Category placement rules
- Category adjacency
- Category flow

**Brand Constraints:**
- Brand blocking
- Brand exclusivity
- Brand positioning

**Product Constraints:**
- Product size
- Product weight
- Product rotation
- Product relationships

## Store Variations

### Master Planogram

**Definition**: Template planogram not tied to specific store.

**Characteristics:**
- Generic template
- Category-based
- Used as starting point
- Adapted to stores

### Store-Specific Planogram

**Definition**: Planogram adapted to specific store.

**Characteristics:**
- Based on master planogram
- Adapted to store constraints
- Store-specific variations
- Ready for execution

**Adaptation Process:**
1. Start with master planogram
2. Apply store constraints
3. Adjust for store size
4. Handle local variations
5. Validate against constraints

## Data Model Benefits

### Queryability

**Examples:**
- Find all products in aisle 5
- Find all high-rotation products at eye level
- Find all products in category "Beverages"
- Find all positions for product X

### Versioning

**Capabilities:**
- Track planogram versions
- Compare versions
- Rollback to previous version
- Audit trail of changes

### Validation

**Capabilities:**
- Validate against rules
- Check constraints
- Verify compliance
- Automated validation

### Analytics

**Capabilities:**
- Analyze placement patterns
- Measure compliance
- Optimize placements
- Performance analysis

## Next Steps

- Review `docs/05-product-placement-rules.md` for placement rules
- Check `examples/store-layout-json-example.md` for JSON examples
- Study `examples/planogram-data-model-example.md` for data model details
