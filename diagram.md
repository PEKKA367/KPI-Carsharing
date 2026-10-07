erDiagram
    Client {
    uuid id PK
    string phone
    string email
    string license_number
    string registration_date
    }

    Vehicle {
        uuid id PK
        string license_plate
        string model
        float fuel_level
        string status
    }

    ParkingZone {
        uuid id PK
        string location_name
        int max_capacity
    }

    RentalSession {
        uuid id PK
        datetime start_time
        datetime end_time
        float total_price
    }

    Client ||--o{ RentalSession : "здійснює"
    Vehicle ||--o{ RentalSession : "учащає_в"
    ParkingZone ||--o{ Vehicle : "містить"