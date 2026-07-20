# Gold Palm Hotel — Reservation System

A full-stack hotel reservation and management platform built with **Spring Boot**. It covers the full guest booking journey (search, book, pay, review) as well as staff-side tools for admins and receptionists (room, booking, promotion, and review management), plus an integrated booking chatbot.

## Features

- **Guest-facing**
  - Room browsing, availability search, and booking
  - Custom payment flow with confirmation emails and QR-code tickets
  - Promotions / discount codes
  - Reviews and ratings
  - Chat assistant for booking help
- **Staff-facing**
  - Admin dashboard: rooms, bookings, staff, promotions, reviews
  - Receptionist dashboard for front-desk operations
  - Role-based authentication (Admin / Receptionist / Customer) via Spring Security

## Tech Stack

| Layer           | Technology                                                             |
| --------------- | ---------------------------------------------------------------------- |
| Backend         | Java 24, Spring Boot 3.5.4 (Web, Security, Data JPA, Mail, Validation) |
| Views           | Thymeleaf                                                              |
| Database        | MySQL                                                                  |
| Build           | Maven                                                                  |
| Extras          | ZXing (QR codes), Jackson                                              |
| Chatbot service | Python (FastAPI) — see `chatbot_service.py` / `requirements.txt`       |

## Prerequisites

- Java 24 (JDK)
- Maven (or use the bundled `./mvnw`)
- MySQL Server running locally (or reachable)
- (Optional, for the chatbot service) Python 3.10+

## Setup

1. **Clone the repo**

   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. **Run the application**

   ```bash
   ./mvnw spring-boot:run
   ```

   The app will be available at `http://localhost:8080`.

3. **(Optional) Run the chatbot service**
   ```bash
   pip install -r requirements.txt
   python chatbot_service.py
   ```

## Project Structure

```
src/main/java/.../hotelreservationsystem/
├── controller/     # REST + MVC controllers (booking, payment, admin, auth, etc.)
├── service/        # Business logic
├── repository/     # Spring Data JPA repositories
├── model/          # JPA entities and enums
├── dto/            # Request/response data transfer objects
├── config/         # Security, web, and data-init configuration
└── util/           # Helpers (QR code generation, password utilities)
src/main/resources/
├── templates/       # Thymeleaf views
├── static/          # CSS, JS, images
└── application.properties.example
```

## Security Notes

- Real credentials are **never** committed — `application.properties` is git-ignored; use `application.properties.example` as a template.
- If you're picking up this project from an earlier version where credentials were committed to git history, **rotate them** (change the DB password, regenerate the Gmail App Password) since old commits may still contain them even after removal from the latest version.

## Team

Built as a team project by PG122.

## License

Add a license of your choice (e.g. MIT) if you intend to make this repository public.
