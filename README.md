# FigmaActivity
Figma Activity
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamic Page with JSON</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        header {
            background-color: #333;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        .filter {
            margin: 20px 0;
        }
        .items {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }
        .item {
            background-color: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: calc(33.333% - 20px);
            box-sizing: border-box;
        }
    </style>
</head>
<body>
    <header>
        <h1>Product List</h1>
    </header>
    <div class="filter">
        <label for="categoryFilter">Filter by Category:</label>
        <select id="categoryFilter">
            <option value="all">All</option>
            <option value="Category A">Category A</option>
            <option value="Category B">Category B</option>
            <option value="Category C">Category C</option>
        </select>
    </div>
    <div class="items" id="itemsContainer"></div>
    <script>
        const data = [
            {
                "id": 1,
                "name": "Product 1",
                "category": "Category A",
                "price": 10.99
            },
            {
                "id": 2,
                "name": "Product 2",
                "category": "Category B",
                "price": 15.49
            },
            {
                "id": 3,
                "name": "Product 3",
                "category": "Category A",
                "price": 7.99
            },
            {
                "id": 4,
                "name": "Product 4",
                "category": "Category C",
                "price": 12.99
            }
        ];

        function renderItems(filter = 'all') {
            const container = document.getElementById('itemsContainer');
            container.innerHTML = ''; // Clear previous items

            const filteredData = filter === 'all' ? data : data.filter(item => item.category === filter);

            filteredData.forEach(item => {
                const itemElement = document.createElement('div');
                itemElement.classList.add('item');
                itemElement.innerHTML = `
                    <h2>${item.name}</h2>
                    <p>Category: ${item.category}</p>
                    <p>Price: $${item.price.toFixed(2)}</p>
                `;
                container.appendChild(itemElement);
            });
        }

        document.getElementById('categoryFilter').addEventListener('change', (event) => {
            renderItems(event.target.value);
        });

        // Initial render
        renderItems();
    </script>
</body>
</html>
