flowchart TD
    %% Initialization Stage
    A["🚀 Start Similarity Analysis"] --> B["📂 Load Trained Models"]
    B --> C["🔍 Load StandardScaler - From Pickle File - Preprocessing Transformer"]
    C --> D["🤖 Load Autoencoder Model - Keras Saved Model - Feature Extraction"]

    %% Data Preparation
    D --> E["📊 Load Training Dataset - Pandas DataFrame - Raw Environmental Data"]
    E --> F["🧹 Data Cleaning - Remove Missing Values - Select Relevant Columns"]
    F --> G["📏 Define Feature Weights - NDVI: 2.7 - CI: 2.5 - Elevation: 2.2"]

    %% New Places Data Processing
    G --> H["📥 Load New Places Dataset - Geographical Variations - Multiple Locations"]
    H --> I["🔢 Group Data - By Latitude - By Longitude - By Month"]
    I --> J["📊 Calculate Aggregated Metrics - Mean Values - Statistical Summaries"]

    %% Similarity Analysis Loop
    J --> K{🔄 Iterate Through Unique Places}
    K --> L["🛠️ Data Preparation - Exclude Spatial Metadata - Reshape for Analysis"]

    %% Similarity Computation Subprocess
    L --> M["🔬 Similarity Metrics Calculation"]
    M --> N["📐 Data Scaling - StandardScaler - Normalize Features"]
    N --> O["🏋️ Apply Feature Weights - Emphasize Key Indicators - Customize Importance"]
    O --> P["🧩 Autoencoder Feature Extraction - Compress High-Dimensional Data - Learn Latent Representations"]

    %% Distance and Similarity Calculations
    P --> Q["📏 Euclidean Distance - Numerical Difference - Geometric Proximity"]
    Q --> R["📐 Cosine Similarity - Angular Proximity - Directional Alignment"]
    R --> S["📊 Percentile Ranking - Normalize Similarity Scores - Comparative Analysis"]

    %% Dissimilarity Threshold Check
    S --> T["🚦 Similarity Thresholds - Euclidean Distance - Cosine Similarity"]
    T --> U{❓ Is Place Dissimilar?}

    %% Result Handling
    U -->|Yes| V["🚨 Flag as Dissimilar - Unique Characteristics - Outlier Detection"]
    U -->|No| W["🔍 Identify Similar Places - Top 5 Matches - Closest Neighbors"]

    %% Visualization and Logging
    V --> X["💾 Store Analysis Results - Geographical Context - Similarity Metrics"]
    W --> X
    X --> Y["📊 Visualize Distributions - Matplotlib - Seaborn Plots - Similarity Landscape"]

    %% Iteration and Finalization
    Y --> Z{🔁 More Places to Analyze?}
    Z -->|Yes| K
    Z -->|No| AA["💾 Save Comprehensive Results - Excel Spreadsheet - Detailed Analysis"]

    %% Conclusion
    AA --> AB["📈 Generate Summary Visualization - Aggregate Insights - Geographical Patterns"]
    AB --> AC["🏁 End of Similarity Analysis"]

    %% Styling
    classDef start fill:#f9f,stroke:#333,stroke-width:4px;
    classDef process fill:#bbf,stroke:#333,stroke-width:2px;
    classDef decision fill:#ff9,stroke:#333,stroke-width:2px;

    class A,AC start;
    class B,C,D,E,F,G,H,I,L,M,N,O,P,Q,R,S,V,W,X,Y,AA,AB process;
    class K,T,U,Z decision;
