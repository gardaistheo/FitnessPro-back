# Feature [nom]

## Description
Permet de manipuler des exercices de musculation (CRUD complet)

## Endpoints

### **Base URL** : `/api/exercices`

### POST /api/exercices
**Auth** : `auth:sanctum`
**Rôle** : `coach`

**Body** (exemple)
```json
{
    "nom" : "Pompes",
    "muscles" : [
        "avant-bras",
        "biceps",
        "triceps",
        "épaules",
        "pecs",
        "grands dorcaux",
        "abdos"
    ],
    "niveau" : "débutant",
    "instructions" : [
        "1 - Placez vos mains à plat sur le sol, légèrement plus larges que la largeur des épaules.",
        "2 - Étendez vos jambes derrière vous, en appui sur les orteils, de manière à former une ligne droite de la tête aux talons.",
        "3 - Abaissez votre corps en pliant les coudes jusqu'à ce que votre poitrine touche presque le sol.",
        "4 - Poussez à travers vos mains pour revenir à la position de départ."
    ],
    "video_url" : "https://www.youtube.com/watch?v=...",
    "image_url" : "http://s3.amazonaws.com/image_pompes/"
}
```

**Response** `201`
```json
{
    "id" : "i28dhzEZA242",
    "nom" : "Pompes",
    "muscles" : [
        "avant-bras",
        "biceps",
        "triceps",
        "épaules",
        "pecs",
        "grands dorcaux",
        "abdos"
    ],
    "niveau" : "débutant",
    "instructions" : [
        "1 - Placez vos mains à plat sur le sol, légèrement plus larges que la largeur des épaules.",
        "2 - Étendez vos jambes derrière vous, en appui sur les orteils, de manière à former une ligne droite de la tête aux talons.",
        "3 - Abaissez votre corps en pliant les coudes jusqu'à ce que votre poitrine touche presque le sol.",
        "4 - Poussez à travers vos mains pour revenir à la position de départ."
    ],
    "video_url" : "https://www.youtube.com/watch?v=...",
    "image_url" : "http://s3.amazonaws.com/image_pompes/",
    "created_at" : "2023-01-01T00:00:00Z",
    "updated_at" : "2023-01-01T00:00:00Z",
    "updated_by" : "user_id"
}
```

**Erreurs**
| Code | Cas |
|------|-----|
| 401  | Non authentifié (token manquant/invalide/expiré) |
| 403  | Authentifié mais pas le bon rôle |
| 422  | Validation échouée (type invalide, valeur hors enum pour niveau...) |
| 500  | Server Error / BDD inaccessible |

### GET /api/exercices
**Auth** : `auth:sanctum`

**Response** `200`
```json
{
    "exercices" : [
        {
            "id" : "i28dhzEZA242",
            "nom" : "Pompes",
            "muscles" : [
                "avant-bras",
                "biceps",
                "triceps",
                "épaules",
                "pecs",
                "grands dorcaux",
                "abdos"
            ],
            "niveau" : "débutant",
            "instructions" : [
                "1 - Placez vos mains à plat sur le sol, légèrement plus larges que la largeur des épaules.",
                "2 - Étendez vos jambes derrière vous, en appui sur les orteils, de manière à former une ligne droite de la tête aux talons.",
                "3 - Abaissez votre corps en pliant les coudes jusqu'à ce que votre poitrine touche presque le sol.",
                "4 - Poussez à travers vos mains pour revenir à la position de départ."
            ],
            "video_url" : "https://www.youtube.com/watch?v=...",
            "image_url" : "http://s3.amazonaws.com/image_pompes/",
            "created_at" : "2023-01-01T00:00:00Z",
            "updated_at" : "2023-01-01T00:00:00Z",
            "updated_by" : "user_id"
        },
        {
            "nom" : "autre",
            "muscles" : [
                "autre",
                "autre",
            ],
            "niveau" : "débutant",
            "instructions" : [
                "1 - ...", 
                "2 - ...",
                "3 - ..."
            ],
            "video_url" : "https://www.youtube.com/watch?v=...",
            "image_url" : "http://s3.amazonaws.com/image_autre/",
            "created_at" : "2023-01-01T00:00:00Z",
            "updated_at" : "2023-01-01T00:00:00Z",
            "updated_by" : "user_id"
        },
        {
            "..."
        },
    ]
}
```

**Response** `200` but empty
```json
{
    "exercices" : []
}
```

**Erreurs**
| Code | Cas |
|------|-----|
| 401  | Non authentifié (token manquant/invalide/expiré) |
| 500  | Server Error / BDD inaccessible|

