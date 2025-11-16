# Requirements

## User Needs

### User stories
TODO: Write brief user stories to explain how various actors would interact with the system to accomplish a goal.
    Express these in the form from agile development:- As a (role) I want (goal) so that (benefit).

    -> As a business i want regional, relevant data so that we can choose between locations to open business chains
    -> As a potential mover, i want regional and relevant data so that i can choose a good place for me/my family to move to
    -> As a resident i want relevant data on the area i live in so that i can get a better understanding of my area

### Actors
    -> Mover, is someone who is looking to move to a new location and needs relevant data to make a decision 
    -> Business, is an entity which is looking to open new locations for their business and need relevant data to select the best candidate (area) 
    -> resident, is someone who is already in an area but would like to look into details of the area they live in

### Use Cases

    | UC1 | The mover | 
    | -------------------------------------- | ------------------- |
    | This user, is looking to move from their current area (anywhere in the world) to a new area, this website will present the user with information about the areas they are interested in, so that they can make an educated decision on where they move to, be it with family or by themselves | TODO: Goal to be achieved by use case and sources for requirement |

    | Mover | Individuals, couples or domestic families or friends |

    | Assumptions include: 1) The user is using a browser which can support the website's acitvities
                       2) The data presented to the user is up-to date
                       3) Any information taken from the user is secure
                       4) The user has a general idea of what relivent data they are looking to compare
                       5) The website is able to access and display the data from the database | TODO: Pre/post-conditions if any</td></tr>
                       
    | First the user chooses either to enter the website via login or as a guest, then the user has to choose between 3 types of User types "1)Mover, 2)Business, 3)resident", in this case the user picks "mover". Then user is asked to type our the area they are looking for, the system matches it with the database and displays the given location on an interactable map, from here the user can look into areas they are interested in and compare the relivent data such as crime rates, household income, available hospitals etc. and can also go into further detailed page about a specific location. | TODO: Interactions between actors and system necessary to achieve goal |

    | For variations, the use might choose to log in, the user might know exactly which area they want to look into or they might need a broader comparisan, of cities and even countries. If the user has family, things like closest school, saloon etc may be things they would compare, while someone who would move alone might care more about information on the job market and their personal needs. | TODO: OPTIONAL - Any variations in the steps of a use case |

    | NFR1, The system may have account settings for regular use | TODO: OPTIONAL - List of non-functional requirements that the use case must meet. |
    | System's readablility of the dataset | TODO: OPTIONAL - List of issues that remain to be resolved |


    | UC2 | The Business | 
    | -------------------------------------- | ------------------- |
    | This user, is a business big enough that they are looking to open business in new locations (supermarkets, fast food chains etc), this website will present the business with information about the areas they are interested in, so that they can make an educated decision on which area they choose to invest in | TODO: Goal to be achieved by use case and sources for requirement |

    | Business | TODO: List of actors involved in use case |

    | Assumptions include: 1) The user is using a browser which can support the website's acitvities
                       2) The data presented to the user is up-to date
                       3) Any information taken from the user is secure
                       4) The user has a general idea of what relivent data they are looking to compare
                       5) The website is able to access and display the data from the database | TODO: Pre/post-conditions if any</td></tr>
                       
    | First the user chooses either to enter the website via login or as a guest, then the user has to choose between 3 types of User types "1)Mover, 2)Business, 3)resident", in this case the user picks "Business". Then user is asked to type our the area they are looking for, the system matches it with the database and displays the given location on an interactable map, from here the user can look into areas they are interested in and compare the relivent data such as house hold income, construction companies, cost of transportation in the area, crime rates etc. and can also go into further detailed page about a specific location. | TODO: Interactions between actors and system necessary to achieve goal |

    | For variations, the use might choose to log in, the user might know exactly which area they want to look into or they might need a broader comparisan, of cities and even countries. Different types of business, care about different things when it comes to opening a new location, some might look for an optical place for restocking (fastfood chains), while others might care more about comparing mental health between areas (Therapist business) | TODO: OPTIONAL - Any variations in the steps of a use case |

    | NFR1, The system may have account settings for regular use | TODO: OPTIONAL - List of non-functional requirements that the use case must meet. |
    | System's readablility of the dataset | TODO: OPTIONAL - List of issues that remain to be resolved |


    | UC3 | The resident | 
    | -------------------------------------- | ------------------- |
    | This user, is already in a location they are happy to stay in, but are looking know more about their current area and comparing it to other locations, this website will present the user with information about the areas they are interested to look into. | TODO: Goal to be achieved by use case and sources for requirement |

    | resident | TODO: List of actors involved in use case |

    | Assumptions include: 1) The user is using a browser which can support the website's acitvities
                       2) The data presented to the user is up-to date
                       3) Any information taken from the user is secure
                       4) The user has a general idea of what relivent data they are looking to compare
                       5) The website is able to access and display the data from the database | TODO: Pre/post-conditions if any</td></tr>
                       
    | First the user chooses either to enter the website via login or as a guest, then the user has to choose between 3 types of User types "1)Mover, 2)Business, 3)Recident", in this case the user picks "resident". Following this, the user is asked to let the website access their location (must), the system matches it with the database and displays the given location on an interactable map, from here the user can look into aspects of the area they are interested in and compare the relivent data such as crime rates, household income, available hospitals etc. to other areas and can also go into further detailed page about a specific location. | TODO: Interactions between actors and system necessary to achieve goal |

    | For variations, the use might choose to log in, the user might not allow the location request in which case the use is given a zoomed out map. If the user has family, things like closest school, saloon etc may be things they would compare, while someone who would move alone might care more about information on the job market and their personal needs. | TODO: OPTIONAL - Any variations in the steps of a use case |

    | NFR1, The system may have account settings for regular use | TODO: OPTIONAL - List of non-functional requirements that the use case must meet. |
    | System's readablility of the dataset | TODO: OPTIONAL - List of issues that remain to be resolved |


TODO: Your Use-Case diagram should include all use-cases.

![Insert your Use-Case Diagram Here](images/use-case.png)

## Software Requirements Specification
### Functional requirements
    FR1, The system should take the location of the resident
    FR2, The system may take the location of the Mover and the business
    FR3, The system must be able to run in the selected brouser software
    FR4, The system should get the user to select a location for inspection
    FR5, The system must show relivent data for the user type
    FR6, The system should be able to display graphs using the dataset
    FR7, the sytem must be able to access the data from the dataset
    FR8, The system must get the user type from user

### Non-Functional Requirements
    NFR1, The system may have account settings for regular use
    NFR2, The system should show a high resolution image of the map
    NFR3, The website must work in mobile
    NFR4, The website may suggest different areas, incase not enough desired, area requirements are found in an area

Indicate which UC the requirement comes from.
