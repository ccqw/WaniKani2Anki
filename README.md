# NihongoTools
A set of utility scripts for simplifying Japanese language study.

While the current focus is on the WaniKani API, I plan to add features that make use of the [Forvo API](https://forvo.com) for additional capacity to do native audio imports, and other APIs and libraries. Suggestions of valuable sources to integrate are very welcome.

## Current Inventory
- The first scripts I am working on are for getting data out of WaniKani and into your Anki database for custom usage. WaniKani is awesome, and I want the chance to do things besides kanji/radicals/vocabulary -> English with their excellent study materials, like focus on reading the example sentences. I hope this growing collection of scripts helps others to do the same.

## Why me, why this?
Right now this project has a single author, me, Caitlin Quintero Weaver.

My undergraduate study was focused in linguistics, and I have always loved studying a variety of languages. I continued my language education in Russian at the graduate level. I also completed graduate-level studies in new media and interaction. My career is as a Cloud infrastructure engineer. I have been interested in the Japanese language from around the age of 12, although better than intermittent dedication to study came somewhat more recently. I am interested in a scientific approach to language learning and I believe that learning languages generally is a skill that one can improve, and that there are techniques that are more and less effective. I also believe in using technology in a constructive and focused way. I hope my automation and integration efforts help other people to learn better and enjoy life.

## Usage Notes

### Colophon
- This project is written in [Python3](https://www.python.org/downloads/)
- Python dependencies are managed with [Pipenv](https://pipenv.pypa.io/en/latest/)
- Configuration (including secrets like the WaniKani API key) is provided to the application as environment variables, as per the [Twelve-Factor App](https://12factor.net) approach
- `jq` is the library in use for querying and reshaping JSON data

### Privileges
When [creating your WaniKani API key](https://www.wanikani.com/settings/personal_access_tokens) for use with these scripts, a read-only token is perfectly sufficient, so you may leave all extra privilege boxes unchecked to created your key.

### Credentials
However you decide to run these scripts, you will need to provide your own `.env` file:

```
cp example.env .env
# open in your preferred text editor
# and paste in your own WaniKani API key as the value of API_KEY
vim .env
```

Note that the `MAX_LEVEL` may also be customized. You will likely prefer to enter your current level. 3 is the highest WaniKani level that is available without a paid subscription.

### Docker build and run

```
# e.g., supply the tag as appropriate:
docker build ./ -t wanikani-get-sentences:v0.0.1
# supply your .env file and which script to run
docker run --env-file .env wanikani-get-sentences:v0.0.1 ./get-sentences.py
```

### Local Python run

```
# within directory WaniKani2Anki/
pipenv shell  # pipenv will export the contents of your .env file for you
pipenv sync  # ensure packages are installed and up to date
python3 get-vocab-sentences/get-sentences.py  # run whatever script you like
```