### GET /api/exercices/{id}
**Auth** : `auth:sanctum`
**id** : string (ex: "i28dhzEZA242")

**Response** `200`
```json
{
    "exercices" : "Pompes",
    "muscles" : [
        "avant-bras",
        "biceps",
        "triceps",
        "épaules",
        "pecs",
        "grands dorcaux",
        "abdos"
    ],
    "niveau" : "débutant",
    "instructions" : [
        "1 - ...",
        "2 - ...",
        "3 - ...",
        "4 - ..."
    ],
    "video_url" : "https://www.youtube.com/watch?v=...",
    "image_url" : "http://s3.amazonaws.com/image_pompes/",
    "created_at" : "2023-01-01T00:00:00Z",
    "updated_at" : "2023-01-01T00:00:00Z",
    "updated_by" : "user_id"
}
```
**Erreurs**
| Code | Cas |
|------|-----|
| 401  | Non authentifié (token manquant/invalide/expiré) |
| 500  | Server Error / BDD inaccessible|

### PATCH /api/exercices/{id}
**Auth** : `auth:sanctum`
**Rôle** : `coach`
**id** : string (ex: "i28dhzEZA242")

**Body** (exemple)
```json
{
    "nom" : "Pompes_modifié",
    "muscles" : [
        "avant-bras_modifié",
        "biceps",
        "triceps",
        "épaules",
        "pecs",
        "grands dorcaux",
        "abdos"
    ],
    "niveau" : "intermédiaire",
    "instructions" : "1 - ..., 2 - ..., 3 - ..., 4 - ..._modifié",
    "video_url" : "https://www.youtube.com/watch?v=..._modifié"
}
```

**Response** `200`
```json
{
    "id" : "i28dhzEZA242",
    "nom" : "Pompes_modifié",
    "muscles" : [
        "avant-bras_modifié",
        "biceps",
        "triceps",
        "épaules",
        "pecs",
        "grands dorcaux",
        "abdos"
    ],
    "niveau" : "intermédiaire",
    "instructions" : "1 - ..., 2 - ..., 3 - ..., 4 - ..._modifié",
    "video_url" : "https://www.youtube.com/watch?v=..._modifié",
    "image_url" : "http://s3.amazonaws.com/image_pompes/",
    "created_at" : "2023-01-01T00:00:00Z",
    "updated_at" : "2023-01-01T00:00:00Z",
    "updated_by" : "user_id"
}
```
**Erreurs**
| Code | Cas |
|------|-----|
| 401  | Non authentifié (token manquant/invalide/expiré) |
| 403  | Authentifié mais pas le bon rôle |
| 404  | Exercice non trouvé |
| 422  | Validation échouée (type invalide, valeur hors enum pour niveau...) |
| 500  | Server Error / BDD inaccessible |


### DELETE /api/exercices/{id}
**Auth** : `auth:sanctum`
**Rôle** : `coach` & `admin`
**id** : string (ex: "i28dhzEZA242")

**Response** `204` (No Content)

**Erreurs**
| Code | Cas |
|------|-----|
| 401  | Non authentifié (token manquant/invalide/expiré) |
| 403  | Authentifié mais pas le bon rôle |
| 404  | Exercice non trouvé |
| 500  | Server Error / BDD inaccessible |

## Modèle de données

| Champ | Type | Contraintes | Description | Required |
|-------|------|-------------|-------------|----------|
| id    | string | PK, auto | Identifiant unique de l'exercice | true |
| nom   | string |             | Nom de l'exercice | true |
| muscles | array  |             | Liste des muscles sollicités | true |
| niveau | string | enum: débutant, intermédiaire, avancé | Niveau de difficulté de l'exercice | true |
| instructions | array |             | Instructions détaillées pour réaliser l'exercice | true |
| video_url | string |             | URL de la vidéo démonstrative | true |
| image_url | string |             | URL de l'image de l'exercice | true |
| created_at | timestamp |             | Date de création de l'exercice | true |
| updated_at | timestamp |             | Date de mise à jour de l'exercice | true |
| updated_by | string | FK (User)     | Identifiant de l'utilisateur ayant effectué la mise à jour | true |

## Règles métier
- Seul un coach ou admin peut créer/modifier un exercice.
- Un exercice ne peut pas être supprimé s'il est utilisé dans un programme actif.

## Relations
- Exercice belongsToMany Programme (via programme_exercice)
- Exercice belongsTo User (updated_by)
