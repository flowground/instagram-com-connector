# ![LOGO](logo.png) Instagram **flow**ground Connector

## Description

A generated **flow**ground connector for the Instagram API (version 1.0.0).

Generated from: https://api.apis.guru/v2/specs/instagram.com/1.0.0/swagger.json<br/>
Generated at: 2019-05-07T17:42:27+03:00

## API Description

Description of Instagram RESTful API.

Current limitations:
  * Instagram service does not support [cross origin headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS)
  for security reasons, therefore it is not possible to use Swagger UI and make API calls directly from browser.
  * Modification API requests (`POST`, `DELETE`) require additional security [scopes](https://instagram.com/developer/authorization/)
  that are available for Apps [created on or after Nov 17, 2015](http://instagram.com/developer/review/) and
  started in [Sandbox Mode](http://instagram.com/developer/sandbox/).
  * Consider the [Instagram limitations](https://instagram.com/developer/limits/) for API calls that depends on App Mode.

**Warning:** For Apps [created on or after Nov 17, 2015](http://instagram.com/developer/changelog/) API responses
containing media objects no longer return the `data` field in `comments` and `likes` nodes.

Last update: 2015-11-28


## Authorization

Supported authorization schemes:
- API Key- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### Get recent media from a custom geo-id.

> Get recent media from a geography subscription that you created.<br/>
> <br/>
> **Note:** You can only access Geographies that were explicitly created by your OAuth client. Check the<br/>
> Geography Subscriptions section of the [real-time updates page](https://instagram.com/developer/realtime/).<br/>
> When you create a subscription to some geography that you define, you will be returned a unique `geo-id` that<br/>
> can be used in this query. To backfill photos from the location covered by this geography, use the<br/>
> [media search endpoint](https://instagram.com/developer/endpoints/media/).<br/>
> <br/>
> **Warning:** [Deprecated](http://instagram.com/developer/changelog/) for Apps created **on or after** Nov 17, 2015

*Tags:* `geographies`

#### Input Parameters
* `geo-id` - _required_ - The geography ID.
* `count` - _optional_ - Max number of media to return.
* `min_id` - _optional_ - Return media before this `min_id`.

### Search for a location by geographic coordinate.

*Tags:* `locations`

#### Input Parameters
* `distance` - _optional_ - Default is 1000m (distance=1000), max distance is 5000.
* `facebook_places_id` - _optional_ - Returns a location mapped off of a Facebook places id. If used, a Foursquare id and `lat`, `lng` are not required.
* `foursquare_id` - _optional_ - Returns a location mapped off of a foursquare v1 api location id. If used, you are not required to use
`lat` and `lng`. Note that this method is deprecated; you should use the new foursquare IDs with V2 of their API.

* `lat` - _optional_ - Latitude of the center search coordinate. If used, `lng` is required.
* `lng` - _optional_ - Longitude of the center search coordinate. If used, `lat` is required.
* `foursquare_v2_id` - _optional_ - Returns a location mapped off of a foursquare v2 api location id. If used, you are not required to use
`lat` and `lng`.


### Get information about a location.

*Tags:* `locations`

#### Input Parameters
* `location-id` - _required_ - The location ID.

### Get a list of recent media objects from a given location.

*Tags:* `locations`

#### Input Parameters
* `location-id` - _required_ - The location ID.
* `min_timestamp` - _optional_ - Return media after this UNIX timestamp.
* `max_timestamp` - _optional_ - Return media before this UNIX timestamp.
* `min_id` - _optional_ - Return media before this `min_id`.
* `max_id` - _optional_ - Return media after this `max_id`.

### Get a list of currently popular media.

> Get a list of what media is most popular at the moment. Can return mix of `image` and `video` types.<br/>
> <br/>
> **Warning:** [Deprecated](http://instagram.com/developer/changelog/) for Apps created **on or after** Nov 17, 2015

*Tags:* `media`

### Search for media in a given area.

> Search for media in a given area. The default time span is set to 5 days. The time span must not exceed 7 days.<br/>
> Defaults time stamps cover the last 5 days. Can return mix of `image` and `video` types.

*Tags:* `media`

#### Input Parameters
* `lat` - _required_ - Latitude of the center search coordinate. If used, `lng` is required.
* `lng` - _required_ - Longitude of the center search coordinate. If used, `lat` is required.
* `min_timestamp` - _optional_ - A unix timestamp. All media returned will be taken later than this timestamp.
* `max_timestamp` - _optional_ - A unix timestamp. All media returned will be taken earlier than this timestamp.
* `distance` - _optional_ - Default is 1km (distance=1000), max distance is 5km.

### Get information about a media object.

> This endpoint returns the same response as `GET /media/{media-id}`.<br/>
> <br/>
> A media object's shortcode can be found in its shortlink URL. An example shortlink is<br/>
> `http://instagram.com/p/D/`, its corresponding shortcode is `D`.

*Tags:* `media`

#### Input Parameters
* `shortcode` - _required_ - The short code of the media resource.

### Get information about a media object.

> Get information about a media object. The returned type key will allow you to differentiate between image and<br/>
> video media.<br/>
> <br/>
> **Note:** if you authenticate with an OAuth Token, you will receive the user_has_liked key which quickly tells<br/>
> you whether the current user has liked this media item.

*Tags:* `media`

#### Input Parameters
* `media-id` - _required_ - The ID of the media resource.

### Get a list of recent comments on a media object.

*Tags:* `comments`

#### Input Parameters
* `media-id` - _required_ - The ID of the media resource.

### Create a comment on a media object.

> Create a comment on a media object with the following rules:<br/>
> <br/>
>   * The total length of the comment cannot exceed 300 characters.<br/>
>   * The comment cannot contain more than 4 hashtags.<br/>
>   * The comment cannot contain more than 1 URL.<br/>
>   * The comment cannot consist of all capital letters.

*Tags:* `comments`

#### Input Parameters
* `media-id` - _required_ - The ID of the media resource.
* `text` - _required_ - Text to post as a comment on the media object as specified in `media-id`.

### Remove a comment.

> Remove a comment either on the authenticated user's media object or authored by the authenticated user.

*Tags:* `comments`

#### Input Parameters
* `media-id` - _required_ - The ID of the media resource.
* `comment-id` - _required_ - The ID of the comment entry.

### Remove a like on this media by the current user.

> Remove a like on this media by the currently authenticated user.

*Tags:* `likes`

#### Input Parameters
* `media-id` - _required_ - The ID of the media resource.

### Get a list of users who have liked this media.

*Tags:* `likes`

#### Input Parameters
* `media-id` - _required_ - The ID of the media resource.

### Set a like on this media by the current user.

> Set a like on this media by the currently authenticated user.

*Tags:* `likes`

#### Input Parameters
* `media-id` - _required_ - The ID of the media resource.

### Search for tags by name.

*Tags:* `tags`

#### Input Parameters
* `q` - _required_ - A valid tag name without a leading \#. (eg. snowy, nofilter)

### Get information about a tag object.

*Tags:* `tags`

#### Input Parameters
* `tag-name` - _required_ - The tag name.

### Get a list of recently tagged media.

> Get a list of recently tagged media. Use the `max_tag_id` and `min_tag_id` parameters in the pagination<br/>
> response to paginate through these objects.

*Tags:* `tags`

#### Input Parameters
* `tag-name` - _required_ - The tag name.
* `count` - _optional_ - Count of tagged media to return.
* `min_tag_id` - _optional_ - Return media before this `min_tag_id`.
* `max_tag_id` - _optional_ - Return media after this `max_tag_id`.

### Search for a user by name.

*Tags:* `users`

#### Input Parameters
* `q` - _required_ - A query string.
* `count` - _optional_ - Number of users to return.

### See the authenticated user's feed.

> See the authenticated user's feed.<br/>
> <br/>
> **Warning:** [Deprecated](http://instagram.com/developer/changelog/) for Apps created **on or after** Nov 17, 2015

*Tags:* `users`

#### Input Parameters
* `count` - _optional_ - Count of media to return.
* `min_id` - _optional_ - Return media later than this `min_id`.
* `max_id` - _optional_ - Return media earlier than this `max_id`.

### See the list of media liked by the authenticated user.

> See the list of media liked by the authenticated user. Private media is returned as long as the authenticated<br/>
> user has permission to view that media. Liked media lists are only available for the currently authenticated<br/>
> user.

*Tags:* `users`

#### Input Parameters
* `count` - _optional_ - Count of media to return.
* `max_like_id` - _optional_ - Return media liked before this id.

### List the users who have requested this user's permission to follow.

*Tags:* `relationships`

### Get basic information about a user.

> Get basic information about a user. To get information about the owner of the access token, you can use<br/>
> **self** instead of the `user-id`.<br/>
> <br/>
> Security scope `public_content` is required to read information about other users.

*Tags:* `users`

#### Input Parameters
* `user-id` - _required_ - The ID of a user to get information about, or **self** to retrieve information about authenticated user.

### Get the list of users this user is followed by.

> Get the list of users this user is followed by. To get users followed by the owner of the access token, you<br/>
> can use **self** instead of the `user-id`.

*Tags:* `relationships`

#### Input Parameters
* `user-id` - _required_ - The ID of a user, or **self** to retrieve information about authenticated user.

### Get the list of users this user follows.

> Get the list of users this user follows. To get follows of the owner of the access token, you can use **self**<br/>
> instead of the `user-id`.

*Tags:* `relationships`

#### Input Parameters
* `user-id` - _required_ - The ID of a user, or **self** to retrieve information about authenticated user.

### Get the most recent media published by a user.

> Get the most recent media published by a user. To get the most recent media published by the owner of the<br/>
> access token, you can use **self** instead of the `user-id`.<br/>
> <br/>
> Security scope `public_content` is required to read information about other users.

*Tags:* `users`

#### Input Parameters
* `user-id` - _required_ - The ID of a user to get recent media of, or **self** to retrieve media of authenticated user.
* `count` - _optional_ - Count of media to return.
* `max_timestamp` - _optional_ - Return media before this UNIX timestamp.
* `min_timestamp` - _optional_ - Return media after this UNIX timestamp.
* `min_id` - _optional_ - Return media later than this `min_id`.
* `max_id` - _optional_ - Return media earlier than this `max_id`.

### Get information about a relationship to another user.

*Tags:* `relationships`

#### Input Parameters
* `user-id` - _required_ - The ID of a user to get information about.

### Modify the relationship between the current user and the target user.

*Tags:* `relationships`

#### Input Parameters
* `user-id` - _required_ - The ID of the target user.
* `action` - _required_ - Type of action to apply for relationship with the user.
    Possible values: follow, unfollow, block, unblock, approve, ignore.

## License

**flow**ground :- Telekom iPaaS / instagram-com-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
