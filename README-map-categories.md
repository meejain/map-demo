# Generic Map Category Filtering System

This document explains how to use the generic map category filtering system that allows you to create custom category filters for your interactive map.

## Overview

The map now supports generic category names like "option1", "option2", etc., making it reusable for any type of project - not just limited to specific domains like conservation or environmental projects.

## How It Works

### 1. Category Mapping Configuration

In `blocks/cards/cards.js`, you'll find this simple mapping:

```javascript
const categoryMapping = {
  'View all': { categoryId: 'all', isActive: true },
  Tous: { categoryId: 'all', isActive: true },
  option1: { categoryId: 'category_3' },
  option2: { categoryId: 'category_4' },
  option3: { categoryId: 'category_5' },
  option4: { categoryId: 'category_10' },
};
```

### 2. Customizing for Your Project

To customize for your specific use case, simply modify the mapping:

```javascript
// Example: Business Services Map
const categoryMapping = {
  'All services': { categoryId: 'all', isActive: true },
  'consulting': { categoryId: 'category_3' },
  'technology': { categoryId: 'category_4' },
  'marketing': { categoryId: 'category_5' },
  'support': { categoryId: 'category_10' },
};

// Example: Educational Programs Map
const categoryMapping = {
  'All programs': { categoryId: 'all', isActive: true },
  'undergraduate': { categoryId: 'category_3' },
  'graduate': { categoryId: 'category_4' },
  'research': { categoryId: 'category_5' },
  'online': { categoryId: 'category_10' },
};
```

### 3. Setting Up Your Map Markers

In your `initmapscript.js`, ensure each marker has the appropriate category:

```javascript
var marker = new google.maps.Marker({
  position: markerLatLng,
  map: map,
  cursor: 'default',
  item: 99,
  icon: iconpointer,
  category: "category_3" // This should match your mapping
});
```

### 4. Creating Category Filter Cards

In your HTML/content, create cards with either:

**Text-based categories:**
- Card text content should match the keys in your mapping (e.g., "consulting", "technology")

**Icon-based categories:**
- Icon images should have `data-icon-name` attribute matching your mapping keys
- Or the filename should match the mapping keys

## Key Features

### Dynamic Zoom Calculation
The system automatically calculates optimal zoom levels based on the geographic distribution of markers in each category:

- **Wide spread markers** → Lower zoom (zoomed out)
- **Clustered markers** → Higher zoom (zoomed in)
- **Few markers close together** → Very high zoom

### Mobile Responsiveness
The system automatically creates mobile-friendly versions of category filters.

### Legacy Support
The system maintains backward compatibility with existing category names while supporting new generic options.

## Usage Examples

### For a Restaurant Chain Map
```javascript
const categoryMapping = {
  'All locations': { categoryId: 'all', isActive: true },
  'fast-food': { categoryId: 'category_3' },
  'fine-dining': { categoryId: 'category_4' },
  'cafes': { categoryId: 'category_5' },
  'delivery-only': { categoryId: 'category_10' },
};
```

### For a Real Estate Map
```javascript
const categoryMapping = {
  'All properties': { categoryId: 'all', isActive: true },
  'residential': { categoryId: 'category_3' },
  'commercial': { categoryId: 'category_4' },
  'industrial': { categoryId: 'category_5' },
  'land': { categoryId: 'category_10' },
};
```

## Technical Implementation

### Shared Filtering Function
The system uses a shared function `filterMapByCategory()` that:
1. Creates a new bounds object
2. Filters markers based on category
3. Updates map display
4. Calls `map.fitBounds()` for automatic zoom

### No Duplicate Code
The refactored system eliminates code duplication by using a single shared filtering function across all category interactions.

## Getting Started

1. **Modify the category mapping** in `blocks/cards/cards.js`
2. **Update your marker categories** in `initmapscript.js`
3. **Create category filter cards** with matching text or icon names
4. **Test the filtering** - zoom levels will adjust automatically

That's it! Your map now supports custom categories with automatic zoom optimization.
