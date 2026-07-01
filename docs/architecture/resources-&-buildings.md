```mermaid
stateDiagram-v2
    direction LR

    state "Tier 1" as Tier1 {
	    state Raw{
		    Flax
	        Meat
	        Grain
	        Wood
	    }
        
        state Extracted{
	        IronOre
	        Coal
	        Salt
	        Gold
	        Stone
        }
        
    }

    state "Tier 2" as Tier2 {
        Textiles
        SeasonedFood
        Beer
        Iron
        Jewelry
    }

    state "Tier 3" as Tier3 {
        Weapons
        Tools
    }
    
    state "Tier 4" as Tier4 {
        Jewelry
    }

    %% Production Flows (Transitions)
    Flax --> Textiles
    
    Meat --> SeasonedFood
    Salt --> SeasonedFood
    
    Grain --> Beer
    
    IronOre --> Iron
    Coal --> Iron
    
    Gold --> Jewelry
    Tools --> Jewelry

    Iron --> Weapons
    Wood --> Tools
    Iron --> Tools


```









```mermaid
stateDiagram-v2
    direction TB

    state "Pop: 0 - 20" as P20
    note right of P20
        • Grain: 1.0
        • Wood: 0.5
    end note

    state "Pop: 21 - 40" as P40
    note right of P40
        • Meat: 0.5
        • Textilies: 0.5
    end note

    state "Pop: 41 - 60" as P60
    note right of P60
        • Tools: 0.1
        • Beer: 0.5
    end note

    state "Pop: 61 - 80" as P80
    note right of P80
        • SeasonedFood: 0.2
    end note

    state "Pop: 81 - 100" as P100
    note right of P100
        • Culture: 0.1
    end note

    state "Pop: 100+" as P100+
    note right of P100+
        • Jewelery: 0.1
    end note

    %% Transakcje i warunki wzrostu
    [*] --> P20
    P20 --> P40 
    P40 --> P60 
    P60 --> P80 
    P80 --> P100 
    P100 --> P100+ 
```

