# ST10447515_IMAD_5112
Kimeshan Padyaachee
the purpose of this weather app allows the user to check the average tempreature for the week and the weather condition for that specific day of the week
# Define a data structure to represent the weather information
struct WeatherData {
    string day_of_week;  # Monday, Tuesday,..., Sunday
    double max_temperature;
    double min_temperature;
    string weather_condition;  # Sunny, Cloudy, Rainy, etc.
}

# Define an array to store the weather data for each day of the week
WeatherData[] weather_data = new WeatherData[7];

# Initialize the weather data for each day of the week
for i = 0 to 6 {
    weather_data[i].day_of_week = get_day_of_week(i);  # Get the day of the week (e.g. Monday, Tuesday, etc.)
    weather_data[i].max_temperature = -INFINITY;  # Initialize max temperature to negative infinity
    weather_data[i].min_temperature = INFINITY;  # Initialize min temperature to positive infinity
    weather_data[i].weather_condition = "";  # Initialize weather condition to empty string
}

# Function to get the day of the week
function get_day_of_week(int day) {
    switch day {
        case 0: return "Monday";
        case 1: return "Tuesday";
        case 2: return "Wednesday";
        case 3: return "Thursday";
        case 4: return "Friday";
        case 5: return "Saturday";
        case 6: return "Sunday";
    }
}

# Function to update the weather data
function update_weather_data(int day, double temperature, string condition) {
    if temperature > weather_data[day].max_temperature {
        weather_data[day].max_temperature = temperature;
    }
    if temperature < weather_data[day].min_temperature {
        weather_data[day].min_temperature = temperature;
    }
    weather_data[day].weather_condition = condition;
}

# Function to display the weather data
function display_weather_data() {
    for i = 0 to 6 {
        print("Day: " + weather_data[i].day_of_week);
        print("Max Temperature: " + weather_data[i].max_temperature + "°C");
        print("Min Temperature: " + weather_data[i].min_temperature + "°C");
        print("Weather Condition: " + weather_data[i].weather_condition);
        print();
    }
}

# Load weather data from database
for i = 0 to 6 {
    weather_data[i].max_temperature = get_max_temp_from_api(i);
    weather_data[i].min_temperature = get_min_temp_from_api(i);
    weather_data[i].weather_condition = get_weather_condition_from_api(i);
}

# Display the weather data
display_weather_data()
