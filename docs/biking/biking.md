This table can be used to indicate the rules of using transit with a bicycle.

# The table

## `bicycle_rules.txt`
This table defines the actual rules.

It contains the following fields:

Field name|Field type|Field details
:-|:-|:-
**`rule_sort_order`**|Required: Integer|The order in which to apply the rules. Applicable rules are applied to a trip in order from lowest to highest, and override the trip's own `bikes_allowed` value. These values must be unique.
`agency_id`|ID referencing [`agency.agency_id`](https://developers.google.com/transit/gtfs/reference/#agencytxt)|The ID of the agency whose routes to which a rule applies.
`route_type`|Enum, same as [`routes.route_type`](https://developers.google.com/transit/gtfs/reference/#routestxt)|The route type to which a rule applies.
`route_id`|ID referencing [`routes.route_id`](https://developers.google.com/transit/gtfs/reference/#routestxt)|The ID of the route to which a rule applies. If set, `agency_id` and `route_type` are ignored, whether or not they match this route.
`direction_id`|Enum, same as [`trips.direction_id`](https://developers.google.com/transit/gtfs/reference/#tripstxt)|The route direction to which a rule applies.
`trip_id`|ID referencing [`trips.trip_id`](#https://developers.google.com/transit/gtfs/reference/tripstxt)|The ID of the trip to which a rule applies. If set, `agency_id`, `route_id`, `route_type`, and `direction_id` are ignored, whether or not they match this trip.
`period_id`|ID referencing [`periods.period_id`](../common/periods.md#periodstxt)|The period of time during which this rule applies.
`after_stop_id`|ID referencing [`stops.stop_id`](https://developers.google.com/transit/gtfs/reference/#stopstxt)|The ID of the stop after which this rule is applied. The rule includes the specified stop.
`before_stop_id`|ID referencing [`stops.stop_id`](https://developers.google.com/transit/gtfs/reference/#stopstxt)|The ID of the stop before which this rule is applied. The rule includes the specified stop.
`at_stop_id`|ID referencing [`stops.stop_id`](https://developers.google.com/transit/gtfs/reference/#stopstxt)|The ID of the stop at which this rule is exclusively applied. Can also be used by itself when indicating a station rule.
`bikes_allowed`|Enum|For a route:<ul><li>`0`: Bikes may not be carried on the vehicle.</li><li>`1`: At least one bike may be carried on the vehicle.</li></ul> For a station:<ul><li>`0`: Bikes may not be present within the station.</li><li>`1`: Bikes may be present within the station.</li></ul>
`bike_capacity`|Integer|The maximum number of bikes that can be carried by the vehicle at this time.
`bike_boarding`|Enum|For a route:<ul><li>`0`: Bikes may not board the vehicle here.</li><li>`1`: Bikes may board the vehicle here.</li></ul> For a station:<ul><li>`0`: Bikes may not board vehicles from this station.</li><li>`1`: Bikes may board vehicles from this station.</li></ul>
`bike_deboarding`|Enum|For a route:<ul><li>`0`: Bikes may not deboard the vehicle here.</li><li>`1`: Bikes may deboard the vehicle here.</li><li>`2`: Bikes *must* deboard the vehicle here.</li></ul> For a station:<ul><li>`0`: Bikes may not deboard vehicles into this station.</li><li>`1`: Bikes may deboard vehicles into this station.</li></ul>Please be aware of local laws that may make this unenforceable.
`bike_entry`|Enum|Ignored for routes. For stations:<ul><li>`0`: Bikes may not enter the station from the street.</li><li>`1`: Bikes may enter the station from the street.</li></ul>
`bike_exit`|Enum|Ignored for routes. For stations:<ul><li>`0`: Bikes may not exit the station to the street.</li><li>`1`: Bikes may exit the station to the street.</li><li>`2`: Bikes *must* exit the station to the street.</li></ul>

Be sure to specify all the rules that change as each individual rule will inherit its last value.