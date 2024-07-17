

### HTML, CSS, and JavaScript Combined Weather Forecast App

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather Forecast App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #e0f7fa;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .weather-container {
            background: #ffffff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        h2 {
            margin-bottom: 20px;
        }
        .input-container {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }
        .input-container input {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-right: 10px;
            width: 200px;
        }
        .input-container button {
            padding: 10px 20px;
            border: none;
            background-color: #00796b;
            color: white;
            border-radius: 4px;
            cursor: pointer;
        }
        .input-container button:hover {
            background-color: #004d40;
        }
        .weather-info {
            display: none;
            margin-top: 20px;
        }
        .weather-info p {
            margin: 5px 0;
        }
    </style>
</head>
<body>
    <div class="weather-container">
        <h2>Weather Forecast</h2>
        <div class="input-container">
            <input type="text" id="cityInput" placeholder="Enter city name">
            <button onclick="getWeather()">Get Weather</button>
        </div>
        <div class="weather-info" id="weatherInfo">
            <p><strong>City:</strong> <span id="cityName"></span></p>
            <p><strong>Temperature:</strong> <span id="temperature"></span> °C</p>
            <p><strong>Weather:</strong> <span id="weatherDescription"></span></p>
        </div>
    </div>

    <script>
        async function getWeather() {
            const apiKey = 'YOUR_API_KEY'; // Replace with your OpenWeatherMap API key
            const city = document.getElementById('cityInput').value.trim();
            if (city === '') return;

            const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${apiKey}`;
            try {
                const response = await fetch(url);
                const data = await response.json();

                if (data.cod === 200) {
                    document.getElementById('cityName').textContent = data.name;
                    document.getElementById('temperature').textContent = data.main.temp;
                    document.getElementById('weatherDescription').textContent = data.weather[0].description;
                    document.getElementById('weatherInfo').style.display = 'block';
                } else {
                    alert('City not found. Please enter a valid city name.');
                    document.getElementById('weatherInfo').style.display = 'none';
                }
            } catch (error) {
                alert('Error fetching the weather data.');
                console.error(error);
            }
        }
    </script>
</body>
</html>
```

### Explanation

1. **HTML Structure**:
    - The `div` with the class `weather-container` contains the entire app.
    - Inside it, there’s an `h2` tag for the title, an `input-container` for the input field and the "Get Weather" button, and a `div` with the class `weather-info` where the weather details will be displayed.

2. **CSS Styling**:
    - The body is styled to center the content vertically and horizontally with a light background.
    - The `.weather-container` is styled with padding, a white background, rounded corners, and a shadow for a card-like appearance.
    - Buttons and input fields are styled for better appearance and usability.
    - The `.weather-info` is initially hidden and will be displayed only when valid weather data is fetched.

3. **JavaScript Functionality**:
    - `getWeather()`: This async function is called when the "Get Weather" button is clicked. It fetches the weather data from the OpenWeatherMap API using the entered city name.
    - If the city is found, it updates the HTML elements with the weather data and displays the `.weather-info` div.
    - If the city is not found or there’s an error, it alerts the user and hides the `.weather-info` div.

### Conclusion

This simple Weather Forecast App demonstrates how HTML, CSS, and JavaScript can be combined to create an interactive web application. The app fetches weather data from the OpenWeatherMap API and displays it to the user. This example can be further expanded with additional features such as a weather icon, forecast for multiple days, and improved error handling.
