# TOGoS's M3U Extensions

## M3U Directives

Some of these are already used by [Playlister](http://www.nuke24.net/projects/Playlister/).
Others are hypothetical.


### URN

Can be used by [Playlister](http://www.nuke24.net/projects/Playlister/) and
can be generated by [CCouch3](https://github.com/TOGoS/ContentCouch3)'s annotate-m3u command.

Indicate a URN for the following item.
Multiple URNs may be specified.

Example:
```
#EXTINF:95,togtrackaday - 2d
#URN:urn:bitprint:RSNAUJ4X7TC2XMMCJHKZIX5Q7WC6SW3F.XVT65BCHCU2V24CASERH4VX5HTQV2UGK52RRRKY
http://music-files.nuke24.net/uri-res/raw/urn:bitprint:RSNAUJ4X7TC2XMMCJHKZIX5Q7WC6SW3F.XVT65BCHCU2V24CASERH4VX5HTQV2UGK52RRRKY/togtrackaday-2008.06.16-2d.mp3
```


### GLUE

A #GLUE line between two tracks indicates that those two tracks should always be played back-to-back with no transition between. This is useful for indicating that songs from an album with built-in transitions should always stick together, e.g. when chopping up playlists. This is actually short for #TRANSITION:glue.


### TRANSITION

Indicates the desired transition from the previous song. When not present, it can be assumed that the songs are independent and can be transitioned however.

Possible values:

- ```undefined``` - same as defining no transition. The tracks may be treated as unrelated.
- ```glue``` - the tracks should be considered attached and always played back-to-back.
- ```glue,remove-silence``` - the tracks should be considered attached
  and always played back-to-back with any silence between them (at the
  end of the first or beginning of the second) track removed (useful
  because MP3 files sometimes contain unwanted silence at the ends of
  tracks due to limitations of the format)


### RDFATTR

As of 2019-11-19, not used by anything.

Associate an RDF attribute with the following item or group.

Format: ```#RDFATTR <property ref> <value>```.
References (including the property itself) should include angle brackets,
and literal strings in quotes with backslash escapes, a la Turtle or N-triples

Could be used to associate album art with an album (the album being represented as a group).


## BEGINGROUP

As of 2019-11-19, not used by anything.

Opens a group of items, which may themselves be groups.
Can be used to represent albums or other groups of tracks.


## ENDGROUP

As of 2019-11-19, not used by anything.

Closes a group of items.


## Examples

```
#EXTM3U
#RDFATTR <http://ns.nuke24.net/SomethingSomething/coverArt> <urn:bitprint:AGQCM5X4GJPOGZ7JPIDJD4QVBEYA6X2X.QUY7QGVOFCY4Z3ZPT72D6WS5G4TTIUGAYHDIGCY>
#BEGINGTROUP
#EXTINF:233,Wintergatan - Sommarf├Ñgel
#URN:urn:bitprint:XV7MMDNKBX26BQPMYITCTCJCMLXB3TXO.FQANOK3P4KBPXN2XJ457NGSQ7GEZZCHJAYCD5OY
01-Wintergatan-Sommarfagel.ogg
#EXTINF:211,Wintergatan - The Rocket
#URN:urn:bitprint:RQN6BTZT6TQXA2D3TPLF6XGBRSB6KFUY.DBSUEDUW3PFMHYGCHA75UKLCH3UBVGVZQJ7YC7A
02-Wintergatan-The_Rocket.ogg
#EXTINF:239,Wintergatan - Valentine
#URN:urn:bitprint:VC6OMOV4SHQWY2OUZMVFFOEOMDTWEJUH.33NA7K7RNYXDZL7AZUKCSXHOII7S3XN7CTXV6NY
03-Wintergatan-Valentine.ogg
#EXTINF:213,Wintergatan - Slottskogen Disc Golf Club
#URN:urn:bitprint:GXSYIOZTA27IXWUZ2AQDFMQWADI4AV4I.27G56JN7QVYSZUQTZOO7OZY7VBSAOB7QODHNFCY
04-Wintergatan-Slottskogen_Disc_Golf_Club.ogg
#EXTINF:208,Wintergatan - Biking Is Better
#URN:urn:bitprint:GMTEHTP7NRHEJZENJF7NPF22D6P6QNTY.SE7C7KSCZAFC5R3FLZONU47OOIKZX4XJGKMY32Q
05-Wintergatan-Biking_Is_Better.ogg
#EXTINF:266,Wintergatan - V├ñstanberg
#URN:urn:bitprint:YO7ZUX5UCX7S6YXLQ6VZ67ECEDM67AKN.MUQF224TYBUNINIIOAIUOTOZA6GPZOVWQTK5OWA
06-Wintergatan-Vastanberg.ogg
#EXTINF:243,Wintergatan - Starmachine2000
#URN:urn:bitprint:2JXTK532NPHJFIGXVIV75VFVXUTR2UWS.HVR6CGF2RAPISBD2NJII6LAOBWE2DVMUTDGZNUQ
07-Wintergatan-Starmachine2000.ogg
#EXTINF:183,Wintergatan - All Was Well
#URN:urn:bitprint:DVDP77YTRBPFMGS2TTKO77NSD3VHMX6F.DV53NE7MWMVW6VRHZ3LTTIPHCTK47VKZVKI6IEI
08-Wintergatan-All_Was_Well.ogg
#EXTINF:851,Wintergatan - Paradis
#URN:urn:bitprint:BAZEYS6VC4A2672WGYUU5KPDBSRBLA4R.DUGWMKN3RP3WVOMF6GUV4F7F4TJYEGS4WPH4YHA
09-Wintergatan-Paradis.ogg
#ENDGROUP
```
Maybe see also: http://musicontology.com/specification/
