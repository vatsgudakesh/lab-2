# Lab - 2

### Use-Case Diagram:

```
@startuml
left to right direction
actor "User" as user
actor "Administrator" as admin
rectangle Homemade-Recipebowl{
  usecase "Login" as L
  usecase "Display\nLogin Error" as L1
  usecase "Verification" as L2

  usecase "Input" as I
  usecase "Text" as I1
  usecase "Image" as I2
  usecase "Cuisine" as I3
  usecase "Recipe\nRating" as I4

  usecase "Display\nInvalid Input\nError" as err

  usecase "ML Model 1" as ML1
  usecase "ML Model 2" as ML2
  usecase "Database" as db

}

user --> L
user --> I

(L) .> (L2) : include
(L1) .> (L) : extends

(err) .> (I) : extends

I1 --> I
I2 --> I
I3 --> I
I4 --> I

(I1) .> (ML1) : include
(I2) .> (ML2) : include
(I3) .> (db) : include

admin --> L
admin --> ML1
admin --> ML2
admin --> db
@enduml

```

![Use-Case Diagram](https://github.com/ankitgoyal0301/Software-Testing-18103018/blob/main/Lab-1/Use%20Case%20Diagram.png)

PlantUML Link to Use-Case Diagram: [Homemade-Recipebowl(Use-Case Diagram)](https://www.plantuml.com/plantuml/png/RPA_RlCW5CLtdk8gKpBaaqmoVKEKggrK96U9savPiBbnhuGX0jm_glhknSPkSDNj-7SkXtkGzpv85xfMCutd0C62e-ObW2A7TI1hcAo3TR1uykWM83rqKKpmHhLao0SdWqskx0dhpqhJQ8G7ss8h5QwFMDC5A_kcFndq8RNq28lIDcI6asMExyXVjFmucS67U-V6_BB8nvxHqPbgsI-QR1xjV4AOInS6I-Ju4Tz7EiiJhMmmSPxpsuuycT7Pv4wgTJ976SWqQM3B_gmYpAlKf61OwMIkdT2vNriVIZXOXHgAOU2GjSvTFhfyTfyCiefgy5J5s1TZqNImNk-Wl4h1sB9SmRyTB4k-Wlz0fjQTmaYB4VSqFXGQvUCmEfUuc75HZ762Js8pYUtFJMBCZ5LcTma-SJxdcyHLbMCs_5wfIQPZwEoBPr_z2-pHgAxLtm00)

### Sequence Diagram:

```
@startuml
actor User as user
participant "Homemade\nRecipebowl" as hr
participant "Server" as server
database "Trained Model/\nRecipes Database" as db


user -> hr: User Login
user -> hr: Ingredients/Image Input

hr -> server: Verify Login
hr -> server: Verify Input

alt If login is valid

    server --> hr: Login Valid
    hr --> user: Successfully Logged in

else Else

    server --> hr: Login Invalid
    hr --> user: Login Unsuccessful

end

alt If Input is valid

    server --> hr: Valid Input
    hr -> server: User Input
    server -> db: User Input
    db --> server: Recipes Generated
    server --> hr: Recipes Generated
    hr -> user: Recipes

else Else

    server --> hr: Invalid Input
    hr -> user: Re-enter Input

end

user -> hr: Cuisine Input
hr -> server: Cuisine Input
server -> db: Cuisine Input

db --> server: Recipes Fetched
server --> hr: Recipes Fetched
hr -> user: Recipes

user -> hr: Favorite Recipes
hr -> server: Favorite Recipes
server --> hr: Added to Favorites
hr --> user: Added to Favorites
@enduml

```

![Sequence Diagram](https://github.com/ankitgoyal0301/Software-Testing-18103018/blob/main/Lab-1/Sequence%20Diagram.png)

PlantUML Link to Sequence Diagram: [Homemade-Recipebowl(Sequence Diagram)](https://www.plantuml.com/plantuml/png/XP8_Ry8m4CLtVueJEs9dgAZQqaPgbrAOkZYv8x7aECX_KlNRr_7XIeQKCW3oxzsxvvTid9VMXruBsVZ1mjwH1UaWn5znYaWrwYIDXyNBq5ClaJxDEyKpgeSllPYatOLmHtOacv1BVmLABslf21OVLYf326y3abvbAmUFPqMQmbg045C2MDv5-pMdUXrQPOhZohIMK97nRbNrigLuSWfUY2v9UFiQ3cJLyPldPr4Uazf3TGGz2K4v6ALMA0J43m_0aZUp5nmcdd37A3YAS1UQXfmx1gtJrfOGucP1sX4ynQyRbfKPvqqPxutxDO-61dDeliBDq1oNXGaNLN376URPIO3r5SGwcURH_1IVoP2Ldd1k-wme4iXNp8h_YkAAYeiK9aioFgVbZegNvY4efmoTUTb1oSeAIYR-g61Blka8HP7v6izTkqYvbUDWbQTCYw0p-6BVFI8X-24BpmQySvwB3HaClVu1)
