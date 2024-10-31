```mermaid
erDiagram
  users ||--o{ event_attendees : ""
  event_group_subscriptions }o--|| users: ""
  event_attendees }o--|| event_capacities : ""
  events }o--|| event_groups: ""
  event_group_subscriptions }o--|| event_groups: ""
  events ||--o{ slides: ""
  events ||--o{ event_capacities: ""

  users {
    bigint id PK
    string name "ユーザー名"
    timestamp created_at
    timestamp updated_at
  }

  events {
    bigint id PK
    references created_by FK
    references event_group FK
    string title
    string subtitle
    string thumbnail
    long_text description
    datetime start_at
    datetime end_at
    string location
    timestamp created_at
    timestamp updated_at
    timestamp updated_at
  }

  event_capacities {
    bigint id PK
    references events FK
    string kind
    integer maximum
    timestamp created_at
    timestamp updated_at
  }

  slides {
    bigint id PK
    references event FK
    references created_by FK
    text url
    timestamp created_at
    timestamp updated_at
  }

  event_attendees {
    bigint id PK
    references user FK
    references event_capacity FK
    timestamp created_at
    timestamp updated_atv
  }

  event_groups {
    bigint id PK
    references event FK
    string name
    text description
    timestamp created_at
    timestamp updated_at
  }

  event_group_subscriptions {
    bigint id PK
    references user FK
    references event_group FK
    timestamp created_at
    timestamp updated_at
  }

  settings {
    bigint id PK
    text name
    string value
    timestamp created_at
    timestamp updated_at
  }


  ```