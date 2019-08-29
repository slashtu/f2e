# GraphQL Best Practice - 曾建勳 (kpman)

{%hackmd yEJ_rTxzTWa2K450RqmT8w %}

## Schema Design

### Identification

- 不要放 foreign key，要直接放 relation
```gql
type Chatbot {
  ownerId: String!  // bad
  ownder: User      // good, can further explore
}

type User {
  id: String!
  name: String!
}

```
- Thinking in Graphs.

### Non-null in GraphQL

- GraphQL schema is ==versionless==.
- Types are ==nullable== by default.
- only add non-null `!` when it is required. (Think twice!)
(不必要的 `!` require mark 可能會導致一個小錯就拿不到整個 record)
> non-null 欄位只要有其中一個取值失敗，會噴 runtime error

### Mutation Schema Design
- 如果參數越來越多 $\rightarrow$ Mutation file $\uparrow$

#### input object type
- 可以考慮把所有參數包成一個 input object，有自己的 type
- 需要改動時只需要改 input object 自己的 type definition，不會動到 query/mutation 本身的參數

#### output payload type
把 mutation output 也包成一種獨立的 type，這樣比較彈性，可以加入非 record 本身的欄位

## Performance Optimization

### [GraphQL fields](https://github.com/robrichard/graphql-fields)
- Early return on `id` only queries, skip unnecessary DB/resource access

### Dataloader
cache to reduce nested structure query
- [Demo repo](https://github.com/kpman/graphqltw-meetup01)

## Error Handling

restful:
200 ok!

Graphql:
- Error 
    - 資料拿不到
- Result
    - Deleted User
    - Suspend User
    - IsBlock User

### [Union type](https://graphql.org/learn/schema/#union-types)
`union userResult = User | Isblocked | Suspend`
use inline fragment to determine your result

```gql
query {
  user {
    ... on User {  // <- inline fragment
      id
      name
      email
    }
    ... on IsBlocked {
      reason
      blockedAt
    }
    ... on Suspend {
      reason
    }
  }
}
```

## Apollo Ecosystem

- Client
- Server
- Graph Manager
    - Apollo Engine
    - Validate schema changes
    - Daily report
- [Federation](https://www.apollographql.com/docs/apollo-server/federation/introduction/)

###### tags: `MW19`
