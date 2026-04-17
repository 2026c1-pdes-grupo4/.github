# UNQ - PDES - 2026 c1
## Aplicación Compra tu Hogar (CTH)

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
        float price
        string address
        string city
        string province
        float area_sq
        int rooms
        string description
        bool available
    }

    AGENCY_PROPERTY {
        int agency_property_id PK
        int agency_id FK
        int property_id FK
        date listed_date
        float listed_price
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
        int property_id FK
        float purchase_price
        date purchase_date
    }

    USER||--o{AGENCY:"lists"
    USER||--o{PROPERTY:"searches"
    USER||--o{FAVORITE:"saves"
    USER||--o{PURCHASE:"makes"
    AGENCY||--o{AGENCY_PROPERTY:"lists through"
    PROPERTY||--o{AGENCY_PROPERTY:"appears in"
    PROPERTY||--o{FAVORITE:"appears in"
    PROPERTY||--o|PURCHASE:"acquired in"

