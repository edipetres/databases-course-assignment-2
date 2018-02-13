# Twitter Dataset Analysis

This project is an analysis of a dataset with 1.600.000 tweets. A mongodb container instance is running with Docker and it stores the data extracted from the `.csv` file of the dataset. These tweets are analysed to find the asnwers to the questions presented in the assignment. You can see the output in the [Results](#results) below.

## Prerequisites

The following CLI tools are required to run this project:

- docker
- git
- python3

If you don't have python3 installed, try changing it to python in the `setup.sh` script - however, I cannot guarantee it will run on python 2.

## Getting started

Once you cloned the repo and cd'd into it run the `setup.sh` script to get started

```sh
./setup.sh
```

This command will extract the dataset. It spins up a mongo database locally in a Docker container with a data volume mounted to the `data` folder. Then it populates the database with the extracted dataset. Finally, it runs the Python script to analyse the data and prints out the results.

## Results

The program should output the following results

```sh
Top 5 happy users (positive words found):
[('syarif_m2e', 79),
 ('manatmouse', 76),
 ('Jeff_Hardyfan', 55),
 ('thalovebug', 49),
 ('shanajaca', 42)]

Top 5 mad users (negative words found):
[('BondServantLZ', 24),
 ('mr_apollo', 12),
 ('fuckz', 10),
 ('swearingwatcher', 7),
 ('alexrapa', 7)]

1. Individual twitter users: 659774

2. Users with most links to other users:
[('Hollywood_Trey', 9),
 ('PamsLove', 7),
 ('tweetpet', 7),
 ('omgwtfannie', 6),
 ('loris_sl', 6),
 ('RoseStack', 5),
 ('gavlp', 5),
 ('jeremy_ellis', 5),
 ('Roonaldo107', 5),
 ('amysav83', 5)]

 # EDIT: I removed the limitation left in the code that made it only check 10.000 tweets
 # The result of querying the entire db for question 2:
 [('tweetpet', 310),
 ('lost_dog', 131),
 ('nuttychris', 82),
 ('keren4562', 74),
 ('mcraddictal', 69),
 ('kasey79', 50),
 ('Djalfy', 44),
 ('tsarnick', 41),
 ('sebby_peek', 39),
 ('ComedyQueen', 37)]

3. Most mentioned users
[('mileycyrus', 23),
 ('Kal_Penn', 15),
 ('stephenkruiser', 13),
 ('JonathanRKnight', 12),
 ('heidimontag', 12)]

 # EDIT: The same is the case with question 3. Please see the full results:
 3. Most mentioned users
[('mileycyrus', 403),
 ('tommcfly', 402),
 ('ddlovato', 285),
 ('DavidArchie', 150),
 ('mitchelmusso', 116)]

4. Most active Twitter users:
[('lost_dog', 549),
 ('webwoke', 345),
 ('tweetpet', 310),
 ('SallytheShizzle', 281),
 ('VioletsCRUK', 279),
 ('mcraddictal', 276),
 ('tsarnick', 248),
 ('what_bugs_u', 246),
 ('Karen230683', 238),
 ('DarkPiano', 236)]
```

## Notes

The sentiment analysis is not quite sophisticated. We take a list of happy and sad words and compare to each word in the tweets. While some words carry a negative meaning, the tweets might still have a positive attitude as a whole.

I had difficulty appending the id's to the beginning of the dataset (the `sed` command did not work on my machine) hence I kept the zipped training data in the repository. Sorry for the slow download time.
