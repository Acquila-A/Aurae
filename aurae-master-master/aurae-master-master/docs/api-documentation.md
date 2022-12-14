# API Documentation for Metabase v0.22.0-snapshot

## `GET /api/activity/`

Get recent activity.


## `GET /api/activity/recent_views`

Get the list of 10 things the current user has been viewing most recently.


## `DELETE /api/card/:card-id/favorite`

Unfavorite a Card.

##### PARAMS:

*  **`card-id`** 


## `DELETE /api/card/:id`

Delete a `Card`.

##### PARAMS:

*  **`id`** 


## `GET /api/card/`

Get all the `Cards`. Option filter param `f` can be used to change the set of Cards that are returned; default is `all`,
   but other options include `mine`, `fav`, `database`, `table`, `recent`, `popular`, and `archived`. See corresponding implementation
   functions above for the specific behavior of each filter option. :card_index:

   Optionally filter cards by LABEL slug.

##### PARAMS:

*  **`f`** value may be nil, or if non-nil, value must be one of: `all`, `archived`, `database`, `fav`, `mine`, `popular`, `recent`, `table`.

*  **`model_id`** value may be nil, or if non-nil, value must be an integer greater than zero.

*  **`label`** value may be nil, or if non-nil, value must be a non-blank string.


## `GET /api/card/:id`

Get `Card` with ID.

##### PARAMS:

*  **`id`** 


## `POST /api/card/`

Create a new `Card`.

##### PARAMS:

*  **`dataset_query`** 

*  **`description`** 

*  **`display`** value must be a non-blank string.

*  **`name`** value must be a non-blank string.

*  **`visualization_settings`** value must be a map.


## `POST /api/card/:card-id/favorite`

Favorite a Card.

##### PARAMS:

*  **`card-id`** 


## `POST /api/card/:card-id/labels`

Update the set of `Labels` that apply to a `Card`.

##### PARAMS:

*  **`card-id`** 

*  **`label_ids`** value must be an array. Each value must be an integer greater than zero.


## `POST /api/card/:card-id/query`

Run the query associated with a Card.

##### PARAMS:

*  **`card-id`** 

*  **`parameters`** 


## `POST /api/card/:card-id/query/csv`

Run the query associated with a Card, and return its results as CSV. Note that this expects the parameters as serialized JSON in the 'parameters' parameter

##### PARAMS:

*  **`card-id`** 

*  **`parameters`** value may be nil, or if non-nil, value must be a valid JSON string.


## `POST /api/card/:card-id/query/json`

Run the query associated with a Card, and return its results as JSON. Note that this expects the parameters as serialized JSON in the 'parameters' parameter

##### PARAMS:

*  **`card-id`** 

*  **`parameters`** value may be nil, or if non-nil, value must be a valid JSON string.


## `PUT /api/card/:id`

Update a `Card`.

##### PARAMS:

*  **`id`** 

*  **`dataset_query`** 

*  **`description`** 

*  **`display`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`name`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`visualization_settings`** value may be nil, or if non-nil, value must be a map.

*  **`archived`** value may be nil, or if non-nil, value must be a boolean.


## `DELETE /api/dashboard/:id`

Delete a `Dashboard`.

##### PARAMS:

*  **`id`** 


## `DELETE /api/dashboard/:id/cards`

Remove a `DashboardCard` from a `Dashboard`.

##### PARAMS:

*  **`id`** 

*  **`dashcardId`** value must be a valid integer greater than zero.


## `GET /api/dashboard/`

Get `Dashboards`. With filter option `f` (default `all`), restrict results as follows:

  *  `all` - Return all `Dashboards`.
  *  `mine` - Return `Dashboards` created by the current user.

##### PARAMS:

*  **`f`** value may be nil, or if non-nil, value must be one of: `all`, `mine`.


## `GET /api/dashboard/:id`

Get `Dashboard` with ID.

##### PARAMS:

*  **`id`** 


## `GET /api/dashboard/:id/revisions`

Fetch `Revisions` for `Dashboard` with ID.

##### PARAMS:

*  **`id`** 


## `POST /api/dashboard/`

Create a new `Dashboard`.

##### PARAMS:

*  **`name`** value must be a non-blank string.

