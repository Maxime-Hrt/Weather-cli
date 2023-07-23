**README.md - Using the Sun Application**

The Sun application is a command-line tool developed in Go (Golang) that allows you to fetch weather forecasts for a specific city using the WeatherAPI. This README will guide you through using the application, including how to set up your environment variables to access the API, how to compile the application, and how to use it as the `sun` command in your terminal.

### Configuring WeatherAPI

To use the Sun application, you need to sign up for an account on WeatherAPI (https://www.weatherapi.com/) and obtain your API Key. This key is necessary to access weather data through the API.

Once you have your API Key, you need to set it up in a `.env` file located in the same directory as the Sun application. The content of the `.env` file should look like this:

```plaintext
WEATHER_API_KEY=YOUR_API_KEY
```

Replace `YOUR_API_KEY` with your actual API Key.

### Installation and Compilation

1. Ensure you have Go (Golang) installed on your system. If not, you can download and install Go from the official website: https://golang.org/dl/

2. Download the source code of the Sun application.

3. Install the required dependencies by running the following command:

   ```bash
   go get -u github.com/joho/godotenv
   go get -u github.com/fatih/color
   ```

4. Compile the application by running the `go build` command. This will generate an executable named `sun` in the same directory.

5. You can test the application by running `./sun` in your terminal. Make sure the `.env` file containing your API Key is present in the directory.

### Installing as the "sun" Command

To use the Sun application as the `sun` command in your terminal, follow these steps:

1. Copy your API Key from the `.env` file and modify the line
    ```go
    link := fmt.Sprintf("http://api.weatherapi.com/v1/forecast.json?key=%s&q=%s&days=1&aqi=no&alerts=no", WEATHER_KEY, q)
    ```
    to
    ```go
    link := fmt.Sprintf("http://api.weatherapi.com/v1/forecast.json?key=<YOUR_API_KEY>&q=%s&days=1&aqi=no&alerts=no", q)
    ```
    replacing `<YOUR_API_KEY>` with your actual API Key.

2. Delete or comment out all lines related to environment variables and the `.env` file:
    ```go
    //err := godotenv.Load()
    //err_verif(err)

    q := "Paris"
    if len(os.Args) >= 2 {
        q = os.Args[1]
    }
    //WEATHER_KEY := os.Getenv("WEATHER_API_KEY")
    link := fmt.Sprintf("http://api.weatherapi.com/v1/forecast.json?key=<YOUR_API_KEY>&q=%s&days=1&aqi=no&alerts=no", q)
    ```

3. Compile the application again by running the `go build` command. This will generate an executable named `sun` in the same directory.

4. Copy the `sun` executable to a directory included in your `PATH` environment variable. For example, you can copy it to `/usr/local/bin` using the following command (you will need administrator privileges):

   ```bash
   sudo cp ./sun /usr/local/bin
   ```

5. After copying the executable, you can now use the `sun` command directly in your terminal to fetch weather forecasts for the city of your choice.

### Using the Sun Application

To use the Sun application, open a terminal and execute the `sun` command followed by the name of the city for which you want to fetch weather forecasts (if you don't specify a city name, the program will automatically use Paris as the default city). For example, to get the forecast for London, run the following command:

```bash
sun London
```

The application will display the weather forecast for the specified city, including the current temperature, weather conditions, and hourly forecasts.

Please note that you need an active internet connection for the application to access the WeatherAPI and retrieve weather data.

---

This concludes the README for the Sun application. By following these instructions, you should be able to use the `sun` application to conveniently and easily get weather forecasts from your terminal. Feel free to ask any questions if you need further assistance!