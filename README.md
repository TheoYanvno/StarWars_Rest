# Star Wars REST API

A REST API built with **Python, Flask and SQLAlchemy** for a Star Wars blog. Users can save favorite characters and planets.

**Tech:** Python · Flask · SQLAlchemy ORM · Flask-Migrate · PostgreSQL / SQLite · Flask-Admin

## Data model

Four SQLAlchemy model classes ([`src/models.py`](src/models.py)) with foreign-key relationships:

- `User` — email, password, active flag
- `Character` and `Planet` — name and description
- `Favorites` — links a user to a favorite character or planet (`USER_ID`, `FAV_CHARACTER_ID`, `FAV_PLANET_ID`)

## Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | `/user` | Create a user |
| GET | `/user` | List users |
| GET | `/user/favorites` | List favorites |
| POST | `/favorites/planets/<planet_id>` | Add a favorite planet (`{ "user_id": 1 }`) |
| POST | `/favorites/character/<character_id>` | Add a favorite character |
| DELETE | `/user/<user_id>/favorites/planets/<planet_id>` | Remove a favorite planet |
| DELETE | `/user/<user_id>/favorites/characters/<character_id>` | Remove a favorite character |

## Run it

```bash
pipenv install
pipenv run migrate && pipenv run upgrade   # create tables
pipenv run start                          # http://localhost:3000
```

Set `DATABASE_URL` to use PostgreSQL; without it the app uses SQLite. An admin panel is available at `/admin`.

Built as part of the 4Geeks Academy Full Stack Software Development program (2023), starting from the academy's Flask boilerplate (original notes in [`docs/BOILERPLATE_README.md`](docs/BOILERPLATE_README.md)).
