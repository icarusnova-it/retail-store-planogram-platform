# Planogram Concepts

## Overview

This document defines the core concepts and terminology used in planogramming for retail stores.

## Core Concepts

### Planogram

**Definition**: A planogram (planograma) is a visual representation and data model of how products should be arranged on store shelves and displays.

**Key Characteristics:**
- **Visual**: Shows product placement visually
- **Data-Driven**: Based on structured data (not just images)
- **Rule-Based**: Placement follows business rules
- **Versionable**: Can be versioned and tracked over time
- **Store-Specific**: Can be adapted to specific stores

**Purpose:**
- Optimize product placement for sales
- Ensure consistent execution across stores
- Facilitate restocking and operations
- Support category management

### Store Hierarchy

The physical structure of a retail store follows a hierarchical model:

```
Store
  └── Aisle (Pasillo)
      └── Gondola (Góndola)
          └── Module (Módulo)
              └── Shelf (Nivel)
                  └── Position (Posición)
                      └── Product (Producto)
```

### Aisle (Pasillo)

**Definition**: A major walkway in a store, typically running from front to back.

**Characteristics:**
- Wide walkway for customer traffic
- Contains multiple gondolas on both sides
- Organized by category or department
- Numbered or named for identification

**Example**: "Aisle 5 - Beverages", "Aisle 12 - Frozen Foods"

### Gondola (Góndola)

**Definition**: A freestanding display unit with shelves on both sides, placed in aisles.

**Characteristics:**
- Double-sided display unit
- Multiple shelves (levels)
- Can be moved and reconfigured
- Standard widths (typically 4 feet)

**Example**: "Gondola A-5-3" (Aisle 5, Gondola 3)

### Module (Módulo)

**Definition**: A section of a gondola, typically one side (left or right) of the gondola.

**Characteristics:**
- One side of a gondola
- Contains multiple shelves
- Can be managed independently
- Standard width (typically 2 feet per module)

**Example**: "Module A-5-3-L" (Aisle 5, Gondola 3, Left side)

### Shelf (Nivel)

**Definition**: A horizontal level within a module where products are placed.

**Characteristics:**
- Horizontal surface for product placement
- Numbered from bottom to top (Level 1 = bottom)
- Height varies by gondola type
- Can have weight and height constraints

**Example**: "Shelf 3" (third shelf from bottom, typically eye level)

**Shelf Levels:**
- **Level 1 (Bottom)**: Heavy products, large packages
- **Level 2-3 (Knee to Waist)**: Standard products
- **Level 4-5 (Eye Level)**: High-rotation products, premium items
- **Level 6+ (Above Eye Level)**: Slow-moving items, large packages

### Position (Posición)

**Definition**: A specific location on a shelf where a product is placed.

**Characteristics:**
- Specific X, Y coordinates on shelf
- Can be measured in inches or centimeters
- Left to right position
- Front to back position (depth)

**Example**: "Position 12" (12th position from left on shelf)

### Facing

**Definition**: The number of product units visible from the front (customer-facing side).

**Characteristics:**
- Count of visible product units
- Affects product visibility and sales
- Can vary by product and category
- Important for high-rotation products

**Example**: "3 facings" means 3 units of the product are visible from the front.

**Facing Rules:**
- **High-Rotation Products**: More facings (3-5)
- **Premium Products**: More facings (2-4)
- **Standard Products**: Standard facings (1-2)
- **Slow-Moving Products**: Fewer facings (1)

### Category and Subcategory

**Definition**: Organizational structure for grouping related products.

**Category Hierarchy:**
```
Category (Categoría)
  └── Subcategory (Subcategoría)
      └── Product Group
          └── Product
```

**Example:**
- **Category**: Beverages
  - **Subcategory**: Soft Drinks
    - **Product Group**: Cola
      - **Product**: Coca-Cola 2L

**Category Management:**
- Products grouped by category
- Category rules apply to all products in category
- Category performance tracked
- Category optimization

## Product Placement Concepts

### Product Positioning

**Definition**: Where a product is placed within a shelf or module.

**Position Factors:**
- **Height**: Eye level preferred for high-rotation
- **Left/Right**: Category flow, brand positioning
- **Front/Back**: Depth placement
- **Adjacency**: Products placed near related items

### Space Allocation

**Definition**: How much space (linear feet or centimeters) is allocated to a product or category.

**Characteristics:**
- Measured in linear units
- Based on sales velocity
- Category importance
- Brand agreements

**Example**: "Coca-Cola allocated 2.5 linear feet on shelf 4"

### Product Rotation

**Definition**: How quickly products sell (sales velocity).

**Rotation Categories:**
- **High Rotation**: Fast-selling products
- **Medium Rotation**: Moderate sales
- **Low Rotation**: Slow-selling products

**Placement Rules:**
- High rotation → Eye level, more facings
- Low rotation → Lower shelves, fewer facings

### Brand Blocking

**Definition**: Grouping products by brand within a category.

**Characteristics:**
- All products of same brand together
- Brand visibility
- Brand agreements
- Customer shopping patterns

**Example**: All Coca-Cola products grouped together in soft drinks section.

### Category Flow

**Definition**: The logical flow of categories within an aisle or store.

**Characteristics:**
- Categories arranged logically
- Customer shopping patterns
- Related categories adjacent
- Natural flow through store

**Example**: Breakfast items (cereals, milk, bread) in same area.

## Constraints and Rules

### Physical Constraints

**Weight Constraints:**
- Heavy products on lower shelves
- Weight limits per shelf
- Safety considerations

**Height Constraints:**
- Product height vs shelf height
- Store ceiling height
- Visibility requirements

**Depth Constraints:**
- Product depth vs shelf depth
- Front-to-back placement
- Safety (products not hanging over edge)

### Business Rules

**Category Rules:**
- Category placement rules
- Subcategory grouping
- Category adjacency

**Brand Rules:**
- Brand blocking requirements
- Brand exclusivity
- Brand positioning

**Product Rules:**
- Product-specific placement
- Rotation-based placement
- Promotional placement

### Compliance Rules

**Regulatory:**
- Age-restricted products (alcohol, tobacco)
- Product placement restrictions
- Safety regulations

**Brand Guidelines:**
- Brand-specific requirements
- Visual merchandising standards
- Promotional requirements

**Store Policies:**
- Store-specific rules
- Regional variations
- Format-specific rules

## Planogram States

### Draft

**Definition**: Planogram being created or modified.

**Characteristics:**
- Not yet approved
- Can be edited
- Not published to stores

### Approved

**Definition**: Planogram approved for publication.

**Characteristics:**
- Approved by authorized person
- Ready for publication
- Cannot be edited (must create new version)

### Published

**Definition**: Planogram published to stores.

**Characteristics:**
- Available in stores
- Can be executed
- Active version

### Archived

**Definition**: Planogram no longer active.

**Characteristics:**
- Replaced by new version
- Historical record
- Can be referenced

## Planogram Types

### Master Planogram

**Definition**: Template planogram for a category or product group.

**Characteristics:**
- Generic template
- Not store-specific
- Used as starting point
- Adapted to stores

### Store Planogram

**Definition**: Store-specific planogram adapted from master.

**Characteristics:**
- Adapted to store constraints
- Store-specific variations
- Ready for execution
- Tied to specific store

## Next Steps

- Read `docs/04-store-layout-model.md` for detailed store modeling
- Review `docs/05-product-placement-rules.md` for placement rules
- Check `examples/planogram-data-model-example.md` for data model examples
