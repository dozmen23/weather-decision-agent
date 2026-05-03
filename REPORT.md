# Weather Decision Agent - Technical Report

## 1. Project Scope

Weather Decision Agent is a Python-based decision support system that recommends daily activities based on weather conditions and user preferences.

The system will use weather variables such as temperature, weather condition, precipitation, wind speed, and humidity. These variables will be combined with user preferences such as indoor/outdoor preference, activity intensity, and budget level.

The main goal of the project is to convert raw weather data into ranked activity recommendations. In this project, the decision-making process will be supported by GPT-4o mini. GPT-4o mini will analyze the normalized weather data, user preferences, and possible activity options, then decide which activities are the most suitable for the user. It will also generate short explanations for the recommended activities.

The system will evaluate predefined activity options according to weather conditions and user preferences. However, instead of relying only on fixed heuristic scoring, the final recommendation decision and ranking will be made by the GPT-4o mini based decision agent.

The project will be developed as a modular Python application and presented through a simple Streamlit web interface.

## 2. Data Source and Collection Method

The project will use real weather data collected from an external weather API. OpenWeatherMap will be used as the main weather data source because it provides real-time weather data in JSON format and includes the required variables such as temperature, weather condition, humidity, wind speed, and precipitation.

The weather data will be fetched according to the user’s selected location. The API response will be received in JSON format and converted into the project’s internal data structure before being used by the decision agent.

The data collection process will work as follows:

1. The user enters a location through the Streamlit interface.
2. The weather service sends a request to the OpenWeatherMap API.
3. The API returns weather data in JSON format.
4. The system extracts the required weather variables.
5. The extracted data is normalized into a standard internal format.
6. The normalized weather data is combined with user preferences and predefined activity options.
7. The combined data is sent to the GPT-4o mini based decision agent.
8. GPT-4o mini analyzes the context and returns ranked activity recommendations with explanations.

Example normalized weather data:

```json
{
  "location": "Istanbul",
  "temperature": 18,
  "feels_like": 16,
  "condition": "rainy",
  "precipitation": 70,
  "wind_speed": 15,
  "humidity": 65,
  "timestamp": "2026-05-03 12:00"
}
```

---

## 3. Technologies and Frameworks

The main technologies planned for the project are:

**Python:** Main programming language.

**Streamlit:** Web interface for location input, user preferences, and recommendation output.

**Requests:** Sending HTTP requests to the weather API and retrieving weather data.

**Pandas:** Organizing and processing collected weather data if needed.

**JSON:** Storing normalized weather data, user preferences, and activity definitions.

**Python-dotenv:** Managing the weather API key and OpenAI API key through environment variables.

**OpenWeatherMap API:** Fetching real-time weather data.

**GPT-4o mini:** Analyzing weather data and user preferences, ranking activity options, and generating recommendation explanations.

The weather API key and OpenAI API key will be stored in a `.env` file and will not be written directly in the source code.

## 4. System Workflow

The system will follow a step-by-step workflow from user input to activity recommendation.

1. The user enters a location and personal preferences through the Streamlit interface.
2. The weather service fetches real-time weather data from the OpenWeatherMap API.
3. The raw API response is converted into a normalized weather data format.
4. The decision agent receives the normalized weather data, user preferences, and predefined activity options.
5. The GPT-4o mini based decision agent analyzes the weather conditions and user preferences.
6. The agent compares possible activities according to the given context.
7. GPT-4o mini ranks the most suitable activities.
8. The system returns the top recommendations with short explanations.

The general workflow is:

```text
User Location and Preferences
        ↓
Weather API Request
        ↓
Raw Weather Data
        ↓
Data Normalization
        ↓
GPT-4o Mini Based Decision Agent
        ↓
Activity Ranking and Reasoning
        ↓
Ranked Activity Recommendations
```

## 5. Team Member Responsibilities

### Deniz Özmen

- Designing the decision agent workflow
- Preparing the GPT-4o mini based decision prompt structure
- Implementing the activity recommendation logic
- Integrating the GPT-4o mini decision-making process
- Building the Streamlit user preference input section

### Ömer Şahin

- Implementing weather data fetching from the OpenWeatherMap API
- Normalizing raw weather API responses into the internal data format
- Preparing structured activity data in JSON format
- Connecting normalized weather data and activity data to the decision agent
- Building the Streamlit recommendation output section