```mermaid
flowchart LR
    %% Актори
    Client((Клієнт))
    Admin((Адміністратор))
    GPS((GPS-трекер))

    %% Межа системи
    subgraph System [Мережа Каршерінгу]
        direction TB
        UC_Rent([Орендувати авто])
        UC_Promo([Застосувати промокод])
        UC_Auth([Пройти автентифікацію])
        UC_Fleet([Керувати автопарком])
        UC_Zones([Налаштувати паркувальні зони])
        UC_Telemetry([Передати телеметрію])
    end

    Client --> UC_Rent
    Admin --> UC_Fleet
    Admin --> UC_Zones
    GPS --> UC_Telemetry

    UC_Rent -. "«include»" .-> UC_Auth
    UC_Fleet -. "«include»" .-> UC_Auth
    UC_Zones -. "«include»" .-> UC_Auth
    UC_Promo -. "«extend»" .-> UC_Rent