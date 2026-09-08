# Tasty Food App

A simple Android recipe application built with **Kotlin** that fetches recipes from the Tasty API, stores them locally with Room, and shows list/detail screens.

## Features
- Fetches recipes from the Tasty API (RapidAPI)
- Displays recipes in a grid on the home screen
- Opens a details screen for each recipe
- Plays recipe video on the details screen
- Caches latest recipes in local Room database for offline viewing

## Tech Stack
- Kotlin
- MVVM Architecture
- Retrofit + Gson
- Room Database
- Android ViewModel + LiveData
- Coroutines
- RecyclerView + Glide

## Project Structure

```text
app/src/main/java/com/ajc/tasty
├── model
│   ├── local
│   └── remote
├── repository
├── ui
│   └── adapter
└── viewmodel
```

## Most Important Classes (Explained)

### `FoodMainScreen`
Main entry activity. It initializes Retrofit, Room, Repository, and ViewModel, loads API data when network is available, observes database data, and binds data to RecyclerView.

### `MainViewModel`
Acts as the UI-facing state holder. It triggers data loading through repository functions and exposes LiveData for the UI layer.

### `DataRepository`
Central data layer class. It fetches recipe data from `ApiService`, posts it to LiveData, and handles insert/read/delete operations in Room through `Dao`.

### `ApiService`
Retrofit interface describing the endpoint:
- `GET recipes/list`
- query params: `from`, `size`
- headers: RapidAPI host and key

### `Network`
Creates and provides a configured Retrofit instance with base URL `https://tasty.p.rapidapi.com/` and Gson converter.

### `FoodDatabase`
Room database singleton. Provides access to the app DAO and manages local storage lifecycle.

### `Dao`
Defines database operations:
- insert API data
- fetch all cached items as `LiveData<List<FoodEntity>>`
- clear existing cache

### `FoodEntity`
Room entity representing recipe data stored locally (name, image URL, description, language, preparation time, video URL).

### `Adapter` + `ViewHolder`
RecyclerView components that render recipe cards and handle row click events to open detail view.

### `FoodDetailsScreen`
Shows selected recipe details and plays recipe video using `VideoView`.

## Setup & Run

### 1) Clone repository
```bash
git clone https://github.com/shree-chougule/Tasty-Food-App.git
cd Tasty-Food-App
```

### 2) Open in Android Studio
- Open project root folder.
- Let Gradle sync complete.

### 3) Configure API key (recommended)
This project currently uses RapidAPI headers in repository code. Replace with your own key before running production/testing workloads.

### 4) Run app
- Use an emulator or physical device (API 26+)
- Click **Run** in Android Studio

## API Reference
- Tasty API: https://rapidapi.com/blog/tasty-api-with-java-python-php-ruby-javascript-examples/

## Screenshots
<img width="180" alt="Screenshot 2022-02-12 at 9 07 06 AM" src="https://user-images.githubusercontent.com/60433739/153708946-d7e836a6-4bcf-44d1-854b-c4d4e04a5030.png">

<img width="319" alt="Screenshot 2022-02-12 at 4 39 34 PM" src="https://user-images.githubusercontent.com/60433739/153708925-3c491363-b483-47eb-97f6-6d6ebb3a8f39.png">

<img width="319" alt="Screenshot 2022-02-12 at 4 33 15 PM" src="https://user-images.githubusercontent.com/60433739/153708932-ab72c2e3-fbd5-4f3d-a176-dc35be04197e.png">

## Demo Videos
- https://user-images.githubusercontent.com/60433739/153708630-41bdac60-5152-44aa-bdea-4e22cd6bd5b5.mov
- https://user-images.githubusercontent.com/60433739/153708684-4a5c0d94-dbe6-42ce-b6b9-5b10bd64afaf.mov
