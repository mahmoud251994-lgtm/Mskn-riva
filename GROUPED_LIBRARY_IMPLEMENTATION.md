# Sharaf Design System - Grouped Previous Projects Library

## New Grouping Logic

The new aggregation system does NOT group by item name only.

An item is considered identical ONLY if ALL of the following fields are identical:

- القسم الفرعي
- البند
- المواصفات
- المورد
- الموديل / اللون
- الصورة
- الحالة

If ANY field changes, a new grouped item is created.

---

## UI Changes

### Removed Columns
- عدد المشاريع
- آخر استخدام

### Added Filters Section
The same top category cards from the main page are added:

- خامات معمارية
- خامات كهربائية
- خامات صحية وميكانيكية

---

## Final Page Structure

- Same design as the current system
- Same table style
- Same filters
- Same export buttons
- Same print behavior
- Same multi-user compatibility

But with:

- Smart grouped items
- Expand button to show projects using this exact item
- Auto grouping after item updates

---

## Suggested Firebase Structure

projectGroupedLibrary/
  groupedItems/
    itemHash/
      subCategory
      itemName
      specifications
      supplier
      model
      imageUrl
      status
      projects/
        projectId/
          projectName
          addedBy
          createdAt

---

## Matching Function

```js
function generateItemHash(item) {
  return [
    item.subCategory || '',
    item.name || '',
    item.specifications || '',
    item.supplier || '',
    item.model || '',
    item.imageUrl || '',
    item.status || ''
  ]
    .join('||')
    .toLowerCase()
    .trim();
}
```

---

## Important Notes

- Current projects structure remains untouched.
- Printing page remains untouched.
- Existing sync logic remains untouched.
- Existing authentication remains untouched.
- This feature is added as a separate aggregation layer.

