---
layout: default
title: $from()
parent: cheat-sheet
grand_parent: Guides
---

# 🧾 $from() Cheat Sheet (OpenAF Array Superpowers)

## 🔍 Filtering

```javascript
$from(arr).equals("key", "value").select()
$from(arr).greater("size", 1024).select()
$from(arr).contains("tags", "urgent").select()
$from(arr).where(r => r.name.startsWith("A")).select()
```

## 📊 Sorting

```javascript
$from(arr).sort("name").select()
$from(arr).sort("-date", "priority").select()  // "-" for descending
```

## 🏷️ Selecting/Mapping

```javascript
$from(arr).select(r => ({ id: r.id, label: r.name.toUpperCase() }))
```

## 🧮 Aggregation

```javascript
$from(arr).sum("amount")       // total of amount fields
$from(arr).count()             // count all
$from(arr).avg("score")        // average score
$from(arr).max("age")          // max age
```

## 🧩 Grouping

```javascript
$from(arr).group("type").select()
```

Result: a list of { key: type, values: [...] }

## 🧹 Distinct

```javascript
$from(arr).distinct("category").select()
```

## 🔗 Combining Sets

```javascript
$from(arr1).intersect(arr2).select()
$from(arr1).except(arr2).select()
$from(arr1).cartesian(arr2).select()
```

## 🧰 Common Patterns

**Get first match**

```javascript
$from(arr).equals("status", "active").at(0)
```

**Chain filters** 

```javascript
$from(arr).greater("price", 10).less("price", 100).select()
```

**Use custom logic**

```javascript
$from(arr).where(r => r.date < now()).select()
```