*  **`parameters`** value must be an array. Each value must be a map.

*  **`dashboard`** 


## `POST /api/dashboard/:id/cards`

Add a `Card` to a `Dashboard`.

##### PARAMS:

*  **`id`** 

*  **`cardId`** value must be an integer greater than zero.

*  **`parameter_mappings`** value must be an array. Each value must be a map.

*  **`series`** 

*  **`dashboard-card`** 


## `POST /api/dashboard/:id/revert`

Revert a `Dashboard` to a prior `Revision`.

##### PARAMS:

*  **`id`** 

*  **`revision_id`** value must be an integer greater than zero.


## `PUT /api/dashboard/:id`

Update a `Dashboard`.

##### PARAMS:

*  **`id`** 

*  **`description`** 

*  **`name`** value must be a non-blank string.

*  **`parameters`** value must be an array. Each value must be a map.

*  **`caveats`** 

*  **`points_of_interest`** 

*  **`show_in_getting_started`** 

*  **`dashboard`** 


## `PUT /api/dashboard/:id/cards`

Update `Cards` on a `Dashboard`. Request body should have the form:

    {:cards [{:id ...
              :sizeX ...
              :sizeY ...
              :row ...
              :col ...
              :series [{:id 123
                        ...}]} ...]}

##### PARAMS:

*  **`id`** 

*  **`cards`** 


## `DELETE /api/database/:id`

Delete a `Database`.

##### PARAMS:

*  **`id`** 


## `GET /api/database/`

Fetch all `Databases`.

##### PARAMS:

*  **`include_tables`** 


## `GET /api/database/:id`

Get `Database` with ID.

##### PARAMS:

*  **`id`** 


## `GET /api/database/:id/autocomplete_suggestions`

Return a list of autocomplete suggestions for a given PREFIX.
   This is intened for use with the ACE Editor when the User is typing raw SQL.
   Suggestions include matching `Tables` and `Fields` in this `Database`.

   Tables are returned in the format `[table_name "Table"]`;
   Fields are returned in the format `[field_name "table_name base_type special_type"]`

##### PARAMS:

*  **`id`** 

*  **`prefix`** value must be a non-blank string.


## `GET /api/database/:id/fields`

Get a list of all `Fields` in `Database`.

##### PARAMS:

*  **`id`** 


## `GET /api/database/:id/idfields`

Get a list of all primary key `Fields` for `Database`.

##### PARAMS:

*  **`id`** 


## `GET /api/database/:id/metadata`

Get metadata about a `Database`, including all of its `Tables` and `Fields`.
   Returns DB, fields, and field values.

##### PARAMS:

*  **`id`** 


## `POST /api/database/`

Add a new `Database`.

You must be a superuser to do this.

##### PARAMS:

*  **`name`** value must be a non-blank string.

*  **`engine`** value must be a valid database engine.

*  **`details`** value must be a map.

*  **`is_full_sync`** 


## `POST /api/database/:id/sync`

Update the metadata for this `Database`.

##### PARAMS:

*  **`id`** 


## `POST /api/database/sample_dataset`

Add the sample dataset as a new `Database`.

You must be a superuser to do this.


## `PUT /api/database/:id`

Update a `Database`.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 

*  **`name`** value must be a non-blank string.

*  **`engine`** value must be a valid database engine.

*  **`details`** value must be a map.

*  **`is_full_sync`** 

*  **`description`** 

*  **`caveats`** 

*  **`points_of_interest`** 


## `POST /api/dataset/`

Execute an MQL query and retrieve the results as JSON.

##### PARAMS:

*  **`database`** 


## `POST /api/dataset/csv`

Execute a query and download the result data as a CSV file.

##### PARAMS:

*  **`query`** value must be a valid JSON string.


## `POST /api/dataset/duration`

Get historical query execution duration.

##### PARAMS:

*  **`database`** 

*  **`query`** 


## `POST /api/dataset/json`

Execute a query and download the result data as a JSON file.

##### PARAMS:

*  **`query`** value must be a valid JSON string.


## `POST /api/email/test`

Send a test email. You must be a superuser to do this.

You must be a superuser to do this.


## `PUT /api/email/`

