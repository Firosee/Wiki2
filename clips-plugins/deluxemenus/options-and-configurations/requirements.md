---
description: Everything about DeluxeMenus requirements!
---

# Requirements

## Syntax

> ```yaml
> # This option can also be:
> # open_requirement:
> # left_click_requirement:
> # right_click_requirement:
> view_requirement:
>   requirements:
>     # You can define multiple requirements.
>     # Each requiremnt should have a unique name.
>     requirement_name:
>       type: TYPE
>   # This can only be defined for open and
>   # left/right click requirement
>   deny_commands:
>     - "[ACTIONTYPE] ACTION"
>     - "[ACTIONTYPE] ACTION"
> ```

Requirements allow you to restrict certain actions or even an entire menu and only allow certain players to see and/or use the menu.

### Requirement types

| Type | Description |
| :--- | :--- |
| [Open Requirement](gui.md#open-requirements) | Defines the requirements to open the menu. |
| [View Requirement](item.md#view-requirement) | Defines the requirements to see an item in the menu. |
| [Left/Right Click Requirements](item.md#shift-left-middle-right-click-requirement) | Defines the requirements to left/right click an item. |

{% hint style="info" %}
* Placeholders can be used in the requirements.
* If you set multiple requirements, all of them should be met \(Use [JavaScript type](requirements.md#javascript) to add optional requirements\).
{% endhint %}

## Requirement types

### **Has permission**

> ```yaml
> type: has permission
> permission: TEXT
> ```

Checks if the player has the specified permission.

### **Has money**

> ```yaml
> type: has money
> amount: #
> ```

Checks if the player has the specified amount of money \([Vault](https://www.spigotmc.org/resources/34315/) is required\).

### **Has item**

> ```yaml
> type: has item
> material: "TEXT"
> data: #
> amount: #
> name: "TEXT"
> lore:
>   - "TEXT"
> ```

Checks if the player has the specified item in the inventory.

{% hint style="info" %}
You can use color/format codes in name and lore fields, but using `§` character instead of `&` character.
{% endhint %}

### **JavaScript**

> ```yaml
> type: javascript
> expression: 'EXPRESSION'
> ```
>
> > **Example:**
> >
> > ```yaml
> > type: javascript
> > expression: '%vault_eco_balance% >= 100'
> > ```

Evaluates a JavaScript expression that must return true or false.

### **String Equals**

> ```yaml
> type: string equals
> input: "TEXT"
> output: "TEXT"
> ```
>
> > **Example:**
> >
> > ```yaml
> > type: string equals
> > input: "%server_name%"
> > output: "HelpChat"
> > ```

Checks if `input:` matches `output:` \(Case sensitive\).

### **String Equals Ignore Case**

> ```yaml
> type: string equals ignorecase
> input: "TEXT"
> output: "TEXT"
> ```
>
> > **Example:**
> >
> > ```yaml
> > type: string equals ignorecase
> > input: "%server_name%"
> > output: "helpchat"
> > ```

Checks if `input:` matches `output:` \(Case insensitive\).

### **String Contains**

> ```yaml
> type: string contains
> input: "TEXT"
> output: "TEXT"
> ```
>
> > **Example:**
> >
> > ```yaml
> > type: string contains
> > input: "%server_name%"
> > output: "chat"
> > ```

Checks if `input:` contains `output:` \(Case sensitive\).

### **Comparators**

> ```yaml
> type: (==, >=, <=, !=, >, <)
> input: #
> output: #
> ```

Compares `input:` with `output:`.

#### Available options

| Comparator | Description |
| :--- | :--- |
| `==` | `input:` equals to `output:` |
| `>=` | `input:` greater than or equals to `output:` |
| `<=` | `input:` less than or equals to `output:` |
| `!=` | `input:` not equals to `output:` |
| `>` | `input:` greater than `output:` |
| `<` | `input:` less than `output:` |

## Examples

### Open Requirement

```yaml
open_requirement:
  requirements:
    example_1:
      type: has permission
      permission: open.menu.one
  deny_commands:
    - "[message] &cYou don't have the permission."
```

### View Requirement

```yaml
view_requirement:
  requirements:
    example_2:
      type: string equals
      input: "%player_is_op%"
      output: "yes"
```

### Left/Right Click Requirement

```yaml
# left_click_requirement: or
right_click_requirement:
  requirements:
    example_3:
      type: has money
      amount: 100
  deny_commands:
    - "[message] &7You don't have enough money."
```

