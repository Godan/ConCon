```mermaid　
erDiagram
  users ||--o{ event_attendees : ""
  event_group_subscriptions }o--|| users: ""
  event_attendees }o--|| events : ""
  events }o--|| event_groups: ""
  event_group_subscriptions }o--|| events: ""

  users {
    bigint id PK
    string name "ユーザー名"
    timestamp created_at
    timestamp deleted_at
  }

  events {
    bigint id PK
    references user FK
    string title "投稿タイトル"
    text content "投稿内容"
    timestamp created_at
    timestamp deleted_at
  }

  event_attendees {
    bigint id PK
    references user FK
    references event FK
    timestamp created_at
    timestamp deleted_at
  }  

  event_groups {
    bigint id PK
    references post FK
    references user FK
    text content "コメント内容"
    timestamp created_at
    timestamp deleted_at
  }

  event_group_subscriptions {
    bigint id PK
    references user FK
    references event_group FK
    timestamp created_at
    timestamp deleted_at
  }

  settings {
    bigint id PK
    timestamp created_at
    timestamp deleted_at
  }

  messages {
    bigint id PK
    timestamp created_at
    timestamp deleted_at
  }
  ```