Update multiple `Settings` values.  You must be a superuser to do this.

You must be a superuser to do this.

##### PARAMS:

*  **`settings`** value must be a map.


## `GET /api/field/:id`

Get `Field` with ID.

##### PARAMS:

*  **`id`** 


## `GET /api/field/:id/summary`

Get the count and distinct count of `Field` with ID.

##### PARAMS:

*  **`id`** 


## `GET /api/field/:id/values`

If `Field`'s special type derives from `type/Category`, or its base type is `type/Boolean`, return
   all distinct values of the field, and a map of human-readable values defined by the user.

##### PARAMS:

*  **`id`** 


## `POST /api/field/:id/value_map_update`

Update the human-readable values for a `Field` whose special type is `category`/`city`/`state`/`country`
   or whose base type is `type/Boolean`.

##### PARAMS:

*  **`id`** 

*  **`values_map`** value must be a map.


## `PUT /api/field/:id`

Update `Field` with ID.

##### PARAMS:

*  **`id`** 

*  **`caveats`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`description`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`display_name`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`fk_target_field_id`** value may be nil, or if non-nil, value must be an integer.

*  **`points_of_interest`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`special_type`** value may be nil, or if non-nil, value must be a valid field type.

*  **`visibility_type`** value may be nil, or if non-nil, value must be one of: `details-only`, `hidden`, `normal`, `retired`, `sensitive`.


## `GET /api/geojson/:key`

Fetch a custom GeoJSON file as defined in the `custom-geojson` setting. (This just acts as a simple proxy for the file specified for KEY).

##### PARAMS:

*  **`key`** value must be a non-blank string.


## `GET /api/getting-started/`

Fetch basic info for the Getting Started guide.


## `DELETE /api/label/:id`

Delete a `Label`. :label:

##### PARAMS:

*  **`id`** 


## `GET /api/label/`

List all `Labels`. :label:


## `POST /api/label/`

Create a new `Label`. :label: 

##### PARAMS:

*  **`name`** value must be a non-blank string.

*  **`icon`** value may be nil, or if non-nil, value must be a non-blank string.


## `PUT /api/label/:id`

Update a `Label`. :label:

##### PARAMS:

*  **`id`** 

*  **`name`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`icon`** value may be nil, or if non-nil, value must be a non-blank string.


## `DELETE /api/metric/:id`

Delete a `Metric`.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 

*  **`revision_message`** value must be a non-blank string.


## `GET /api/metric/`

Fetch *all* `Metrics`.

##### PARAMS:

*  **`id`** 


## `GET /api/metric/:id`

Fetch `Metric` with ID.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `GET /api/metric/:id/revisions`

Fetch `Revisions` for `Metric` with ID.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `POST /api/metric/`

Create a new `Metric`.

You must be a superuser to do this.

##### PARAMS:

*  **`name`** value must be a non-blank string.

*  **`description`** 

*  **`table_id`** value must be an integer greater than zero.

*  **`definition`** value must be a map.


## `POST /api/metric/:id/revert`

Revert a `Metric` to a prior `Revision`.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 

*  **`revision_id`** value must be an integer greater than zero.


## `PUT /api/metric/:id`

Update a `Metric` with ID.

You must be a superuser to do this.

##### PARAMS:

*  **`points_of_interest`** 

*  **`description`** 

*  **`definition`** value must be a map.

*  **`revision_message`** value must be a non-blank string.

*  **`show_in_getting_started`** 

*  **`name`** value must be a non-blank string.

*  **`caveats`** 

*  **`id`** 

*  **`how_is_this_calculated`** 


## `PUT /api/metric/:id/important_fields`

Update the important `Fields` for a `Metric` with ID.
   (This is used for the Getting Started guide).

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 

*  **`important_field_ids`** value must be an array. Each value must be an integer greater than zero.


## `POST /api/notify/db/:id`

Notification about a potential schema change to one of our `Databases`.
  Caller can optionally specify a `:table_id` or `:table_name` in the body to limit updates to a single `Table`.

##### PARAMS:

*  **`id`** 

*  **`table_id`** 

*  **`table_name`** 


## `DELETE /api/permissions/group/:group-id`

Delete a specific `PermissionsGroup`.

