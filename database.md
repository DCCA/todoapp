erDiagram
    Area ||--|| Objective: ObjectiveID
    Area ||--|| Project: ProjectID
    Area ||--|| Resources: ResourceID

    Area {
        int AreaID PK
        int ObjectiveID FK
        int ProjectID FK
        int ResourceID FK
        date CreatedDate
        int Name
        string Icon
    }
    
    Objective {
        int ObjectiveID PK
        int KeyResultID FK
        int ProjectID FK
        date CreatedDate 
        string Name 
        date Deadline 
    }
    Objective ||--|| Project: ProjectID
    Objective ||--|| KeyResult: KeyResultID

    KeyResult {
        int KeyResultID PK
        int ProjectID FK
        date CreatedDate
        string Name 
        int Goal 
        date Deadline 
    }
    KeyResult ||--|| Project: ProjectID
    KeyResult ||--|| KeyResultLog: KeyResultLogID

    KeyResultLog {
        int KeyResultLogID PK
        int KeyResultID FK
        date CreatedDate
        int Value
    }

    Task {
        int TaskID PK
        int ProjectID FK
        int PriorityID FK
        int StatusID FK
        date CreatedDate
        string Name
        string Description
        date Deadline
        date WaitDate
        bool isProcessed
    }
    Task ||--|| Project: ProjectID
    Task ||--|| Priority: PriorityID 
    Task ||--|| Status: StatusID

    Status {
        int StatusID PK
        string Name
    }

    Priority {
        int PriorityID PK
        string Name
    }

    Project {
        int ProjectID PK
        int AreaID FK
        int ObjectiveID FK
        int ResourceID FK
        int StatusID FK
        string Name
        string Description
        date Deadline
    }
    Project ||--|| Area: AreaID
    Project ||--|| Objective: ObjectiveID
    Project ||--|| Resources: ResourceID
    Project ||--|| Status: StatusID

    Notes {
        int NoteID PK
        int ResourceID FK
        int ProjectID FK
        int TaskID FK
        string Name
        string Description
        string Anexo
        string Link
    }
    Notes ||--|| Resources: ResourceID
    Notes ||--|| Project: ProjectID
    Notes ||--|| Task: TaskID

    Resources {
        int ResourceID PK
        string Name
    }

    Routine {
        int RoutineID PK
        date CreatedDate
        string Name
        string Repeatable
    }
