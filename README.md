# Red vs Blue

Welcome to the Red vs Blue workshop illustrating the power of the Pivotal Platform!

# The Game

![Red vs Blue - a form of Dodgeball](dodgeball.gif "Red vs Blue - a form of Dodgeball")

In this workshop, we will play a little game of throwing balls at each other.
This is how the workshop is technically set up:

![Red vs Blue Workshop Architecture](architecture.png "Red vs Blue Workshop Architecture")

As you can see, all the apps and services will be deployed and running on the Pivotal Platform.
Let's go over the different parts of the diagram.

# Preparing your Workstation

Depending on which of the two teams you intent to participate in, you will have
to install some additional tools on your local workstation.

At the least, you will have to install the Cloud Foundry CLI. Instructions and
links to the downloadable installer can be found [here](https://docs.pivotal.io/pivotalcf/2-3/cf-cli/install-go-cli.html).

Depending on which team you intent to be part of, you will also need to install
the appropriate other tools, like e.g. Maven, Java JDK, etc.

# Referee

The referee has been created to act as sort of validator and score keeper in the Red vs Blue game.
The app validates teams throwing balls at each other by reading messages from the message broker, and registers the hits in the database.

The referee offers a UI to keep track of the top players and their scores.
It will simply update every second to show a realtime overview of the game.

![Red vs Blue Workshop UI](referee-ui.png "Red vs Blue Workshop UI")

The referee also offers an API that exposes player information and their scores.
You will need to consume this API to build your player app.

## Referee API

The referee API is generated by [Spring REST Docs](https://spring.io/projects/spring-restdocs), a Spring library that generates REST API documentation during integration tests.
When the integration tests fail, the documentation is not generated.
This means that, if the integration tests are comprehensive enough and cover all the REST API codebase, the documentation will always be up-to-date with the actual API.

[Referee API Documentation](https://referee.apps.pcfone.io/docs/index.html)

## Run the Referee application

### Locally

To run the referee application locally, execute the following command in a new terminal window in the referee folder:

```bash
./mvnw spring-boot:run
```

### On the Pivotal Platform

To see how the Referee service gets built and deployed to the Pivotal Platform, play the `./demo.sh` script in the `referee` folder.

# Players

Players will be creating an application that can throw balls at players from the other team by sending messages over a message broker.
Each player is either in Team Red or Team Blue.

# Java Player

Read the instructions in the [java-player](/java-player/README.md) README.
When you get lost, check out the solution in [java-player-solution](/java-player-solution).

# Python Player

Read the instructions in the [python-player](/python-player/README.md) README.
When you get lost, check out the solution in [python-player-solution](/python-player-solution).