You must be a superuser to do this.

##### PARAMS:

*  **`group-id`** 


## `DELETE /api/permissions/membership/:id`

Remove a User from a PermissionsGroup (delete their membership).

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `GET /api/permissions/graph`

Fetch a graph of all Permissions.

You must be a superuser to do this.


## `GET /api/permissions/group`

Fetch all `PermissionsGroups`, including a count of the number of `:members` in that group.

You must be a superuser to do this.


## `GET /api/permissions/group/:id`

Fetch the details for a certain permissions group.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `GET /api/permissions/membership`

Fetch a map describing the group memberships of various users.
   This map's format is:

    {<user-id> [{:membership_id <id>
                 :group_id      <id>}]}

You must be a superuser to do this.


## `POST /api/permissions/group`

Create a new `PermissionsGroup`.

You must be a superuser to do this.

##### PARAMS:

*  **`name`** value must be a non-blank string.


## `POST /api/permissions/membership`

Add a `User` to a `PermissionsGroup`. Returns updated list of members belonging to the group.

You must be a superuser to do this.

##### PARAMS:

*  **`group_id`** value must be an integer greater than zero.

*  **`user_id`** value must be an integer greater than zero.


## `PUT /api/permissions/graph`

Do a batch update of Permissions by passing in a modified graph. This should return the same graph,
   in the same format, that you got from `GET /api/permissions/graph`, with any changes made in the wherever neccesary.
   This modified graph must correspond to the `PermissionsGraph` schema.
   If successful, this endpoint returns the updated permissions graph; use this as a base for any further modifications.

   Revisions to the permissions graph are tracked. If you fetch the permissions graph and some other third-party modifies it before you can submit
   you revisions, the endpoint will instead make no changes andr eturn a 409 (Conflict) response. In this case, you should fetch the updated graph
   and make desired changes to that.

You must be a superuser to do this.

##### PARAMS:

*  **`body`** value must be a map.


## `PUT /api/permissions/group/:group-id`

Update the name of a `PermissionsGroup`.

You must be a superuser to do this.

##### PARAMS:

*  **`group-id`** 

*  **`name`** value must be a non-blank string.


## `DELETE /api/pulse/:id`

Delete a `Pulse`.

##### PARAMS:

*  **`id`** 


## `GET /api/pulse/`

Fetch all `Pulses`


## `GET /api/pulse/:id`

Fetch `Pulse` with ID.

##### PARAMS:

*  **`id`** 


## `GET /api/pulse/form_input`

Provides relevant configuration information and user choices for creating/updating `Pulses`.


## `GET /api/pulse/preview_card/:id`

Get HTML rendering of a `Card` with ID.

##### PARAMS:

*  **`id`** 


## `GET /api/pulse/preview_card_info/:id`

Get JSON object containing HTML rendering of a `Card` with ID and other information.

##### PARAMS:

*  **`id`** 


## `GET /api/pulse/preview_card_png/:id`

Get PNG rendering of a `Card` with ID.

##### PARAMS:

*  **`id`** 


## `POST /api/pulse/`

Create a new `Pulse`.

##### PARAMS:

*  **`name`** value must be a non-blank string.

*  **`cards`** value must be an array. Each value must be a map. The array cannot be empty.

*  **`channels`** value must be an array. Each value must be a map. The array cannot be empty.


## `POST /api/pulse/test`

Test send an unsaved pulse.

##### PARAMS:

*  **`name`** value must be a non-blank string.

*  **`cards`** value must be an array. Each value must be a map. The array cannot be empty.

*  **`channels`** value must be an array. Each value must be a map. The array cannot be empty.


## `PUT /api/pulse/:id`

Update a `Pulse` with ID.

##### PARAMS:

*  **`id`** 

*  **`name`** value must be a non-blank string.

*  **`cards`** value must be an array. Each value must be a map. The array cannot be empty.

*  **`channels`** value must be an array. Each value must be a map. The array cannot be empty.


## `GET /api/revision/`

Get revisions of an object.

##### PARAMS:

*  **`entity`** value must be one of: `card`, `dashboard`.

*  **`id`** value must be an integer.


## `POST /api/revision/revert`

Revert an object to a prior revision.

