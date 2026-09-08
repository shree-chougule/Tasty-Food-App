# 🍽️ Tasty Food App

> A Kotlin Android app inspired by the Tasty experience, built using clean MVVM layers with API + local caching.

## ✨ Overview
**Tasty Food App** fetches recipes from the Tasty API, stores them in Room, and shows a smooth list-to-details experience with video playback.

## 🎯 Clone Tasty App Goal
Recreate a Tasty-like recipe browsing experience inspired by the official app:
- Play Store: https://play.google.com/store/apps/details?id=com.buzzfeed.tasty

## 🧱 Required Architecture & Tools
As requested for this project:
- MVVM
- Room
- Retrofit
- Dagger/Hilt
- Coroutines
- Fragments
- Constraint Layout
- Relative Layout

### Current project implementation snapshot
- ✅ MVVM, Room, Retrofit, Coroutines, Constraint Layout, Relative Layout
- ⚠️ Dagger/Hilt and Fragments are target requirements to integrate/expand further

## 🚀 Features
- Recipe list from Tasty API
- Local cache for recipe data using Room
- Recipe details screen with video playback
- RecyclerView grid UI with image loading via Glide

## 🧰 Tech Stack
- **Language:** Kotlin
- **Architecture:** MVVM
- **Networking:** Retrofit + Gson
- **Local Storage:** Room
- **Async:** Coroutines
- **UI:** RecyclerView, ConstraintLayout, RelativeLayout
- **Image Loading:** Glide

## 📂 Project Structure
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

## 🧠 Important Highlighted Classes (with explanation)

| Class | Responsibility | Why it is important |
|---|---|---|
| `FoodMainScreen` | Entry activity, initializes DB/API/ViewModel, observes data, binds RecyclerView | Main orchestration point where app flow starts |
| `MainViewModel` | Triggers data fetch and exposes observable data to UI | Keeps UI logic separate from data layer (MVVM core) |
| `DataRepository` | Handles remote fetch + local DB operations | Single source of data access between ViewModel and data sources |
| `ApiService` | Defines Retrofit endpoint (`recipes/list`) and request params/headers | Contract for all remote API communication |
| `Network` | Creates Retrofit singleton instance | Centralized network client configuration |
| `FoodDatabase` | Room database singleton provider | Persistent local storage entry point |
| `Dao` | Insert/read/delete operations for cached recipes | Encapsulates SQL operations in clean interfaces |
| `FoodEntity` | Local Room table model for recipe fields | Defines exactly what recipe data is cached |
| `Adapter` + `ViewHolder` | Renders recipe cards and click handling | Connects model data to visual list UI |
| `FoodDetailsScreen` | Displays selected recipe details and plays video | Final user consumption screen for each recipe |

## ▶️ Demo
Use the play button to watch demos directly from README.

<video src="https://user-images.githubusercontent.com/60433739/153708630-41bdac60-5152-44aa-bdea-4e22cd6bd5b5.mov" controls width="700"></video>

<video src="https://user-images.githubusercontent.com/60433739/153708684-4a5c0d94-dbe6-42ce-b6b9-5b10bd64afaf.mov" controls width="700"></video>

## 🖼️ Screenshots
<p>
  <img width="250" alt="Home Screen" src="https://user-images.githubusercontent.com/60433739/153708946-d7e836a6-4bcf-44d1-854b-c4d4e04a5030.png">
  <img width="250" alt="Recipe List Screen" src="https://user-images.githubusercontent.com/60433739/153708925-3c491363-b483-47eb-97f6-6d6ebb3a8f39.png">
  <img width="250" alt="Recipe Details Screen" src="https://user-images.githubusercontent.com/60433739/153708932-ab72c2e3-fbd5-4f3d-a176-dc35be04197e.png">
</p>

## ⚙️ Setup & Run
1. Clone repository
```bash
git clone https://github.com/shree-chougule/Tasty-Food-App.git
cd Tasty-Food-App
```

2. Open project in Android Studio and allow Gradle sync.
3. Add your RapidAPI key for Tasty API where required.
4. Run on emulator/device (API 26+).

## 🔗 Food APIs Reference
- Tasty API: https://rapidapi.com/blog/tasty-api-with-java-python-php-ruby-javascript-examples/
- Spoonacular: https://spoonacular.com/food-api
- TheMealDB: https://www.themealdb.com/api.php
- The API Collective (Food & Drink): https://the-api-collective.com/category/food-and-drink
- Edamam Recipe API: https://developer.edamam.com/edamam-docs-recipe-api

## 📚 Extra References for Tasty-style apps
- Official Tasty website: https://tasty.co
- BuzzFeed Tasty YouTube: https://www.youtube.com/c/buzzfeedtasty

---
If you want, this README can also be extended with installation screenshots, architecture diagram, and contribution guidelines.
