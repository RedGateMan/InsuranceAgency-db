# InsuranceAgency-db
Repository contain project for db class of 2023, 3rd year.

>Student: Chyzhou Yahpr, 153503\
>Project: Insurance Agency (IGI 4th term)

## Functionality
1. Registration, Authorisation, Authentification
2. Role system
3. User management(CRUD)
4. Logging of User's actions
5. Office management(CRUD)
6. Insurance managemnt(CRUD)
7. Contract management(CRUD)
    - Status update (by Agent)
    - Insurance type (by Agent)
    - Insurance cost (by Agent)
    - Type of object for insurance (by User)
8. News management(CRUD)
---

## Tables:
1. User
   - id - integer() NOT NULL
   - name - varchar(15)NOT NULL
   - surname - varchar(20)NOT NUll
   - patronymic - varchar(20)NOT NULL
   - username - varchar(30)UNIQUE
   - email - text()NOT NUL, must be valid
   - phone - varchar(20)NOT NULL
   - date_joined - timestamp()
   - last_login - timestamp()
   - role - OtO(Permissions)

2. Office
   - id - integer() NOT NULL
   - name - varchar(30)NOT NULL
   - address - varchar(50)NOT NULL
   - phone - varchar(13)NOT NULL
   
3. Insurance
   - id - integer() NOT NULL
   - insurance_type - MtO(Insurance_type)NOT NULL
   - minimal_cost - integer() NOT NULL
   - duration - bigint() NOT NULL
   - percentage  - float() NOT NULL
   
4. Object 
   - id - integer() NOT NULL
   - object_type - varchar(20)NOT NULL, choices
   - description - text()NOT NULL
   
5. Agent
   - id - integer() NOT NULL
   - office - MtO(Office)NULL
   - user - OtO(User)is staff = TRUE

6. Contract
   - id - integer() NOT NULL
   - status - varchar(15)default = "PENDING",NULL, BLANK, choices
   - agent - MtO(Agent)NULL, BLANK
   - insurance - MtO(Insurance)NULL,BLANK
   - object - OtO(Object)NULL, BLANK
   - sign_date - timestamp()
   - cost - varchar(60)NULL, BLANK
   
7. Article
   - id - integer() NOT NULL
   - created_at - timestamp()
   - author - MtO(User)NOT NULL, NOT BLANK
   - title - text(150)default = "Article Title"
   - content - text()

8. Logs
   - id - integer() NOT NULL
   - operation - varchar('create', 'delete', 'update')NOT NULL
   - timestamp - timestamp NOT NULL
   - old - text()
   - new - text()

9. Permissions
   - id - integer() NOT NULL
   - is_admin - boolean()
   - is_staff - boolean()
   - is_superuser - boolean()

10. Insurance_type
    - id - integer() NOT NULL
    - type - varchar(20)

11. UserRole
    - id - integer() NOT NULL
    - role - varchar(15) NOT NULL, NOT BLANK