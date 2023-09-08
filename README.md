<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-commerce Site</title>
    
</head>
<body>
    <div class="container">
        <h1>Product List</h1>
        <div class="row">
            <div class="col-md-4">
                <div class="card">
                    <img src="product1.jpg" class="card-img-top" alt="Product 1">
                    <div class="card-body">
                        <h5 class="card-title">Product 1</h5>
                        <p class="card-text">Rs.10.00</p>
                        <button class="btn btn-primary" onclick="addToCart('Product 1', 10.00)">Add to Cart</button>
                    </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="card">
                    <img src="product1.jpg" class="card-img-top" alt="Product 1">
                    <div class="card-body">
                        <h5 class="card-title">Product 2</h5>
                        <p class="card-text">Rs.20.00</p>
                        <button class="btn btn-primary" onclick="addToCart('Product 2', 20.00)">Add to Cart</button>
                    </div>
                </div>
            </div>
        </div>
        <div class="row">
            
        </div>
        <hr>
        <h1>Shopping Cart</h1>
        <div id="cart">
            
        </div>
        
        <h3>Total Price: Rs.<span id="totalPrice">0.00</span></h3>
        
        <button class="btn btn-success" onclick="MakePay()">Make Payment</button>
    </div>

    <script>
        let cart = [];
        let totalPrice = 0;

        function addToCart(productName, price) {
            cart.push({ productName, price });
            totalPrice += price;
            displayCart();
            updateTotalPrice();
        }

        function removeFromCart(index) {
            totalPrice -= cart[index].price;
            cart.splice(index, 1);
            displayCart();
            updateTotalPrice();
        }

        function displayCart() {
            let cartDiv = document.getElementById('cart');
            cartDiv.innerHTML = '';

            cart.forEach((item, index) => {
                cartDiv.innerHTML += `
                    <div class="alert alert-info" role="alert">
                        ${item.productName} - Rs.${item.price}
                        <button class="btn btn-danger btn-sm float-right" onclick="removeFromCart(${index})">Remove</button>
                    </div>
                `;
            });
        }

        function updateTotalPrice() {
            document.getElementById('totalPrice').innerText = totalPrice.toFixed(2);
        }

        function MakePay() {
            alert('Payment successful!');
            cart = [];
            totalPrice = 0;
            displayCart();
            updateTotalPrice();
        }
    </script>
</body>
</html>
