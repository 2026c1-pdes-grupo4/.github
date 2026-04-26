# UNQ - PDES - 2026 c1
## Aplicación Compra tu Hogar (CTH)

### Enunciado
[doc](https://docs.google.com/document/d/1HdWZfd2t0L3aWw08RnvoGvPg9YEU4v5jv9J2NPIPwcg/edit?usp=sharing)

### Diagrama entidad relación

<!-- mermaid-sync -->
```mermaid
erDiagram
	direction LR
	USER {
		int user_id PK
		string username
		string email
		string password
		enum profile_type
	}

	AGENCY {
		int agency_id PK
		string username
		string email
        string password
		int admin_user_id FK
	}

	PROPERTY {
		int property_id PK
		enum property_type
		string address
		string city
		string province
		float area_sq
		int rooms
		string description
		bool available
		string circunscripcion
		string seccion
		string manzana
		string parcela
	}

	AGENCY_PROPERTY {
        int agency_property_id PK
        int agency_id FK
        int property_id FK
        date listed_date
        float listed_price
    }

	PICTURE {
		int picture_id PK
		int agency_property_id FK
		string url
	}

	FAVORITE {
		int favorite_id PK
		int user_id FK
		int property_id FK
		date saved_date
		float saved_price
		int score
		string comment
	}

	PURCHASE {
		int purchase_id PK
		int user_id FK
		int agency_property_id FK
		float purchase_price
		date purchase_date
	}

	USER||--o{AGENCY:"lists"
    USER||--o{AGENCY_PROPERTY:"searches"
	USER||--o{FAVORITE:"saves"
	USER||--o{PURCHASE:"makes"
    AGENCY||--o{AGENCY_PROPERTY:"lists through"
    PROPERTY||--o{AGENCY_PROPERTY:"appears in"
	AGENCY_PROPERTY||--o{FAVORITE:"appears in"
	AGENCY_PROPERTY||--o|PURCHASE:"acquired in"
	AGENCY_PROPERTY||--o{PICTURE:"has"

```
<!-- /mermaid-sync -->

### Integrantes
- Juan Hualampa
- Sofia Justiniano

