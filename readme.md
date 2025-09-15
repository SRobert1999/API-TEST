# FastAPI Project

O aplicație FastAPI simplă cu endpoint-uri pentru gestionarea items.

## Descriere

Această aplicație oferă următoarele funcționalități:
- Endpoint de bază pentru salut (`/`)
- Citirea unui item specific (`/items/{item_id}`)
- Actualizarea unui item (`PUT /items/{item_id}`)

## Cerințe

- Python 3.7+
- pip (Python package installer)

## Instalare

### 1. Clonează repository-ul
```bash
git clone <url-repository>
cd <nume-folder>
```

### 2. Creează un virtual environment
```bash
# Windows
python -m venv fastapi_env

# macOS/Linux
python3 -m venv fastapi_env
```

### 3. Activează virtual environment-ul
```bash
# Windows
fastapi_env\Scripts\activate

# macOS/Linux
source fastapi_env/bin/activate
```

### 4. Instalează dependențele
```bash
pip install -r requirements.txt
```

## Executare

### Pornirea serverului de dezvoltare
```bash
uvicorn test:app --reload
```

Aplicația va fi disponibilă la: http://127.0.0.1:8000

### Pornirea cu parametri personalizați
```bash
# Specifică host și port
uvicorn test:app --host 0.0.0.0 --port 8080 --reload

# Pentru producție (fără --reload)
uvicorn test:app --host 0.0.0.0 --port 8000
```

## Testarea API-ului

### Endpoint-uri disponibile:

1. **GET /** - Salut simplu
   ```bash
   curl http://127.0.0.1:8000/
   ```

2. **GET /items/{item_id}** - Obține un item
   ```bash
   curl http://127.0.0.1:8000/items/1?q=test
   ```

3. **PUT /items/{item_id}** - Actualizează un item
   ```bash
   curl -X PUT "http://127.0.0.1:8000/items/1" \
        -H "Content-Type: application/json" \
        -d '{"name": "Laptop", "price": 1200.50, "is_offer": true}'
   ```

### Documentația automată

FastAPI generează automat documentația API:
- **Swagger UI**: http://127.0.0.1:8000/docs
- **ReDoc**: http://127.0.0.1:8000/redoc

## Structura proiectului

```
.
├── test.py              # Aplicația FastAPI principală
├── requirements.txt     # Dependențele Python
└── README.md           # Acest fișier
```

## Dezvoltare

### Adăugarea de noi dependențe
```bash
pip install nume_pachet
pip freeze > requirements.txt
```

### Dezactivarea virtual environment-ului
```bash
deactivate
```

## Model de date

### Item
```python
{
    "name": "string",      # Numele item-ului (default: "test")
    "price": "float",      # Prețul item-ului (obligatoriu)
    "is_offer": "boolean"  # Dacă este o ofertă (opțional)
}
```

## Exemple de răspunsuri

### GET /
```json
{
    "Hello": "World"
}
```

### GET /items/1?q=test
```json
{
    "item_id": 1,
    "q": "test"
}
```

### PUT /items/1
```json
{
    "item_name": "Laptop",
    "item_id": 1
}
```

## Troubleshooting

### Eroare: "uvicorn: command not found"
Asigură-te că virtual environment-ul este activat și că ai instalat dependențele.

### Eroare: "Port already in use"
Schimbă portul folosind: `uvicorn test:app --port 8001 --reload`

### Eroare de import
Verifică că te afli în directorul corect și că fișierul se numește `test.py`.

## Contribuții

1. Fork repository-ul
2. Creează o branch pentru feature (`git checkout -b feature/nume-feature`)
3. Commit modificările (`git commit -am 'Adaugă feature nou'`)
4. Push la branch (`git push origin feature/nume-feature`)
5. Creează un Pull Request