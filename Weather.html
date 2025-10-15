<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather Forecast</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(to bottom right, #4a00e0, #8e2de2); /* Deep purple gradient */
        }
        .container {
            backdrop-filter: blur(10px);
            background-color: rgba(255, 255, 255, 0.1); /* Slightly transparent background */
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
        }
        .weather-info {
            background-color: rgba(255, 255, 255, 0.05);
        }
        .forecast-button {
            background: linear-gradient(to right, #6EE7B7, #3B82F6); /* Green-blue gradient */
            transition: all 0.2s ease-in-out;
        }
        .forecast-button:hover {
            transform: scale(1.05);
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4);
        }
        .forecast-button:active {
            transform: scale(0.95);
        }
        input::placeholder {
            color: #ccc;
        }
    </style>
</head>
<body class="flex items-center justify-center min-h-screen p-4">
    <div class="container bg-white bg-opacity-10 rounded-xl p-8 max-w-lg w-full text-white shadow-lg backdrop-blur-md">
        <h1 class="text-4xl font-bold text-center mb-6 text-white">Weather Forecast</h1>

        <div class="mb-6">
            <input type="text" id="cityInput" placeholder="Enter city name (e.g., London)"
                   class="w-full p-3 rounded-lg bg-gray-700 bg-opacity-50 text-white placeholder-gray-300 focus:outline-none focus:ring-2 focus:ring-purple-400 border border-gray-600">
        </div>

        <button id="getWeatherBtn"
                class="w-full forecast-button text-white font-bold py-3 px-4 rounded-lg focus:outline-none focus:shadow-outline mb-6">
            Get Weather
        </button>

        <div id="loadingIndicator" class="text-center py-4 hidden">
            <div class="animate-spin rounded-full h-8 w-8 border-b-2 border-white mx-auto"></div>
            <p class="mt-2 text-white">Fetching weather data and generating image...</p>
        </div>

        <div id="weatherResult" class="hidden weather-info rounded-lg p-6 text-center border border-gray-600">
            <h2 id="cityName" class="text-3xl font-semibold mb-2"></h2>
            <p id="temperature" class="text-5xl font-bold mb-4"></p>
            <p id="description" class="text-2xl capitalize mb-4"></p>
            <img id="weatherImage" src="" alt="Weather Image" class="w-full max-w-md h-auto rounded-lg mx-auto mb-4 object-cover" onerror="this.onerror=null;this.src='https://placehold.co/400x250/5B21B6/FFFFFF?text=No+Image';">
            <div class="grid grid-cols-2 gap-4 text-xl">
                <p><span class="font-semibold">Humidity:</span> <span id="humidity"></span></p>
                <p><span class="font-semibold">Wind Speed:</span> <span id="windSpeed"></span></p>
            </div>
        </div>

        <div id="messageBox" class="bg-red-500 text-white p-4 rounded-lg text-center mt-4 hidden"></div>
    </div>

    <script>
        const cityInput = document.getElementById('cityInput');
        const getWeatherBtn = document.getElementById('getWeatherBtn');
        const weatherResult = document.getElementById('weatherResult');
        const cityName = document.getElementById('cityName');
        const temperature = document.getElementById('temperature');
        const description = document.getElementById('description');
        const humidity = document.getElementById('humidity');
        const windSpeed = document.getElementById('windSpeed');
        const weatherImage = document.getElementById('weatherImage');
        const loadingIndicator = document.getElementById('loadingIndicator');
        const messageBox = document.getElementById('messageBox');

        // IMPORTANT: Replace 'YOUR_OPENWEATHERMAP_API_KEY' with your actual API key from openweathermap.org
        const OPENWEATHERMAP_API_KEY = '2cf89b2af46637bfff0ebef91541aac3';

        // Function to show messages
        function showMessage(msg, type = 'error') {
            messageBox.textContent = msg;
            messageBox.className = `bg-${type === 'error' ? 'red' : 'green'}-500 text-white p-4 rounded-lg text-center mt-4`;
            messageBox.classList.remove('hidden');
            setTimeout(() => {
                messageBox.classList.add('hidden');
            }, 5000);
        }

        // Function to fetch weather data from OpenWeatherMap
        async function getWeatherData(city) {
            const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${OPENWEATHERMAP_API_KEY}&units=metric`;
            const response = await fetch(url);
            if (!response.ok) {
                const errorData = await response.json();
                throw new Error(errorData.message || 'Could not fetch weather data.');
            }
            return await response.json();
        }

        // Function to generate image based on weather description
        async function generateWeatherImage(prompt) {
            let imageUrl = '';
            let retries = 0;
            const maxRetries = 3;
            const baseDelay = 1000; // 1 second

            while (retries < maxRetries) {
                try {
                    const payload = { instances: { prompt: prompt }, parameters: { "sampleCount": 1 } };
                    const apiKey = ""; // Canvas will provide this at runtime
                    // Removed ?key=${apiKey} from the URL as per debugging common 401 issues with Canvas API injection
                    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/imagen-3.0-generate-002:predict`; 

                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    // Check if the response is OK and has content
                    if (!response.ok) {
                        const errorText = await response.text(); // Get raw text for better debugging
                        throw new Error(`API error: ${response.status} - ${errorText}`);
                    }

                    // Check if the response body is empty (e.g., status 204 No Content)
                    const contentLength = response.headers.get('content-length');
                    if (contentLength === '0' || response.status === 204) {
                        throw new Error("Image API returned empty response.");
                    }

                    const result = await response.json();

                    if (result && result.predictions && result.predictions.length > 0 && result.predictions[0].bytesBase64Encoded) {
                        imageUrl = `data:image/png;base64,${result.predictions[0].bytesBase64Encoded}`;
                        break; // Exit loop on success
                    } else {
                        console.error("Image generation failed or returned no data:", result);
                        throw new Error("Failed to get valid image data from API response.");
                    }
                } catch (error) {
                    console.error(`Attempt ${retries + 1} for image generation failed:`, error);
                    retries++;
                    if (retries < maxRetries) {
                        const delay = baseDelay * Math.pow(2, retries - 1); // Exponential backoff
                        await new Promise(res => setTimeout(res, delay));
                    } else {
                        // If all retries failed, log the final error
                        console.error("All retries for image generation failed.");
                    }
                }
            }
            return imageUrl;
        }

        // Main function to fetch weather data and generate image
        async function fetchWeatherAndImage() {
            const city = cityInput.value.trim();
            if (!city) {
                showMessage("Please enter a city name.");
                return;
            }

            // Hide previous results and show loading
            weatherResult.classList.add('hidden');
            loadingIndicator.classList.remove('hidden');
            weatherImage.src = ''; // Clear previous image

            try {
                // Fetch weather data
                const weatherData = await getWeatherData(city);

                const temp = weatherData.main.temp;
                const desc = weatherData.weather[0].description;
                const hum = weatherData.main.humidity;
                const wind = weatherData.wind.speed; // in meters/sec

                // Generate image based on actual weather description
                const prompt = `A realistic photo of ${desc} weather in ${city}, with local architecture in the background if possible.`;
                const imageUrl = await generateWeatherImage(prompt);

                if (!imageUrl) {
                    showMessage("Failed to generate weather image. Displaying default image.");
                    weatherImage.src = 'https://placehold.co/400x250/5B21B6/FFFFFF?text=Image+Failed';
                } else {
                    weatherImage.src = imageUrl;
                }

                // Populate weather data
                cityName.textContent = weatherData.name; // Use actual city name from API
                temperature.textContent = `${temp.toFixed(1)}°C`;
                description.textContent = desc;
                humidity.textContent = `${hum}%`;
                windSpeed.textContent = `${(wind * 3.6).toFixed(1)} km/h`; // Convert m/s to km/h

                weatherResult.classList.remove('hidden');
                loadingIndicator.classList.add('hidden');

            } catch (error) {
                console.error('Error fetching weather or generating image:', error);
                loadingIndicator.classList.add('hidden');
                let errorMessage = "An error occurred. Please try again.";
                if (error.message.includes("city not found")) {
                    errorMessage = "City not found. Please check the spelling.";
                } else if (error.message.includes("Invalid API key")) {
                    errorMessage = "Invalid OpenWeatherMap API key. Please check your key.";
                } else if (error.message.includes("Image API returned empty response") || error.message.includes("Failed to get valid image data")) {
                    errorMessage = "Could not generate a weather image. Please try again later.";
                } else if (error.message.includes("API error: 401")) {
                    errorMessage = "Image generation service authorization failed. Please try again later.";
                }
                showMessage(errorMessage);
                weatherImage.src = 'https://placehold.co/400x250/5B21B6/FFFFFF?text=Error'; // Fallback for general errors
            }
        }

        getWeatherBtn.addEventListener('click', fetchWeatherAndImage);
        cityInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                fetchWeatherAndImage();
            }
        });
    </script>
</body>
</html>
