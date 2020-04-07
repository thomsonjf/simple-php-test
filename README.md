# Interview Questions - PHP/Database/Architecture

### Question One

The code snippet below shows a very simple representation of a shopping cart with three methods - one to add a product to the cart, one to remove a product from the cart and a third method to list the contents of the cart.

An item can be added to the cart multiple times - if this happens then it should be listed once, but with a quantity that reflects the number of times it has been added.

#### Tasks

1. The `addToCart` method is a bit buggy which means it might not behave as expected - can you identify the issues and implement the method correctly?

2. Please implement the `updateQuantity` and `removeFromCart` methods, considering edge cases for example what happens if an item in the basket is updated with a quantity of 0 or -1?

3. When packing items in an order for shipping, every individual item to be shipped needs it's own box. Please implement the `getCountOfItems` method to work out the number of boxes needed. Hint: your solution needs to consider quantities.

```
<?php

namespace Test\SimpleQuestions;

class ShoppingCart
{
    /**
     * Holds the contents of the cart
     * Mapping of SKU => QUANTITY
     *
     * @var array
     */
    protected $items = [];

    /**
     * Add a product to the cart
     *
     * @param string $sku
     * @param int $quantity
     */
    public function addToCart(string $sku, int $quantity)
    {
        foreach ($this->items as $productSku => $itemQuantity) {
            if ($productSku = $sku) {
                ++$itemQuantity;
            }
        }
    }

    /**
     * Update the item with a new quantity
     * 
     * @param string $sku
     * @param int $quantity
     */
    public function updateQuantity(string $sku, int $quantity)
    {
        // @todo - implement this
    }

    /**
     * Remove a product from the cart
     *
     * @param string $sku
     */
    public function removeFromCart(string $sku)
    {
        // @todo - implement this
    }
    
    /**
     * Get a count of every individual item in the cart
     * 
     * @return int
     */
    public function getCountOfItems(): int
    {
        // @todo - implement this
    }

    /**
     * Get items
     *
     * @return array
     */
    public function getItems()
    {
        return $this->items;
    }
}

```

### Question Two

The PHP function `array_map` can apply a custom callback to each element of a given array and return the resulting new array.

Complete the code fragment beneath to transform the `$initialValues` array into an array of integer ID's, plucking just the `id` value from each item in the list.

```
<?php

$initialValues = [
    ['id' => 38, 'name' => 'John'],
    ['id' => 39, 'name' => 'Rupert'],
    ['id' => 40, 'name' => 'Robert'],
    ['id' => 41, 'name' => 'Simon'],
    ['id' => 42, 'name' => 'Peter']
];

$mapped = array_map(
    function (array $item) {
    
    },
    $initialValues
);

print_r($mapped);

```

The expected output should be:

```
Array
(
    [0] => 38
    [1] => 39
    [2] => 40
    [3] => 41
    [4] => 42
)
```

### Question Three

The two table structures defined beneath represent the relationship between `brand` and `department` in a business. There is a foreign key between the two, such that a department has an optional (nullable) brand associated with it. 

#### brand
```
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| id         | int(11)      | NO   | PRI | NULL    |       |
| name       | varchar(255) | NO   |     | NULL    |       |
| created_at | timestamp    | YES  |     | NULL    |       |
| updated_at | timestamp    | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```

#### department
```
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| id         | char(36)     | NO   | PRI | NULL    |       |
| name       | varchar(255) | NO   |     | NULL    |       |
| brand_id   | int(11)      | YES  |     | NULL    |       |
| created_at | timestamp    | YES  |     | NULL    |       |
| updated_at | timestamp    | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```

Using the table structures, write a simple `SELECT` query that lists the `id` and `name` fields from the `department` table, and the `name` field from the `brand` table.

### Question Four

Scenario: The System Dashboard shows an overview of operations including key metrics. It can take a while to load - sometimes an e-mail newsletter will go out with links in it and several thousand system users might sign in at once. This creates a serious CPU spike and the storage layer (database in this case) can't keep up.

How would you solve this problem at the application layer?

### Question Five

Here are some quick fire general PHP and MVC framework type questions (without any particular allegiance to a framework!):

- Scenario - You've just taken over a new system written in a popular PHP MVC framework. You've noticed some of the controllers are over 500 lines long - briefly, how would you approach breaking this down?

- 
  
