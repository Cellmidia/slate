# GET /users/{id}/info

+ Request (application/json)

    + Headers

            Authorization: Bearer YourTokenComesHere
            Accept: application/json

    + Body

            {
                "name": "Perry",
                "lastLogin": "2016-07-18T12:02:59-03:00",
                "summary": {
                    "product": "Plano SMS",
                    "messages": {
                        "total": 300,
                        "sent": 10
                    },
                    "contacts": {
                        "total": 230,
                        "new": 15
                    },
                    "actions": {
                        "total": 10
                    },
                    "groups": {
                        "total": 25,
                        "new": 3
                    }
                }
            }



