# Planogram Data Model Example

## Overview

This document provides concrete examples of the planogram data model, showing how store layouts and product placements are represented as structured data.

## Complete Store Layout Example

### Store Structure

```json
{
  "store": {
    "storeId": "STORE-001",
    "name": "Supermarket Downtown",
    "address": "123 Main St, City, State 12345",
    "format": "SUPERMARKET",
    "size": 50000,
    "layout": "STANDARD",
    "constraints": {
      "maxGondolaHeight": 84,
      "aisleWidth": 8,
      "ceilingHeight": 12
    }
  },
  "aisles": [
    {
      "aisleId": "AISLE-001",
      "storeId": "STORE-001",
      "number": 5,
      "name": "Beverages",
      "category": "BEVERAGES",
      "length": 60,
      "width": 8,
      "gondolas": ["GONDOLA-001", "GONDOLA-002", "GONDOLA-003"]
    }
  ],
  "gondolas": [
    {
      "gondolaId": "GONDOLA-001",
      "aisleId": "AISLE-001",
      "number": 1,
      "type": "STANDARD",
      "width": 48,
      "depth": 24,
      "height": 84,
      "modules": {
        "left": "MODULE-001-L",
        "right": "MODULE-001-R"
      }
    }
  ],
  "modules": [
    {
      "moduleId": "MODULE-001-L",
      "gondolaId": "GONDOLA-001",
      "side": "LEFT",
      "width": 24,
      "depth": 18,
      "shelves": [
        {"shelfId": "SHELF-001", "level": 1, "height": 12},
        {"shelfId": "SHELF-002", "level": 2, "height": 24},
        {"shelfId": "SHELF-003", "level": 3, "height": 36},
        {"shelfId": "SHELF-004", "level": 4, "height": 60},
        {"shelfId": "SHELF-005", "level": 5, "height": 72}
      ]
    }
  ],
  "shelves": [
    {
      "shelfId": "SHELF-004",
      "moduleId": "MODULE-001-L",
      "level": 4,
      "height": 60,
      "depth": 18,
      "width": 24,
      "maxWeight": 500,
      "positions": [
        {"positionId": "POS-001", "index": 1, "x": 0, "width": 6},
        {"positionId": "POS-002", "index": 2, "x": 6, "width": 6},
        {"positionId": "POS-003", "index": 3, "x": 12, "width": 6},
        {"positionId": "POS-004", "index": 4, "x": 18, "width": 6}
      ]
    }
  ]
}
```

## Planogram Example

### Complete Planogram

```json
{
  "planogramId": "PLANO-001",
  "name": "Beverages Aisle 5 - Q1 2024",
  "storeId": "STORE-001",
  "category": "BEVERAGES",
  "version": 1,
  "status": "PUBLISHED",
  "createdDate": "2024-01-01T10:00:00Z",
  "approvedDate": "2024-01-05T14:30:00Z",
  "publishedDate": "2024-01-10T09:00:00Z",
  "createdBy": "merchandising@retail.com",
  "approvedBy": "operations@retail.com",
  "productPlacements": [
    {
      "placementId": "PLACE-001",
      "productId": "PROD-001",
      "productName": "Coca-Cola 2L",
      "positionId": "POS-001",
      "shelfId": "SHELF-004",
      "facings": 3,
      "depth": 2,
      "startDate": "2024-01-15",
      "endDate": "2024-03-15",
      "rules": [
        "HIGH_ROTATION_EYE_LEVEL",
        "BRAND_BLOCKING"
      ]
    },
    {
      "placementId": "PLACE-002",
      "productId": "PROD-002",
      "productName": "Pepsi 2L",
      "positionId": "POS-002",
      "shelfId": "SHELF-004",
      "facings": 2,
      "depth": 2,
      "startDate": "2024-01-15",
      "endDate": "2024-03-15",
      "rules": [
        "HIGH_ROTATION_EYE_LEVEL",
        "BRAND_BLOCKING"
      ]
    },
    {
      "placementId": "PLACE-003",
      "productId": "PROD-003",
      "productName": "Sprite 2L",
      "positionId": "POS-003",
      "shelfId": "SHELF-004",
      "facings": 2,
      "depth": 2,
      "startDate": "2024-01-15",
      "endDate": "2024-03-15",
      "rules": [
        "HIGH_ROTATION_EYE_LEVEL",
        "BRAND_BLOCKING"
      ]
    }
  ]
}
```

