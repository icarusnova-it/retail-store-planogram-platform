# Compliance Check Example

## Overview

This document provides examples of compliance checking for planograms, including rule compliance, brand compliance, and regulatory compliance.

## Compliance Check Report

### Complete Compliance Report

```json
{
  "planogramId": "PLANO-001",
  "storeId": "STORE-001",
  "complianceCheckDate": "2024-01-15T10:00:00Z",
  "overallCompliance": 92.5,
  "status": "COMPLIANT",
  "checks": {
    "ruleCompliance": {
      "score": 95.0,
      "status": "COMPLIANT",
      "totalRules": 20,
      "compliantRules": 19,
      "violations": 1,
      "details": [
        {
          "ruleId": "HIGH_ROTATION_EYE_LEVEL",
          "status": "COMPLIANT",
          "checkedProducts": 15,
          "compliantProducts": 15,
          "violations": 0
        },
        {
          "ruleId": "BRAND_BLOCKING",
          "status": "COMPLIANT",
          "checkedProducts": 50,
          "compliantProducts": 50,
          "violations": 0
        },
        {
          "ruleId": "WEIGHT_CONSTRAINT",
          "status": "VIOLATION",
          "checkedProducts": 10,
          "compliantProducts": 9,
          "violations": 1,
          "violationDetails": [
            {
              "productId": "PROD-010",
              "productName": "Heavy Product",
              "violation": "Product weight exceeds shelf capacity",
              "shelfId": "SHELF-003",
              "recommendation": "Move to lower shelf (Shelf 1-2)"
            }
          ]
        }
      ]
    },
    "brandCompliance": {
      "score": 90.0,
      "status": "COMPLIANT",
      "totalBrands": 10,
      "compliantBrands": 9,
      "violations": 1,
      "details": [
        {
          "brandId": "BRAND-001",
          "brandName": "Coca-Cola",
          "status": "COMPLIANT",
          "requirements": {
            "minFacings": 3,
            "actualFacings": 3,
            "preferredHeight": "EYE_LEVEL",
            "actualHeight": "EYE_LEVEL"
          }
        },
        {
          "brandId": "BRAND-002",
          "brandName": "Premium Brand",
          "status": "VIOLATION",
          "requirements": {
            "minFacings": 4,
            "actualFacings": 2,
            "preferredHeight": "EYE_LEVEL",
            "actualHeight": "EYE_LEVEL"
          },
          "violation": "Minimum facings not met (required: 4, actual: 2)",
          "recommendation": "Increase facings to 4"
        }
      ]
    },
    "regulatoryCompliance": {
      "score": 100.0,
      "status": "COMPLIANT",
      "totalChecks": 5,
      "compliantChecks": 5,
      "violations": 0,
      "details": [
        {
          "checkType": "AGE_RESTRICTED_PLACEMENT",
          "status": "COMPLIANT",
          "checkedProducts": 3,
          "compliantProducts": 3,
          "details": "All age-restricted products on lower shelves"
        },
        {
          "checkType": "SAFETY_REGULATIONS",
          "status": "COMPLIANT",
          "checkedProducts": 100,
          "compliantProducts": 100,
          "details": "All products comply with safety regulations"
        }
      ]
    },
    "categoryCompliance": {
      "score": 95.0,
      "status": "COMPLIANT",
      "totalCategories": 8,
      "compliantCategories": 8,
      "violations": 0,
      "details": [
        {
          "categoryId": "CAT-001",
          "categoryName": "Beverages",
          "status": "COMPLIANT",
          "rules": {
            "categoryGrouping": "COMPLIANT",
            "categoryFlow": "COMPLIANT",
            "categorySize": "COMPLIANT"
          }
        }
      ]
    },
    "storeCompliance": {
      "score": 100.0,
      "status": "COMPLIANT",
      "totalConstraints": 5,
      "compliantConstraints": 5,
      "violations": 0,
      "details": [
        {
          "constraintType": "CEILING_HEIGHT",
          "status": "COMPLIANT",
          "required": 84,
          "actual": 84,
          "details": "Gondola height within ceiling height limit"
        },
        {
          "constraintType": "AISLE_WIDTH",
          "status": "COMPLIANT",
          "required": 8,
          "actual": 8,
          "details": "Aisle width meets requirements"
        }
      ]
    }
  },
  "violations": [
    {
      "violationId": "VIOL-001",
      "type": "RULE_VIOLATION",
      "severity": "MEDIUM",
      "ruleId": "WEIGHT_CONSTRAINT",
      "productId": "PROD-010",
      "message": "Product weight exceeds shelf capacity",
      "recommendation": "Move to lower shelf"
    },
    {
      "violationId": "VIOL-002",
      "type": "BRAND_VIOLATION",
      "severity": "HIGH",
      "brandId": "BRAND-002",
      "message": "Minimum facings not met",
      "recommendation": "Increase facings to 4"
    }
  ],
  "recommendations": [
    "Move heavy product to lower shelf",
    "Increase facings for premium brand",
    "Review weight constraints for shelf 3"
  ]
}
```

