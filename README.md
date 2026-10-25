# Wypożyczalnia filmów – REST API

Backend wypożyczalni filmów w **Node.js + Express** z bazą **MongoDB**. Obsługuje rejestrację i logowanie użytkowników (JWT), katalog filmów, wypożyczenia oraz recenzje.

> Projekt zespołowy zrealizowany w ramach studiów (Informatyka i Ekonometria, Uniwersytet Gdański).

## Funkcje

- 🔐 Rejestracja i logowanie – hasła hashowane bcryptem, autoryzacja tokenem JWT
- 🎬 Katalog filmów – przeglądanie i dodawanie
- 📼 Wypożyczenia – tworzenie i historia wypożyczeń użytkownika
- ⭐ Recenzje – ocena i komentarz do filmu, lista recenzji użytkownika
- 🛡️ Middleware chroniący endpointy wymagające logowania

## Endpointy

| Metoda | Ścieżka | Opis | Auth |
|---|---|---|:-:|
| `POST` | `/auth/signup` | Rejestracja | |
| `POST` | `/auth/login` | Logowanie, zwraca token JWT | |
| `GET` | `/movies` | Lista filmów | |
| `POST` | `/movies` | Dodanie filmu | 🔒 |
| `POST` | `/rentals` | Nowe wypożyczenie | 🔒 |
| `GET` | `/rentals/user/:userId` | Wypożyczenia użytkownika | 🔒 |
| `POST` | `/reviews` | Dodanie recenzji | 🔒 |
| `GET` | `/reviews/user/:userId` | Recenzje użytkownika | 🔒 |
| `GET` | `/users` | Lista użytkowników | 🔒 |

🔒 = wymaga nagłówka `Authorization: Bearer <token>`

### Przykład

```http
POST /auth/login
Content-Type: application/json

{ "email": "jan@example.com", "password": "haslo123" }
```

```json
{ "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..." }
```

## Struktura

```
api/
├── controllers/  # logika biznesowa
├── middleware/   # weryfikacja JWT
├── models/       # schematy Mongoose: User, Movie, Rental, Review
└── router/       # definicje tras
app.js            # konfiguracja Express i połączenie z bazą
server.js         # start serwera
```

## Technologie

**Node.js** · **Express** · **MongoDB + Mongoose** · **JWT** · **bcrypt** · **dotenv** · **morgan**

## Uruchomienie

```bash
npm install
cp .env.example .env   # uzupełnij MONGODB_URI i JWTkey
npm start              # http://localhost:3000
```