## Product Placement Detail

### Product Placement with Full Context

```json
{
  "placementId": "PLACE-001",
  "planogramId": "PLANO-001",
  "product": {
    "productId": "PROD-001",
    "name": "Coca-Cola 2L",
    "sku": "COKE-2L-001",
    "brand": "Coca-Cola",
    "category": "BEVERAGES",
    "subcategory": "SOFT_DRINKS",
    "subSubcategory": "COLA",
    "dimensions": {
      "height": 12,
      "width": 4,
      "depth": 4,
      "weight": 4.4
    },
    "rotation": "HIGH",
    "rotationUnits": 150
  },
  "position": {
    "positionId": "POS-001",
    "shelfId": "SHELF-004",
    "shelfLevel": 4,
    "shelfHeight": 60,
    "moduleId": "MODULE-001-L",
    "gondolaId": "GONDOLA-001",
    "aisleId": "AISLE-001",
    "storeId": "STORE-001",
    "index": 1,
    "x": 0,
    "width": 6,
    "depth": 18
  },
  "placement": {
    "facings": 3,
    "depth": 2,
    "startDate": "2024-01-15",
    "endDate": "2024-03-15"
  },
  "rules": [
    {
      "ruleId": "HIGH_ROTATION_EYE_LEVEL",
      "name": "High-Rotation Products at Eye Level",
      "category": "ROTATION",
      "priority": "MEDIUM",
      "applied": true,
      "compliant": true
    },
    {
      "ruleId": "BRAND_BLOCKING",
      "name": "Brand Blocking",
      "category": "BRAND",
      "priority": "MEDIUM",
      "applied": true,
      "compliant": true
    }
  ],
  "validation": {
    "valid": true,
    "violations": [],
    "warnings": []
  }
}
```

## Store Hierarchy Query Examples

### Query: Find All Products in Aisle 5

```json
{
  "query": "Find all products in Aisle 5",
  "filter": {
    "aisleId": "AISLE-001"
  },
  "results": [
    {
      "productId": "PROD-001",
      "productName": "Coca-Cola 2L",
      "position": "Aisle 5, Gondola 1, Module Left, Shelf 4, Position 1"
    },
    {
      "productId": "PROD-002",
      "productName": "Pepsi 2L",
      "position": "Aisle 5, Gondola 1, Module Left, Shelf 4, Position 2"
    }
  ]
}
```

### Query: Find All High-Rotation Products at Eye Level

```json
{
  "query": "Find all high-rotation products at eye level",
  "filter": {
    "rotation": "HIGH",
    "shelfLevel": [4, 5]
  },
  "results": [
    {
      "productId": "PROD-001",
      "productName": "Coca-Cola 2L",
      "shelfLevel": 4,
      "rotation": "HIGH"
    }
  ]
}
```

### Query: Find All Products in Category "Beverages"

```json
{
  "query": "Find all products in Beverages category",
  "filter": {
    "category": "BEVERAGES"
  },
  "results": [
    {
      "productId": "PROD-001",
      "productName": "Coca-Cola 2L",
      "category": "BEVERAGES",
      "subcategory": "SOFT_DRINKS"
    }
  ]
}
```

## Planogram Versioning Example

### Version History

```json
{
  "planogramId": "PLANO-001",
  "versions": [
    {
      "version": 1,
      "status": "ARCHIVED",
      "createdDate": "2024-01-01",
      "publishedDate": "2024-01-10",
      "changes": "Initial version"
    },
    {
      "version": 2,
      "status": "PUBLISHED",
      "createdDate": "2024-02-01",
      "publishedDate": "2024-02-10",
      "changes": "Updated product placements based on sales data"
    }
  ],
  "currentVersion": 2
}
```

## Related Documents

- `docs/04-store-layout-model.md` - Store layout model
- `examples/store-layout-json-example.md` - JSON examples
