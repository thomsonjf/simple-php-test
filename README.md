# Simple PHP Questions

### Question One

The code snippet below shows a very simple representation of a shopping cart with three methods - one to add a product to the cart, one to remove a product from the cart and a third method to list the contents of the cart.

An item can be added to the cart multiple times - if this happens then it should be listed once, but with a quantity that reflects the number of times it has been added.

#### Tasks

1. The `addToCart` method is a bit buggy which means it might not behave as expected - can you identify the issues and implement the method correctly?

2. Please implement the `updateQuantity` and `removeFromCart` methods, considering edge cases for example what happens if an item in the basket is updated with a quantity of 0 or -1?

```
<?php

namespace Test\SimpleQuestions;

class ShoppingCart
{
    /**
     * Holds the contents of the cart
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





  
