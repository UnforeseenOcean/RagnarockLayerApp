# Ragnarock WebSocket API documentation 
## because I'm too impatient

```
{"event": "StartSong", "data": {"SongName":"Dewey","SongBand":"Celkilt"}}
```
I've started the song. You can see that I've picked the shortest song in the game, because as I said, I'm impatient.

```
{"event": "BeatHit", "data": {"delta":"-0.000854","time":"165.500656"}}
{"event": "BeatHit", "data": {"delta":"0.010429","time":"168.500671"}}
```
`BeatHit` event looks like this, `delta` contains the timing delta from the ideal timing, both negative and positive number. `time` contains global time in song.
```
{"event": "BeatMiss", "data": {"delta":"0.0","time":"123.833992"}}
```
Because ~~you~~ I play badly, there are some missed notes. That's okay, the robot overlords have noted it.

`delta` value can be ignored, since it's always 0.0 anyway. `time` contains global time in song.
```
{"event": "ComboTriggered", "data": {"level":1}}
```
Congratulations to me, I've managed to hit the combo. Probably when you hit the yellow combo (full combo) the `level` parameter would go up?
```
{"event": "ComboLost", "data": {"lostAt":"0.616667"}}
```
Aw shucks, I lost the combo. As you can see, `lostAt` contains the timing delta from the ideal time to hit the notes.
```
{"event": "DrumHit", "data": {"intensity":0.291987,"hand":"Right"}}
{"event": "DrumHit", "data": {"intensity":0.582399,"hand":"Left"}}
```
As you can see, `DrumHit` event contains info about intensity (0.000001~1.000000) and which hand hit it. It does not know which drum it has hit. Yet.
```
{"event": "EndSong", "data": {}}
```
After the absolute clown show of a race is over, this event is sent to the client. There's no data, so don't worry about accessing it.
```
{
   "event":"Score",
   "data":{
      "stats":{
         "PercentageOfPerfects":39,
         "ComboBlue":3,
         "ComboYellow":0,
         "Missed":5,
         "Hit":211,
         "HitPercentage":98,
         "HitDeltaAverage":11
      },
      "extra":{
      },
      "distance":"1555.403809"
   }
}
```
The `Score` event contains both `stats` and `distance` attributes, which you can quickly access at the end of the race (which is when this event will fire.)