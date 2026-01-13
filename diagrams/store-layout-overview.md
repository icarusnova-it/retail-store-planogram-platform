# Store Layout Overview

## Overview

This diagram shows the hierarchical structure of a retail store layout, from store level down to individual product positions.

## Mermaid Diagram

```mermaid
graph TB
    subgraph "Store"
        Store[Store: Supermarket Downtown<br/>50,000 sq ft]
    end
    
    subgraph "Aisles"
        Aisle1[Aisle 1: Produce]
        Aisle2[Aisle 2: Meat & Seafood]
        Aisle3[Aisle 3: Dairy]
        Aisle5[Aisle 5: Beverages]
        Aisle10[Aisle 10: Frozen]
    end
    
    subgraph "Gondolas in Aisle 5"
        Gondola1[Gondola 1<br/>Standard 4ft]
        Gondola2[Gondola 2<br/>Standard 4ft]
        Gondola3[Gondola 3<br/>Endcap]
    end
    
    subgraph "Modules in Gondola 1"
        ModuleL[Module Left<br/>2ft width]
        ModuleR[Module Right<br/>2ft width]
    end
    
    subgraph "Shelves in Module Left"
        Shelf1[Shelf 1: Bottom<br/>12" from floor]
        Shelf2[Shelf 2: Knee Level<br/>24" from floor]
        Shelf3[Shelf 3: Waist Level<br/>36" from floor]
        Shelf4[Shelf 4: Eye Level<br/>60" from floor]
        Shelf5[Shelf 5: Above Eye<br/>72" from floor]
    end
    
    subgraph "Positions on Shelf 4"
        Pos1[Position 1<br/>0-6 inches]
        Pos2[Position 2<br/>6-12 inches]
        Pos3[Position 3<br/>12-18 inches]
        Pos4[Position 4<br/>18-24 inches]
    end
    
    subgraph "Product Placement"
        Product1[Product: Coca-Cola 2L<br/>3 facings, 2 deep]
    end
    
    Store --> Aisle1
    Store --> Aisle2
    Store --> Aisle3
    Store --> Aisle5
    Store --> Aisle10
    
    Aisle5 --> Gondola1
    Aisle5 --> Gondola2
    Aisle5 --> Gondola3
    
    Gondola1 --> ModuleL
    Gondola1 --> ModuleR
    
    ModuleL --> Shelf1
    ModuleL --> Shelf2
    ModuleL --> Shelf3
    ModuleL --> Shelf4
    ModuleL --> Shelf5
    
    Shelf4 --> Pos1
    Shelf4 --> Pos2
    Shelf4 --> Pos3
    Shelf4 --> Pos4
    
    Pos1 --> Product1
    
    style Store fill:#e1f5ff
    style Aisle5 fill:#fff4e1
    style Gondola1 fill:#ffe1e1
    style ModuleL fill:#e8f5e9
    style Shelf4 fill:#f3e5f5
    style Pos1 fill:#fff9c4
    style Product1 fill:#ffebee
```

## Hierarchy Description

### Store Level
- **Store**: Physical retail location
- **Attributes**: Name, address, format, size, constraints
- **Contains**: Multiple aisles

### Aisle Level
- **Aisle**: Major walkway in store
- **Attributes**: Number, name, category, dimensions
- **Contains**: Multiple gondolas

### Gondola Level
- **Gondola**: Freestanding display unit
- **Attributes**: Type, dimensions, height
- **Contains**: Left and right modules

### Module Level
- **Module**: One side of gondola
- **Attributes**: Side (left/right), dimensions
- **Contains**: Multiple shelves

### Shelf Level
- **Shelf**: Horizontal level within module
- **Attributes**: Level number, height from floor, dimensions
- **Contains**: Multiple positions

### Position Level
- **Position**: Specific location on shelf
- **Attributes**: Index, coordinates, dimensions
- **Contains**: Product placement

### Product Placement
- **Product Placement**: Product placed at position
- **Attributes**: Product, facings, depth, dates

## Key Relationships

1. **One-to-Many**: Each level contains multiple children
2. **Hierarchical**: Clear parent-child relationships
3. **Navigable**: Can navigate up and down hierarchy
4. **Queryable**: Can query at any level

## Use Cases

- **Store Planning**: Design store layout
- **Planogram Creation**: Create planograms using hierarchy
- **Navigation**: Navigate store structure
- **Queries**: Query products by location
- **Analytics**: Analyze by hierarchy level
