# Using JSON with Custom Types

Encode and decode JSON data, regardless of its structure, using Swift’s JSON support.

[Download](https://docs-assets.developer.apple.com/published/83799f6e15/UsingJSONWithCustomTypes.zip)

## Overview

JSON data you send or receive from other apps, services, and files can come in many different shapes and structures. Use the techniques described in this sample to handle the differences between external JSON data and your app’s model types.

![](https://docs-assets.developer.apple.com/published/d7a01449d3/rendered2x-1581360204.png)

This sample defines a simple data type, GroceryProduct, and demonstrates how to construct instances of that type from several different JSON formats.

```swift
struct GroceryProduct: Codable {
    var name: String
    var points: Int
    var description: String?
}
```

## Read Data from Arrays

Use Swift’s expressive type system to avoid manually looping over collections of identically structured objects. This playground uses array types as values to see how to work with JSON that’s structured like this:

```json
[
    {
        "name": "Banana",
        "points": 200,
        "description": "A banana grown in Ecuador."
    }
]
```

## Change Key Names
Learn how to map data from JSON keys into properties on your custom types, regardless of their names. For example, this playground shows how to map the "product_name" key in the JSON below to the name property on GroceryProduct:

```json
{
    "product_name": "Banana",
    "product_cost": 200,
    "description": "A banana grown in Ecuador."
}
```

Custom mappings let you to apply the Swift [API Design Guidelines](https://swift.org/documentation/api-design-guidelines/) to the names of properties in your Swift model, even if the names of the JSON keys are different.

## Access Nested Data

Learn how to ignore structure and data in JSON that you don’t need in your code. This playground uses an intermediate type to see how to extract grocery products from JSON that looks like this to skip over unwanted data and structure:

```json
[
    {
        "name": "Home Town Market",
        "aisles": [
            {
                "name": "Produce",
                "shelves": [
                    {
                        "name": "Discount Produce",
                        "product": {
                            "name": "Banana",
                            "points": 200,
                            "description": "A banana that's perfectly ripe."
                        }
                    }
                ]
            }
        ]
    }
]
```

## Merge Data at Different Depths

Combine or separate data from different depths of a JSON structure by writing custom implementations of protocol requirements from Encodable and Decodable. This playground shows how to construct a GroceryProduct instance from JSON that looks like this:

```json
{
    "Banana": {
        "points": 200,
        "description": "A banana grown in Ecuador."
    }
}
```



