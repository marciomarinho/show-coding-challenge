# Coding Challenge

Welcome to the Coding Challenge! To complete this challenge, you will need to write and deploy a simple JSON-based web service, and provide us the URL.

**Note:** As this is also an exercise in setup and deployment, please don't solve this by adding an endpoint to an existing app. The service should be standalone and deployed at the root path - e.g. `http://myservice.herokuapp.com/`

## The Challenge

This challenge is based on a simplified version of a catch-up TV service. The service provides a list of shows, and you need to filter that list based on some criteria.

The goal is to write and deploy a simple JSON-based web service in Golang, and provide the final URL.

It's pretty simple. A POST request will be sent to the URL provided. The request will contain a JSON payload, and the service should return a JSON response.

As part of the requirements, the response data needs to be filtered, and return a few fields.

Here's an example request and an example response.

### Example Request Payload
```json
{
  "payload": [
    {
      "country": "UK",
      "description": "What's life like when you have enough children to field your own football team?",
      "drm": true,
      "episodeCount": 3,
      "genre": "Reality",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/16KidsandCounting1280.jpg"
      },
      "language": "English",
      "nextEpisode": null,
      "primaryColour": "#ff7800",
      "seasons": [
        {
          "slug": "show/16kidsandcounting/season/1"
        }
      ],
      "slug": "show/16kidsandcounting",
      "title": "16 Kids and Counting",
      "tvChannel": "GEM"
    },
    {
      "slug": "show/seapatrol",
      "title": "Sea Patrol",
      "tvChannel": "Channel 9"
    },
    {
      "country": " USA",
      "description": "The Taste puts 16 culinary competitors in the kitchen, where four of the World's most notable culinary masters of the food world judges their creations based on a blind taste. Join judges Anthony Bourdain, Nigella Lawson, Ludovic Lefebvre and Brian Malarkey in this pressure-packed contest where a single spoonful can catapult a contender to the top or send them packing.",
      "drm": true,
      "episodeCount": 2,
      "genre": "Reality",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/TheTaste1280.jpg"
      },
      "language": "English",
      "nextEpisode": {
        "channel": null,
        "channelLogo": "http://catchup.ninemsn.com.au/img/player/logo_go.gif",
        "date": null,
        "html": "<br><span class=\"visit\">Visit the Official Website</span></span>",
        "url": "http://go.ninemsn.com.au/"
      },
      "primaryColour": "#df0000",
      "seasons": [
        {
          "slug": "show/thetaste/season/1"
        }
      ],
      "slug": "show/thetaste",
      "title": "The Taste (Le Goût)",
      "tvChannel": "GEM"
    },
    {
      "country": "UK",
      "description": "The series follows the adventures of International Rescue, an organisation created to help those in grave danger using technically advanced equipment and machinery. The series focuses on the head of the organisation, ex-astronaut Jeff Tracy, and his five sons who piloted the \"Thunderbird\" machines.",
      "drm": true,
      "episodeCount": 24,
      "genre": "Action",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/Thunderbirds_1280.jpg"
      },
      "language": "English",
      "nextEpisode": null,
      "primaryColour": "#0084da",
      "seasons": [
        {
          "slug": "show/thunderbirds/season/1"
        },
        {
          "slug": "show/thunderbirds/season/3"
        },
        {
          "slug": "show/thunderbirds/season/4"
        },
        {
          "slug": "show/thunderbirds/season/5"
        },
        {
          "slug": "show/thunderbirds/season/6"
        },
        {
          "slug": "show/thunderbirds/season/8"
        }
      ],
      "slug": "show/thunderbirds",
      "title": "Thunderbirds",
      "tvChannel": "Channel 9"
    },
    {
      "country": "USA",
      "description": "A sleepy little village, Crystal Cove boasts a long history of ghost sightings, poltergeists, demon possessions, phantoms and other paranormal occurrences. The renowned sleuthing team of Fred, Daphne, Velma, Shaggy and Scooby-Doo prove all of this simply isn't real, and along the way, uncover a larger, season-long mystery that will change everything.",
      "drm": true,
      "episodeCount": 4,
      "genre": "Kids",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/ScoobyDoo1280.jpg"
      },
      "language": "English",
      "nextEpisode": null,
      "primaryColour": "#1b9e00",
      "seasons": [
        {
          "slug": "show/scoobydoomysteryincorporated/season/1"
        }
      ],
      "slug": "show/scoobydoomysteryincorporated",
      "title": "Scooby-Doo! Mystery Incorporated",
      "tvChannel": "GO!"
    },
    {
      "country": "USA",
      "description": "Toy Hunter follows toy and collectibles expert and dealer Jordan Hembrough as he scours the U.S. for hidden treasures to sell to buyers around the world. In each episode, he travels from city to city, strategically manoeuvring around reluctant sellers, abating budgets, and avoiding unforeseen roadblocks.",
      "drm": true,
      "episodeCount": 2,
      "genre": "Reality",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/ToyHunter1280.jpg"
      },
      "language": "English",
      "nextEpisode": null,
      "primaryColour": "#0084da",
      "seasons": [
        {
          "slug": "show/toyhunter/season/1"
        }
      ],
      "slug": "show/toyhunter",
      "title": "Toy Hunter",
      "tvChannel": "GO!"
    },
    {
      "country": "AUS",
      "description": "A series of documentary specials featuring some of the world's most frightening moments, greatest daredevils and craziest weddings.",
      "drm": true,
      "episodeCount": 1,
      "genre": "Documentary",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/Worlds1280.jpg"
      },
      "language": "English",
      "nextEpisode": null,
      "primaryColour": "#ff7800",
      "seasons": [
        {
          "slug": "show/worlds/season/1"
        }
      ],
      "slug": "show/worlds",
      "title": "World's...",
      "tvChannel": "Channel 9"
    },
    {
      "country": "USA",
      "description": "Another year of bachelorhood brought many new adventures for roommates Walden Schmidt and Alan Harper. After his girlfriend turned down his marriage proposal, Walden was thrown back into the dating world in a serious way. The guys may have thought things were going to slow down once Jake got transferred to Japan, but they're about to be proven wrong when a niece of Alan's, who shares more than a few characteristics with her father, shows up at the beach house.",
      "drm": true,
      "episodeCount": 0,
      "genre": "Comedy",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/TwoandahHalfMen_V2.jpg"
      },
      "language": "English",
      "nextEpisode": {
        "channel": null,
        "channelLogo": "http://catchup.ninemsn.com.au/img/player/Ch9_new_logo.gif",
        "date": null,
        "html": "Next episode airs: <span> 10:00pm Monday on<br><span class=\"visit\">Visit the Official Website</span></span>",
        "url": "http://channelnine.ninemsn.com.au/twoandahalfmen/"
      },
      "primaryColour": "#ff7800",
      "seasons": null,
      "slug": "show/twoandahalfmen",
      "title": "Two and a Half Men",
      "tvChannel": "Channel 9"
    },
    {
      "country": "USA",
      "description": "Simmering with supernatural elements and featuring familiar and fan-favourite characters from the immensely popular drama The Vampire Diaries, it's The Originals. This sexy new series centres on the Original vampire family and the dangerous vampire/werewolf hybrid, Klaus, who returns to the magical melting pot that is the French Quarter of New Orleans, a town he helped build centuries ago.",
      "drm": true,
      "episodeCount": 1,
      "genre": "Action",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/TheOriginals1280.jpg"
      },
      "language": "English",
      "nextEpisode": {
        "channel": null,
        "channelLogo": "http://catchup.ninemsn.com.au/img/player/logo_go.gif",
        "date": null,
        "html": "<br><span class=\"visit\">Visit the Official Website</span></span>",
        "url": "http://go.ninemsn.com.au/"
      },
      "primaryColour": "#df0000",
      "seasons": [
        {
          "slug": "show/theoriginals/season/1"
        }
      ],
      "slug": "show/theoriginals",
      "title": "The Originals",
      "tvChannel": "GO!"
    },
    {
      "country": "AUS",
      "description": "Join the most dynamic TV judging panel Australia has ever seen as they uncover the next breed of superstars every Sunday night. UK comedy royalty Dawn French, international pop superstar Geri Halliwell, (in) famous Aussie straight-talking radio jock Kyle Sandilands, and chart -topping former AGT alumni Timomatic.",
      "drm": false,
      "episodeCount": 0,
      "genre": "Reality",
      "image": {
        "showImage": "http://catchup.ninemsn.com.au/img/jump-in/shows/AGT.jpg"
      },
      "language": "English",
      "nextEpisode": {
        "channel": null,
        "channelLogo": "http://catchup.ninemsn.com.au/img/player/Ch9_new_logo.gif",
        "date": null,
        "html": "Next episode airs:<span>6:30pm Sunday on<br><span class=\"visit\">Visit the Official Website</span></span>",
        "url": "http://agt.ninemsn.com.au"
      },
      "primaryColour": "#df0000",
      "seasons": null,
      "slug": "show/australiasgottalent",
      "title": "Australia's Got Talent",
      "tvChannel": "Channel 9"
    }
  ],
  "skip": 0,
  "take": 10,
  "totalRecords": 75
}
```

