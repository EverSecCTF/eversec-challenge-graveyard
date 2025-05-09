# eversec-challenge-graveyard
Public repository for retired challenges

## TL;DR
We make a lot of challenges for CTF events and after we run them once or twice (with revisions), we don't have much use for them. This repo is public and intended for learning purposes. 

No promises that these will be maintained in the long term. 

## How to run a challenge with Docker
In the directory of the challenge (i.e. Challenges>cheerio), run:
`docker build . -t cheerio`

`docker run --rm -it -p 3000:3000/tcp cheerio:latest`

See Docker examples here: https://docs.docker.com/get-started/docker-concepts/building-images/build-tag-and-publish-an-image/

### Solutions
Each challenge folder should have a `solutions.md` file. Don't look at it if you want to don't want to be spoiled.
