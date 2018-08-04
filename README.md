# [WIP] Qarma
An open source karma system for graphql implemented with custom `schema types`. A karma system is a way to incentivize users to self-police a community.

_Potentially ship with custom resolvers and database_

## Type: Qarma Rating
Extend any `type` by giving it a `field` with type `QarmaRating`
```javascript
type QarmaRating {
  ratingTotal : Int           // Total value
  castTotal   : Int           // Total votes cast
  status      : String        // Text description of voting trends
  votes       : [ QarmaVote ] // List of all votes
}
```

## Type: Qarma Vote
All votes cast are saved off to a vote database
```javascript
type QarmaVote {
  value  : Int // A value between -5 and +5
  castBy : Int // Entity ID that cast the vote (maybe hashed?)
  castOn : Int // Entity ID that was rated (maybe hashed?)
}
```

## Type: Qarma User
Extend your applications users by adding a `field` with type `QarmaUser`
```javascript
type QarmaUser {
  voteCount : Int           // Number of times user voted
  upCount   : Int           // Number of times user upvoted
  downCount : Int           // Number of times user downvoted
  votes     : [ QarmaVote ] // List of all votes
}
```
## Misc Thoughts
 - [ ] Karma based acheivments
 - [ ] Karma based permissions (or just base it off acheivments?)
 - [ ] `type QarmaFlag` for flagging content