### Example Response
```json
{
  "response": [
    {
      "image": "http://catchup.ninemsn.com.au/img/jump-in/shows/16KidsandCounting1280.jpg",
      "slug": "show/16kidsandcounting",
      "title": "16 Kids and Counting"
    },
    {
      "image": "http://catchup.ninemsn.com.au/img/jump-in/shows/TheTaste1280.jpg",
      "slug": "show/thetaste",
      "title": "The Taste (Le Goût)"
    },
    {
      "image": "http://catchup.ninemsn.com.au/img/jump-in/shows/Thunderbirds_1280.jpg",
      "slug": "show/thunderbirds",
      "title": "Thunderbirds"
    },
    {
      "image": "http://catchup.ninemsn.com.au/img/jump-in/shows/ScoobyDoo1280.jpg",
      "slug": "show/scoobydoomysteryincorporated",
      "title": "Scooby-Doo! Mystery Incorporated"
    },
    {
      "image": "http://catchup.ninemsn.com.au/img/jump-in/shows/ToyHunter1280.jpg",
      "slug": "show/toyhunter",
      "title": "Toy Hunter"
    },
    {
      "image": "http://catchup.ninemsn.com.au/img/jump-in/shows/Worlds1280.jpg",
      "slug": "show/worlds",
      "title": "World's..."
    },
    {
      "image": "http://catchup.ninemsn.com.au/img/jump-in/shows/TheOriginals1280.jpg",
      "slug": "show/theoriginals",
      "title": "The Originals"
    }
  ]
}
```

