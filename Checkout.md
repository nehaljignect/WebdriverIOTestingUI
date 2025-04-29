describe('Swag Labs - Checkout Flow', () => {
  it('should complete the checkout successfully', async () => {
    // 1. Open login page
    await browser.url('https://www.saucedemo.com');

    // 2. Login
    await $('#user-name').setValue('standard_user');
    await $('#password').setValue('secret_sauce');
    await $('#login-button').click();

    // 3. Add item to cart
    await $('#add-to-cart-sauce-labs-backpack').click();

    // 4. Go to cart
    await $('.shopping_cart_link').click();

    // 5. Proceed to checkout
    await $('#checkout').click();

    // 6. Enter user info
    await $('#first-name').setValue('John');
    await $('#last-name').setValue('Doe');
    await $('#postal-code').setValue('12345');
    await $('#continue').click();

    // 7. Finish checkout
    await $('#finish').click();

    // 8. Assert success message
    const successMsg = await $('.complete-header');
    await expect(successMsg).toHaveText('Thank you for your order!');
  });
});