```mermaid
flowchart TD
    %% Definicja stylów dla węzłów
    classDef t1Node fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#000
    classDef t2Node fill:#eeeeee,stroke:#616161,stroke-width:2px,color:#000
    classDef t3Node fill:#fff3e0,stroke:#e65100,stroke-width:2px,color:#000

    subgraph Tier1 ["TIER 1(Cost: Wood)"]
        direction TB
        %% Core Infrastructure
        TownCenter1[Village Center]:::t1Node
        Housing1[Wooden Huts]:::t1Node
        Storage1[Small Stockpile]:::t1Node
        Outpost1[Watchtower]:::t1Node
        
        %% Resource Gatherers
        Lumberjack1[Lumbercamp]:::t1Node
        Farm1[Crop Fields]:::t1Node
        Pasture1[Livestock Pen]:::t1Node
        Quarry1[Stone Pit]:::t1Node
        Weaver1[Spinning Wheel]:::t1Node
    end

    subgraph Tier2 ["TIER 2(Cost: Wood + Stone)"]
        direction TB
        %% Core Infrastructure
        TownCenter2[Town Hall]:::t2Node
        Housing2[Stone Houses]:::t2Node
        Storage2[Warehouse]:::t2Node
        Market2[Market Square]:::t2Node
        Outpost2[Stone Keep]:::t2Node
        
        %% Advanced Production & New Gatherers
        Mine1[Basic Mine]:::t2Node
        Smelter1[Bloomery/Smelter]:::t2Node
        Brewery1[Brewery]:::t2Node
        Smokehouse1[Smokehouse]:::t2Node
        Weaver2[Textile Workshop]:::t2Node
    end

    subgraph Tier3 ["TIER 3(Cost: Wood + Stone + Tools)"]
        direction TB
        %% Core Infrastructure
        TownCenter3[City Council]:::t3Node
        Housing3[Multi-story Estates]:::t3Node
        Storage3[Grand Vault]:::t3Node
        Market3[Trade Hub]:::t3Node
        Outpost3[Fortress]:::t3Node
        Culture1[Culture Center]:::t3Node
        
        %% End-game Production
        Mine2[Deep Shaft Mine]:::t3Node
        Smelter2[Blast Furnace]:::t3Node
        Blacksmith1[Blacksmith/Armory]:::t3Node
        Jeweler1[Jeweler]:::t3Node
    end

    %% UPGRADE PATHS (Logical progressions)
    
    %% Core Upgrades
    TownCenter1 -.->|Upgrade| TownCenter2
    TownCenter2 -.->|Upgrade| TownCenter3
    
    Housing1 -.->|Upgrade| Housing2
    Housing2 -.->|Upgrade| Housing3
    
    Storage1 -.->|Upgrade| Storage2
    Storage2 -.->|Upgrade| Storage3
    
    Outpost1 -.->|Upgrade| Outpost2
    Outpost2 -.->|Upgrade| Outpost3
    
    %% Market appears in T2, upgrades in T3
    Market2 -.->|Upgrade| Market3

    %% Production Upgrades (Only when mechanically logical)
    Weaver1 -.->|Upgrade| Weaver2
    Mine1 -.->|Upgrade| Mine2
    Smelter1 -.->|Upgrade| Smelter2
    
    %% Implicit Rules (No direct lines needed, but conceptually true)
    %% Lumbercamp, Farm, Pasture, Quarry stay as T1 base structures. 
    %% You build more of them rather than upgrading a "Farm Level 3".
    
    %% New buildings introduced in specific Tiers
    %% Brewery, Smokehouse introduced in T2 (No upgrades needed)
    %% Blacksmith, Jeweler, Culture Center introduced in T3

    %% Style dla teł Tierów (Paski poziome)
    style Tier1 fill:#f1f8e9,stroke:#33691e,stroke-width:2px,stroke-dasharray: 5 5
    style Tier2 fill:#fafafa,stroke:#424242,stroke-width:2px,stroke-dasharray: 5 5
    style Tier3 fill:#fff8e1,stroke:#ff6f00,stroke-width:2px,stroke-dasharray: 5 5
```

Handel
Osady maj




| **Name               | **Wood** | **Stone** | **Tools** | Worker Capacity | **Production** |
| :------------------- | :------: | :-------: | :-------: | --------------- | -------------- |
| **Village Center**   |          |           |     -     | -               |                |
| **Town Hall**        |          |           |     -     | -               |                |
| **City Council**     |          |           |           | -               |                |
| **Huts**             |          |     -     |     -     | -               |                |
| **Hause**            |          |           |     -     | -               |                |
| **Estate**           |          |           |           | -               |                |
| **Stockpile**        |          |     -     |     -     | -               |                |
| **Warehouse**        |          |           |     -     | -               |                |
| **Vault**            |          |           |           | -               |                |
| **Market**           |          |           |     -     |                 |                |
| **Trade Hub**        |          |           |           |                 |                |
| **Watchtower**       |          |     -     |     -     |                 |                |
| **Keep**             |          |           |     -     |                 |                |
| **Castle**           |          |           |           |                 |                |
| **Lumbercamp**       |          |     -     |     -     |                 |                |
| **Field**            |          |     -     |     -     |                 |                |
| **Livestock**        |          |     -     |     -     |                 |                |
| **Querry**           |          |     -     |     -     |                 |                |
| **Textile Workshop** |          |     -     |     -     |                 |                |
| **Brewery**          |          |           |     -     |                 |                |
| **Smokehause**       |          |           |     -     |                 |                |
| **Mine**             |          |           |     -     |                 |                |
| **Deep Mine**        |          |           |           |                 |                |
| **Smelter**          |          |           |     -     |                 |                |
| **Furnace**          |          |           |           |                 |                |
| **Blacksmith**       |          |           |     -     |                 |                |
| **Manofacture**      |          |           |           |                 |                |
| **Jewelery**         |          |           |           | 10              |                |
| **Culture Center**   |          |           |           | 10              |                |
