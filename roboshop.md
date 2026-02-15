graph TD
    %% Tier 1: Web
    Client((User Browser)) --> Frontend[Frontend: Nginx]

    %% Tier 2: App Services
    subgraph "Application Services"
        Frontend --> Catalogue[Catalogue: Node.js]
        Frontend --> User[User: Node.js]
        Frontend --> Cart[Cart: Node.js]
        Cart --> Shipping[Shipping: Java]
        Shipping --> Payment[Payment: Python]
        Payment --> Dispatch[Dispatch: Go]
    end

    %% Tier 3: Databases & Middleware
    subgraph "Data & Messaging"
        Catalogue --> MongoDB[(MongoDB)]
        User --> MongoDB
        User --> Redis[(Redis Cache)]
        Cart --> Redis
        Shipping --> MySQL[(MySQL)]
        Payment --> RabbitMQ{RabbitMQ}
        Dispatch --> RabbitMQ
    end

    %% Styling
    style Frontend fill:#f9f,stroke:#333,stroke-width:2px
    style MongoDB fill:#4DB33D,color:#fff
    style MySQL fill:#00758F,color:#fff
    style Redis fill:#D82C20,color:#fff
    style RabbitMQ fill:#FF6600,color:#fff