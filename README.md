graph TD
    subgraph User Layer
        A[Students] -->|Requests| B(Backend);
        B -->|Mentorship & Networking| C[Alumni];
        C -->|Data/Feedback| B;
        B -->|Dashboards/Insights| D[College Admins];
        D -->|Strategic Planning| B;
    end

    subgraph Application Layer
        B(Backend) -->|Processes Requests| E[User Management Module];
        B -->|Manages Matching| F[Mentorship Module];
        B -->|Handles Postings| G[Job Board Module];
        B -->|Manages Events| H[Event Module];
    end

    subgraph AI / Intelligence Layer
        subgraph Data Processing
            I[Student Profile] -->|Input| J[Matching Engine];
            J -->|Output| K[Ranked Alumni List];
            K --> B;
            L[Alumni Interaction Logs] -->|Input| M[Engagement & Sentiment Analyzer];
            M -->|Output| N[Engagement Scores];
            N --> P;
            O[Historical Placement Data] -->|Input| Q[Placement & Industry Intelligence];
            Q -->|Output| R[Trends & Forecasts];
            R --> P;
            S[Student Queries] -->|Input| T[RAG Chatbot / Networking Assistant];
            T -->|Output| U[Outreach Drafts & Guidance];
            U --> B;
            V[Student Profile & Target Career] -->|Input| W[Career Trajectory Simulator];
            W -->|Output| X[Predicted Paths & Skill Gaps];
            X --> P;
        end

        subgraph Knowledge Graph
            Y[Alumni, Students, Companies, etc.] -->|Nodes| Z[Knowledge Graph Engine];
            Z -->|Edges| AA[Worked at, Mentored, etc.];
            AA --> Z;
            Z -->|Advanced Queries| B;
        end
    end

    subgraph Data Layer
        P[Data Output from AI] -->|Stored in| AB[Relational DB (PostgreSQL/MySQL)];
        P -->|Stored in| AC[Vector DB (FAISS/Milvus)];
        P -->|Stored in| AD[Graph DB (Neo4j/ArangoDB)];
        AE[External APIs] -->|Data Ingestion| P;
    end

    subgraph Visualization & Dashboards
        AF[Plotly/D3.js] --> AG(Dashboards & Visualizations);
        AG -->|Display| A;
        AG -->|Display| C;
        AG -->|Display| D;
        AH[Gamification Layer] --> AG;
    end

    A, C, D -- Interactions with --> B;
    B -- Data Requests --> J, M, Q, T, W, Z;
    J, M, Q, T, W, Z -- Data Storage --> AB, AC, AD;
    AB, AC, AD -- Data Retrieval --> J, M, Q, T, W, Z;
    AB, AC, AD -- Data for Visualization --> AF;
