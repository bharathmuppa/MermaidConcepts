# MermaidConcepts


```mermaid
graph LR

subgraph User
    UA[User Application]
    style UA fill:#f9f, stroke:#333, stroke-width:2px
end

subgraph Identity Provider (IdP)
    IdP[Identity Provider]
    UserStore[User Store]
    style IdP fill:#f9f, stroke:#333, stroke-width:2px
    style UserStore fill:#f9f, stroke:#333, stroke-width:2px
end

subgraph Service Provider (SP)
    SP[Service Provider]
    App[Application]
    RS[Resource Server]
    style SP fill:#f9f, stroke:#333, stroke-width:2px
    style App fill:#f9f, stroke:#333, stroke-width:2px
    style RS fill:#f9f, stroke:#333, stroke-width:2px
end

subgraph Federated Identity Provider (FIdP)
    FIdP[Federated Identity Provider]
    style FIdP fill:#f9f, stroke:#333, stroke-width:2px
end

subgraph Metadata Exchange
    IdP -- Metadata --> SP
    FIdP -- Metadata --> SP
end

subgraph Single Logout
    IdP -- Logout Request --> SP
    SP -- Logout Response --> IdP
end

UA -- SAML Request --> IdP
IdP -- SAML Response --> UA
UA -- SAML Assertion --> SP
SP -- Resource Request --> RS
RS -- Resource Response --> SP
UA -- SAML Logout Request --> IdP
IdP -- SAML Logout Response --> UA

style subgraph fill:#eee, stroke:#333, stroke-width:2px
```