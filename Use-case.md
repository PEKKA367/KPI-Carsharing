flowchart LR
%% Актори (винесені за межі системи)
Client((Клієнт))
Admin((Адміністратор))
GPS((GPS-трекер))

    %% Межа системи (System Boundary)
    subgraph System [Мережа Каршерінгу]
        direction TB
        
        %% Варіанти використання (Потреби акторів)
        UC_Rent([Орендувати авто])
        UC_Promo([Застосувати промокод])
        UC_Auth([Пройти автентифікацію])
        
        UC_Fleet([Керувати автопарком])
        UC_Zones([Налаштувати паркувальні зони])
        
        UC_Telemetry([Передати телеметрію])
    end

    %% Базові зв'язки акторів із варіантами використання
    Client --> UC_Rent
    Admin --> UC_Fleet
    Admin --> UC_Zones
    GPS --> UC_Telemetry

    %% Зв'язки include (обов'язкові підкроки)
    %% Стрілка йде ВІД базового прецеденту ДО обов'язкового кроку
    UC_Rent -. "«include»" .-> UC_Auth
    UC_Fleet -. "«include»" .-> UC_Auth
    UC_Zones -. "«include»" .-> UC_Auth

    %% Зв'язки extend (опціональні розширення)
    %% Стрілка йде ВІД опціонального кроку ДО базового прецеденту (правило UML)
    UC_Promo -. "«extend»" .-> UC_Rent