## Compliance Check by Category

### Rule Compliance Check

```json
{
  "checkType": "RULE_COMPLIANCE",
  "planogramId": "PLANO-001",
  "rulesChecked": [
    {
      "ruleId": "HIGH_ROTATION_EYE_LEVEL",
      "ruleName": "High-Rotation Products at Eye Level",
      "priority": "MEDIUM",
      "status": "COMPLIANT",
      "checkedProducts": 15,
      "compliantProducts": 15,
      "violations": 0,
      "complianceRate": 100.0
    },
    {
      "ruleId": "BRAND_BLOCKING",
      "ruleName": "Brand Blocking",
      "priority": "MEDIUM",
      "status": "COMPLIANT",
      "checkedProducts": 50,
      "compliantProducts": 50,
      "violations": 0,
      "complianceRate": 100.0
    },
    {
      "ruleId": "WEIGHT_CONSTRAINT",
      "ruleName": "Shelf Weight Capacity",
      "priority": "HIGH",
      "status": "VIOLATION",
      "checkedProducts": 10,
      "compliantProducts": 9,
      "violations": 1,
      "complianceRate": 90.0,
      "violationDetails": [
        {
          "productId": "PROD-010",
          "violation": "Weight exceeds shelf capacity",
          "severity": "HIGH"
        }
      ]
    }
  ],
  "overallCompliance": 96.7
}
```

### Brand Compliance Check

```json
{
  "checkType": "BRAND_COMPLIANCE",
  "planogramId": "PLANO-001",
  "brandsChecked": [
    {
      "brandId": "BRAND-001",
      "brandName": "Coca-Cola",
      "status": "COMPLIANT",
      "requirements": {
        "minFacings": 3,
        "actualFacings": 3,
        "preferredHeight": "EYE_LEVEL",
        "actualHeight": "EYE_LEVEL",
        "exclusivity": false
      },
      "complianceScore": 100.0
    },
    {
      "brandId": "BRAND-002",
      "brandName": "Premium Brand",
      "status": "VIOLATION",
      "requirements": {
        "minFacings": 4,
        "actualFacings": 2,
        "preferredHeight": "EYE_LEVEL",
        "actualHeight": "EYE_LEVEL",
        "exclusivity": true
      },
      "complianceScore": 50.0,
      "violations": [
        {
          "requirement": "MIN_FACINGS",
          "required": 4,
          "actual": 2,
          "violation": "Minimum facings not met"
        }
      ]
    }
  ],
  "overallCompliance": 90.0
}
```

### Regulatory Compliance Check

```json
{
  "checkType": "REGULATORY_COMPLIANCE",
  "planogramId": "PLANO-001",
  "regulatoryChecks": [
    {
      "checkType": "AGE_RESTRICTED_PLACEMENT",
      "status": "COMPLIANT",
      "regulation": "Alcohol products must be on lower shelves",
      "checkedProducts": 3,
      "compliantProducts": 3,
      "violations": 0,
      "details": "All alcohol products on shelf 1-2 (lower shelves)"
    },
    {
      "checkType": "SAFETY_REGULATIONS",
      "status": "COMPLIANT",
      "regulation": "Heavy products on lower shelves",
      "checkedProducts": 10,
      "compliantProducts": 10,
      "violations": 0,
      "details": "All heavy products on shelf 1-2"
    },
    {
      "checkType": "FOOD_SAFETY",
      "status": "COMPLIANT",
      "regulation": "Raw meat separate from ready-to-eat",
      "checkedProducts": 20,
      "compliantProducts": 20,
      "violations": 0,
      "details": "Proper product separation maintained"
    }
  ],
  "overallCompliance": 100.0
}
```

## Compliance Violation Handling

### Violation Report

```json
{
  "violationId": "VIOL-001",
  "planogramId": "PLANO-001",
  "violationType": "RULE_VIOLATION",
  "severity": "HIGH",
  "ruleId": "WEIGHT_CONSTRAINT",
  "ruleName": "Shelf Weight Capacity",
  "product": {
    "productId": "PROD-010",
    "productName": "Heavy Product 10L",
    "weight": 12.5
  },
  "position": {
    "shelfId": "SHELF-003",
    "shelfLevel": 3,
    "shelfCapacity": 600,
    "currentWeight": 580,
    "productWeight": 12.5,
    "totalWeight": 592.5
  },
  "violation": {
    "message": "Product weight would exceed shelf capacity",
    "currentCapacity": 600,
    "requiredCapacity": 612.5,
    "excess": 12.5
  },
  "recommendation": {
    "action": "Move product to lower shelf",
    "targetShelf": "SHELF-001",
    "targetShelfCapacity": 1000,
    "reason": "Lower shelf has higher weight capacity"
  },
  "status": "PENDING_CORRECTION"
}
```

## Related Documents

- `docs/06-constraints-and-compliance.md` - Constraints and compliance
- `docs/05-product-placement-rules.md` - Product placement rules