## Requirements

### Filtering Logic
From the list of shows in the request payload, return the ones with:
- DRM enabled (`drm: true`)
- At least one episode (`episodeCount > 0`)

The returned JSON should have a `response` key with an array of shows. Each element should have the following fields from the request:
- `image` - corresponding to `image/showImage` from the request payload
- `slug`
- `title`

### Error Handling
If we send invalid JSON, you need to return a JSON response with HTTP status `400 Bad Request`, and with an `error` key containing the string `Could not decode request`. For example:

```json
{
    "error": "Could not decode request: JSON parsing failed"
}
```

## Technical Implementation

Although this is a simple exercise, we'll be looking for:
- Simple, well-designed code
- Proper testing
- Clean architecture
- Good error handling

## Deployment

Your service must be deployed as a standalone application accessible at the root path. The deployment should be automated and the service should be publicly accessible for testing.

## Useful Resources

- [JSON Specification](https://www.json.org/)
- [HTTP Status Codes](https://httpstatuses.com/)
- [REST API Design Best Practices](https://restfulapi.net/)

## Solution

### Golang Microservice

I build a Golang microservice that fulfill the requirements, using the following technologies:
- Golang
- Gin framework
- Go test
- Docker
- Docker Compose
- DynamoDB local / AWS DynamoDB
- AWS CodeBuild

Project : https://github.com/marciomarinho/show-service

### Terraform AWS Infrastructure ( IaC )
The AWS infrastructure to host the service as been designed, developed and deployed using Terraform, as having infrastructure as code ( IaC ) approach makes it easier to manage and maintain the infrastructure. Allowing us to have a consistent environment and to be able to replicate it easily, and a repeatable process.

The following resources have been created:
- Cognito User Pool
- VPC
- VPC Link
- Subnets
- Security Group
- CodeBuild
- ECS Cluster Fargate / Serverless
- IAM Roles
- S3 Bucket
- API Gateway
- CloudWatch
- DynamoDB Table

Project : https://github.com/marciomarinho/show-service-infra