##### PARAMS:

*  **`entity`** value must be one of: `card`, `dashboard`.

*  **`id`** value must be an integer.

*  **`revision_id`** value must be an integer.


## `DELETE /api/segment/:id`

Delete a `Segment`.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 

*  **`revision_message`** value must be a non-blank string.


## `GET /api/segment/`

Fetch *all* `Segments`.


## `GET /api/segment/:id`

Fetch `Segment` with ID.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `GET /api/segment/:id/revisions`

Fetch `Revisions` for `Segment` with ID.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `POST /api/segment/`

Create a new `Segment`.

You must be a superuser to do this.

##### PARAMS:

*  **`name`** value must be a non-blank string.

*  **`description`** 

*  **`table_id`** value must be an integer greater than zero.

*  **`definition`** value must be a map.


## `POST /api/segment/:id/revert`

Revert a `Segement` to a prior `Revision`.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 

*  **`revision_id`** value must be an integer greater than zero.


## `PUT /api/segment/:id`

Update a `Segment` with ID.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 

*  **`name`** value must be a non-blank string.

*  **`description`** 

*  **`caveats`** 

*  **`points_of_interest`** 

*  **`show_in_getting_started`** 

*  **`definition`** value must be a map.

*  **`revision_message`** value must be a non-blank string.


## `DELETE /api/session/`

Logout.

##### PARAMS:

*  **`session_id`** value must be a non-blank string.


## `GET /api/session/password_reset_token_valid`

Check is a password reset token is valid and isn't expired.

##### PARAMS:

*  **`token`** value must be a string.


## `GET /api/session/properties`

Get all global properties and their values. These are the specific `Settings` which are meant to be public.


## `POST /api/session/`

Login.

##### PARAMS:

*  **`email`** value must be a valid email address.

*  **`password`** value must be a non-blank string.

*  **`remote-address`** 


## `POST /api/session/forgot_password`

Send a reset email when user has forgotten their password.

##### PARAMS:

*  **`server-name`** 

*  **`email`** value must be a valid email address.

*  **`remote-address`** 

*  **`request`** 


## `POST /api/session/google_auth`

Login with Google Auth.

##### PARAMS:

*  **`token`** value must be a non-blank string.

*  **`remote-address`** 


## `POST /api/session/reset_password`

Reset password with a reset token.

##### PARAMS:

*  **`token`** value must be a non-blank string.

*  **`password`** Insufficient password strength


## `GET /api/setting/`

Get all `Settings` and their values. You must be a superuser to do this.

You must be a superuser to do this.


## `GET /api/setting/:key`

Fetch a single `Setting`. You must be a superuser to do this.

You must be a superuser to do this.

##### PARAMS:

*  **`key`** value must be a non-blank string.


## `PUT /api/setting/:key`

Create/update a `Setting`. You must be a superuser to do this.
   This endpoint can also be used to delete Settings by passing `nil` for `:value`.

You must be a superuser to do this.

##### PARAMS:

*  **`key`** value must be a non-blank string.

*  **`value`** 


## `GET /api/setup/admin_checklist`

Return various "admin checklist" steps and whether they've been completed. You must be a superuser to see this!

You must be a superuser to do this.


## `POST /api/setup/`

Special endpoint for creating the first user during setup.
   This endpoint both creates the user AND logs them in and returns a session ID.

##### PARAMS:

*  **`engine`** 

*  **`allow_tracking`** 

*  **`email`** value must be a valid email address.

*  **`first_name`** value must be a non-blank string.

*  **`request`** 

*  **`password`** Insufficient password strength

*  **`name`** 

*  **`is_full_sync`** 

*  **`site_name`** value must be a non-blank string.

*  **`token`** Token does not match the setup token.

*  **`details`** 

*  **`last_name`** value must be a non-blank string.


## `POST /api/setup/validate`

Validate that we can connect to a database given a set of details.

##### PARAMS:

*  **`engine`** value must be a valid database engine.

*  **`host`** 

*  **`port`** 

*  **`details`** 

*  **`token`** Token does not match the setup token.


## `PUT /api/slack/settings`

Update Slack related settings. You must be a superuser to do this.

You must be a superuser to do this.

##### PARAMS:

