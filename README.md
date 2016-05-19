# Twitch Usernames Dataset

scraped by querying [random streams](https://www.twitch.tv/directory/random)
and then querying who those streamers are following.

this was done every 5 minutes for roughly 62 hours: 2016-05-15 to 2016-05-18.

## bias

the scraping method biases towards
those who are more likely to be followed,
or seen streaming during the scraping period.

follower lists (as opposed to following) were not queried.
one could query this themselves if they desire.

## intent

to feed into [a neural network][torch-rnn] for shits and giggles.

apologies to anyone who expected a formal procedure.

[torch-rnn]: https://github.com/jcjohnson/torch-rnn

## raw json responses

each response from the server was saved in its original json format.
however, usernames that appeared more than once on the random stream queries
would have their following json files overwritten by the newer versions
— not too big of a deal.

this data might be uploaded at some point.
it currently stands at 2 GiB for the half-million dataset.

## notes on usernames

the json responses contain two username formats: `display_name` and `name`.

`display_name` contains the username with additional formatting,
such as capitalization and sometimes spaces.

it's possible that the display name doesn't resemble the username at all,
due to names given by twitch staff to large sponsored streams (think MOBA).
i haven't yet checked this for certain.

`name` contains the raw username, satisfying the regular expression:  
`[a-z0-9][a-z0-9_]{3,24}`

the `name` field was used for this dataset.

## TODO

* finish writing this readme

* upload json data

* upload scraping scripts

* upload million user dataset (when we get there)
