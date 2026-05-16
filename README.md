# Namma-Mela# 🎭 Namma-Mela (National Pride) — Drama Company Digital Box-Office

**Namma-Mela** is a dedicated Android application built using Generative AI principles to digitize the traditional rural theater ecosystem (*Company Nataka*). In rural India, village *Melas* (fairs) host highly popular drama troupes. However, due to the lack of an organized booking or communication channel, rural fans often travel up to 50km only to discover that premium seats (like the "Front Row") are sold out or that their favorite artist is not performing tonight.

This application acts as a digital box-office, bringing formal structure, modern data management, and a bold theatrical UI to an unorganized cultural art sector, ensuring our traditional art forms thrive in the digital age.

---

## 🚀 Key Features & User Flow

1. **Tonight's Play (The Marquee)**
   * **Visual Poster:** Features a bold digital poster of the daily play, loaded dynamic and efficiently using **Glide**.
   * **Details:** Clear metadata showing the Play Name, Duration, and specific showtimes.
   * **Manager Portal:** A lightweight, password-protected configuration layer that allows the theater manager to update the play details on the fly.

2. **Cast List (The Green Room)**
   * Displays the scheduled cast profile pictures and designations.
   * Highlights specific performing profiles crucial for rural audiences: the **Lead Actor**, the **Comedian**, and the **Singer**.

3. **Interactive Seat Map (The Pit)**
   * Displays a grid-based, visual row-and-column layout of the tent theater theater.
   * Dynamically tracks seat availability state (`AVAILABLE`, `SELECTED`, `RESERVED`).
   * Clicking an available seat toggles its state and securely saves the choice.

4. **Fan Wall (The Applause)**
   * A digital guestbook where audience members can type feedback and leave interactive "Applause" (virtual claps) for specific performers, reinforcing community entertainment.

---

## 🛠 Tech Stack & Engineering Architecture

The application is structured following clean architecture guidelines with an **MVVM (Model-View-ViewModel)** structural pattern:

* **UI Engine:** XML layouts using `GridLayoutManager` for the seat matrix, styled with high-contrast theatrical elements.
* **Persistent Storage (Room DB):** Android Room serves as the local single source of truth. It tracks seat bookings across application lifecycles and caches manager configurations for offline operations (highly critical for remote/spotty network areas).
* **Asynchronous Flow:** Kotlin Coroutines & `LiveData` / `StateFlow` ensure that as soon as a database write happens, the user interface updates reactively without a full page refresh.
* **Media Handling:** **Glide** caching and processing pipelines for asynchronous image loading of cast headshots and banners.

---

## 🗄 Database Schema Design

### 1. Seat Entity (`seat_table`)
| Column Name | Data Type | Primary Key | Description |
| :--- | :--- | :--- | :--- |
| `seatId` | Integer | Yes | Unique seat configuration string (e.g., Row index + Number) |
| `rowLabel` | String | No | Row designation (e.g., "Row A", "Front Row") |
| `seatNumber` | Integer | No | Individual seat index within row |
| `isReserved` | Boolean | No | Check flag for reservation state (`true` / `false`) |

### 2. Play Configuration Entity (`play_table`)
| Column Name | Data Type | Primary Key | Description |
| :--- | :--- | :--- | :--- |
| `id` | Integer | Yes | Unique ID (usually single row system `id = 1`) |
| `title` | String | No | Title of tonight's play |
| `duration` | String | No | Total running duration (e.g., "3 Hours") |
| `posterUrl` | String | No | Live web link or resource path for the banner graphic |

---

## 🎨 UI & UX Design Language
To match the success criteria of a **Bold & Theatrical** application, the visual language departs completely from standard flat, corporate web styles:
* **Primary Color Scheme:** Deep Velvet Crimson Red (`#8B0000`), Charcoal/Pitch Black (`#121212`), and Metallic Gold (`#FFD700`).
* **Visual Components:** Round elevation card-views, bold drop shadows mimicking theater bills, and custom icon assets (e.g., 👏 for submit, 💺 for seating layouts).

---

## 🧬 GenAI Implementation in Development
This repository incorporates Generative AI tools within its engineering cycle:
1. **Asset Generation:** Used generative diffusion models to synthesize authentic-looking classic play banners and cast portraits to build out the high-fidelity demo environment.
2. **Boilerplate Synthesis:** Used Large Language Models to accelerate the generation of type-safe Room Database setups, boilerplate DAO interfaces, and complex SQL relational queries.
3. **Localization Optimization:** Leveraged LLM translation utilities to natively map out text strings to local languages (e.g., Kannada, Telugu), matching the localized project title "*Namma-Mela*" (Our Fair).

---

## 📊 Success Criteria Verification Checklist
* [ ] **Reactive Seat Map:** Modifying an `isReserved` status inside the Database updates the `RecyclerView` color profile seamlessly via LiveData/Flow observation without layout blinking.
* [ ] **Manager Customization:** Updating values within `play_table` immediately changes the banner artwork, duration strings, and names across all consumer devices.
* [ ] **High-Contrast UI:** No generic white or system grey themes; standardizing dark theatrical high-contrast view styling.

---
*Developed as a step towards digitizing traditional cultural economies and ensuring rural communities have access to organized arts.*
