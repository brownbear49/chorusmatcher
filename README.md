# chorusmatcher

Matches folder names with results from https://chorus.fightthe.pw/ 

## Installation and Usage
`pip install chorusmatcher`

`chorusmatcher <PATH_TO_FOLDER> <PATH_TO_OUTPUT>` (default is `./`)

Additional options :

```
-v or --verbose: shows progress/status of execution

-m <int> or --mode <int> : changes mode of lookup
    0 (Default): Displays song name and link
    1 (Song name only): Displays song name
    2 (Raw): Displays all fields
    3 (Custom): Specify fields to include
    
-i or --include: specify which fields to include (comma-separated), to be used with mode=3
```

### Example usage :

`chorusmatcher ./music` - Reads folder names from `./music` directory

`chorusmatcher ./music ./output` - Reads folder names from `./music` directory, outputs in `./output`

`chorusmatcher ./music -m 1` - Changes output to fetch song names only

`chorusmatcher ./music ./output -m 3 -i link,genre,tier_guitar` - Fetches `link`, `genre` and `tier_guitar` fields (Full list under 'songs': https://github.com/Paturages/chorus)


### Example outputs:
```
Folder structure:

music/
├─ Rihanna/
├─ Eminem/

```

`chorusmatcher ./music`
```
[
    {
        "artist": "Eminem",
        "number": 7,
        "songs": [
            {
                "Song": "Berzerk",
                "link": "https://drive.google.com/file/d/12NbK-xeuODylTGKLAERkjI-juhvWaU6B/view?usp=drivesdk"
            },
            {
                "Song": "The Real Slim Shady",
                "link": "https://drive.google.com/drive/folders/1WuOHm1e06Jk5UyKToE2qNoZVVZnrMCzR"
            },
            {
                "Song": "Sing For The Moment",
                "link": "https://drive.google.com/file/d/1yXdR3eXr4Bvj77NCPXbQBvyj2lWe1Nbt/view?usp=drivesdk"
            },
            {
                "Song": "The Way I Am",
                "link": "https://drive.google.com/drive/folders/1yIgYSSG4ixeO5fnQBo8vJU97DcI79XZ8"
            },
            {
                "Song": "River (Tech Death Cover)",
                "link": "https://drive.google.com/file/d/1ZSvs6LykecJq0X_xGkZWJcqYeYt6fCSo/view?usp=drivesdk"
            },
            {
                "Song": "Survival",
                "link": "https://drive.google.com/drive/folders/1MAJ7aCrLKpOUJFHY9XojJ625YTwptY36"
            },
            {
                "Song": "Without Me (Nokia Version)",
                "link": "https://drive.google.com/file/d/1TFyS3jmvx0H70ra8Db0pMK6L7flxIipB/view?usp=drivesdk"
            }
        ]
    },
    {
        "artist": "Rihanna",
        "number": 2,
        "songs": [
            {
                "Song": "Hate That I Love You (feat. Ne-Yo)",
                "link": "https://drive.google.com/drive/folders/1Nupm04HhxKZxZa7obItbhzQKREttpIt5"
            },
            {
                "Song": "Love On The Brain",
                "link": "https://drive.google.com/file/d/194Va4oiswXBsVg6_TOYWk5hoDHm9yXaT/view?usp=drivesdk"
            }
        ]
    }
]
```


`chorusmatcher ./music -m 1`
```
[
    {
        "artist": "Eminem",
        "number": 7,
        "songs": [
            "Berzerk",
            "The Real Slim Shady",
            "Sing For The Moment",
            "The Way I Am",
            "River (Tech Death Cover)",
            "Survival",
            "Without Me (Nokia Version)"
        ]
    },
    {
        "artist": "Rihanna",
        "number": 2,
        "songs": [
            "Hate That I Love You (feat. Ne-Yo)",
            "Love On The Brain"
        ]
    }
]
```

`chorusmatcher ./music -m 3 -i genre,year,tier_guitar,diff_guitar`
```
[
    {
        "artist": "Eminem",
        "number": 7,
        "songs": [
            {
                "Song": "Berzerk",
                "genre": "Hip-Hop",
                "year": "2013",
                "tier_guitar": 1,
                "diff_guitar": 15
            },
            {
                "Song": "The Real Slim Shady",
                "genre": "Hip Hop",
                "year": "2000",
                "tier_guitar": 1,
                "diff_guitar": 8
            },
            {
                "Song": "Sing For The Moment",
                "genre": "Rap",
                "year": "2002",
                "tier_guitar": null,
                "diff_guitar": 8
            },
            {
                "Song": "The Way I Am",
                "genre": "Hip-Hop",
                "year": "2000",
                "tier_guitar": 2,
                "diff_guitar": 8
            },
            {
                "Song": "River (Tech Death Cover)",
                "genre": "Technical Death Metal",
                "year": "2018",
                "tier_guitar": 4,
                "diff_guitar": 8
            },
            {
                "Song": "Survival",
                "genre": "Alternative",
                "year": "2013",
                "tier_guitar": null,
                "diff_guitar": null
            },
            {
                "Song": "Without Me (Nokia Version)",
                "genre": "Memes",
                "year": "2020",
                "tier_guitar": 1,
                "diff_guitar": 8
            }
        ]
    },
    {
        "artist": "Rihanna",
        "number": 2,
        "songs": [
            {
                "Song": "Hate That I Love You (feat. Ne-Yo)",
                "genre": "Pop",
                "year": "2008",
                "tier_guitar": 2,
                "diff_guitar": 15
            },
            {
                "Song": "Love On The Brain",
                "genre": "R&B",
                "year": "2016",
                "tier_guitar": 0,
                "diff_guitar": 8
            }
        ]
    }
]
```