*  **`slack-token`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`metabot-enabled`** value must be a boolean.

*  **`slack-settings`** 


## `GET /api/table/`

Get all `Tables`.


## `GET /api/table/:id`

Get `Table` with ID.

##### PARAMS:

*  **`id`** 


## `GET /api/table/:id/fks`

Get all foreign keys whose destination is a `Field` that belongs to this `Table`.

##### PARAMS:

*  **`id`** 


## `GET /api/table/:id/query_metadata`

Get metadata about a `Table` useful for running queries.
   Returns DB, fields, field FKs, and field values.

  By passing `include_sensitive_fields=true`, information *about* sensitive `Fields` will be returned; in no case
  will any of its corresponding values be returned. (This option is provided for use in the Admin Edit Metadata page).

##### PARAMS:

*  **`id`** 

*  **`include_sensitive_fields`** value may be nil, or if non-nil, value must be a valid boolean (true or false).


## `PUT /api/table/:id`

Update `Table` with ID.

##### PARAMS:

*  **`id`** 

*  **`display_name`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`entity_type`** value may be nil, or if non-nil, value must be one of: `event`, `person`, `photo`, `place`.

*  **`visibility_type`** value may be nil, or if non-nil, value must be one of: `cruft`, `hidden`, `technical`.

*  **`description`** 

*  **`caveats`** 

*  **`points_of_interest`** 

*  **`show_in_getting_started`** 


## `GET /api/tiles/:zoom/:x/:y/:lat-field-id/:lon-field-id/:lat-col-idx/:lon-col-idx/`

This endpoints provides an image with the appropriate pins rendered given a MBQL QUERY (passed as a GET query string param).
   We evaluate the query and find the set of lat/lon pairs which are relevant and then render the appropriate ones.
   It's expected that to render a full map view several calls will be made to this endpoint in parallel.

##### PARAMS:

*  **`zoom`** value must be a valid integer.

*  **`x`** value must be a valid integer.

*  **`y`** value must be a valid integer.

*  **`lat-field-id`** value must be an integer greater than zero.

*  **`lon-field-id`** value must be an integer greater than zero.

*  **`lat-col-idx`** value must be a valid integer.

*  **`lon-col-idx`** value must be a valid integer.

*  **`query`** value must be a valid JSON string.


## `DELETE /api/user/:id`

Disable a `User`.  This does not remove the `User` from the db and instead disables their account.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `GET /api/user/`

Fetch a list of all active `Users` for the admin People page.


## `GET /api/user/:id`

Fetch a `User`. You must be fetching yourself *or* be a superuser.

##### PARAMS:

*  **`id`** 


## `GET /api/user/current`

Fetch the current `User`.


## `POST /api/user/`

Create a new `User`, or or re??ctivate an existing one.

You must be a superuser to do this.

##### PARAMS:

*  **`first_name`** value must be a non-blank string.

*  **`last_name`** value must be a non-blank string.

*  **`email`** value must be a valid email address.

*  **`password`** 


## `POST /api/user/:id/send_invite`

Resend the user invite email for a given user.

You must be a superuser to do this.

##### PARAMS:

*  **`id`** 


## `PUT /api/user/:id`

Update a `User`.

##### PARAMS:

*  **`id`** 

*  **`email`** value must be a valid email address.

*  **`first_name`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`last_name`** value may be nil, or if non-nil, value must be a non-blank string.

*  **`is_superuser`** 


## `PUT /api/user/:id/password`

Update a user's password.

##### PARAMS:

*  **`id`** 

*  **`password`** Insufficient password strength

*  **`old_password`** 


## `PUT /api/user/:id/qbnewb`

Indicate that a user has been informed about the vast intricacies of 'the' QueryBuilder.

##### PARAMS:

*  **`id`** 


## `GET /api/util/logs`

Logs.

You must be a superuser to do this.


## `GET /api/util/stats`

Anonymous usage stats. Endpoint for testing, and eventually exposing this to instance admins to let them see
  what is being phoned home.

You must be a superuser to do this.


## `POST /api/util/password_check`

Endpoint that checks if the supplied password meets the currently configured password complexity rules.

##### PARAMS:

*  **`password`** Insufficient password strength