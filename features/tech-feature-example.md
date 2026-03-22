# Feature [nom]

## Description
[Ce que la feature fait en 1-2 phrases]

## Endpoints

### [MÉTHODE] /api/[route]
**Auth** : Public / `auth:sanctum` / rôle `___`

**Request**
```json
{}
```
**Response** `200`
```json
{}
```
**Erreurs**
| Code | Cas |
|------|-----|
| 422  | Validation échouée |
| 404  | Ressource introuvable |

*(Dupliquer ce bloc par endpoint)*

## Modèle de données

| Champ | Type | Contraintes |
|-------|------|-------------|
| id    | string | PK, auto |
|       |      |             |

## Règles métier
-

## Relations
- [Entité] hasMany / belongsTo [Entité]
