# Sanity Schema Documentation

## Overview
This document describes the content schemas used in the 24/7 Store Sanity CMS.

## Schemas

### Product

**Location**: `schemaTypes/product.js`

**Description**: Represents a product in the store catalog.

**Fields**:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | Yes | Product name |
| `description` | text | No | Product description |
| `price` | number | Yes | Product price (must be positive) |
| `image` | image | No | Product image with hotspot support |
| `category` | string | No | Product category (electronics, clothing, food, books) |
| `inStock` | boolean | No | Stock availability (default: true) |

**Usage Example**:
```javascript
// Frontend query
const products = await sanityClient.fetch('*[_type == "product"]')
```

---

## Adding New Schemas

To add a new schema:

1. Create a new file in `schemaTypes/` (e.g., `schemaTypes/category.js`)
2. Define the schema following Sanity's schema format
3. Import and add to `schemaTypes/index.js`
4. Document it in this file

## Schema Best Practices

- Use validation rules to ensure data quality
- Add helpful descriptions for content editors
- Use appropriate field types (string, text, number, etc.)
- Consider using references for relationships between documents
- Add preview configurations for better editor experience

## References

- [Sanity Schema Documentation](https://www.sanity.io/docs/schema-types)
- [Field Types Reference](https://www.sanity.io/docs/schema-types)
- [Validation Rules](https://www.sanity.io/docs/validation)
