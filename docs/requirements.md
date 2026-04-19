# Requirements

## User Needs

### User stories
TODO: Write brief user stories to explain how various actors would interact with the system to accomplish a goal.
    Express these in the form from agile development:- As a (role) I want (goal) so that (benefit).

    -> As a user, i want to choose my role to get tags/data relevant to me.
    -> As a user, i want to choose a ward to view specific data related to that location.
    -> As a user, i want to be able to search for wards by their qualities and quickly get relevant wards as ranked results.
    -> As a user, i want to choose tags to filter the data being viewed.
    -> As a user, i want to visualize the data with visual elements to understand the results easier.

### Actors
    User - The user accesses the system to perform actions like searching/selecting, filtering and viewing Bristol Open Data by choosing roles, wards and data types.
    There are various users in the system, such as Mover, Business and Resident. The user types have no substantial impact on the working of the system, and hence the user actors are generally termed as one "User" actor in the system.

    The user types are as follows:

    Mover - The user who's interested in moving to other places
    Business - The user who's interested in business data by ward
    Resident - The user who's interested in the resident area they live in

### Use Cases

  | UC1 -- Select Role                     |                                                                                                                                                                     |
|----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| UC1                                    | Select Role                                                                                                                                                         |
| Description                            | The user will choose a role, either Mover, Business, or Resident, to personalize the experience and influence available data options.                               |
| Actors                                 | User                                                                                                                                                                |
| Assumptions                            | The system is accessible via a supported web browser                                                                                                                |
| Steps                                  | 1. User opens the application → 2. System displays role options → 3. User selects a role → 4. System stores the selected role and proceeds to the next page         |
| Variations                             | The user can continue as a guest without choosing a specific role.                                                                                                  |
| Non-functional                         | The chosen role should be processed immediately.                                                                                                                    |
| Issues                                 | Role selection does not significantly change system functionality                                                                                                   |
|                                        |                                                                                                                                                                     |
| UC2 -- Select Ward (Map interaction)   |                                                                                                                                                                     |
| UC2                                    | Select Ward                                                                                                                                                         |
| Description                            | The user chooses a ward through the interactive map interface                                                                                                       |
| Actors                                 | User                                                                                                                                                                |
| Assumptions                            | The map loads correctly and displays all wards                                                                                                                      |
| Steps                                  | 1. User navigates to map page → 2. System displays ward map → 3. User hovers or clicks a ward → 4. System captures and stores the selected ward                     |
| Variations                             | Alternatively, the user could utilize the search functionality (UC3)                                                                                                |
| Non-functional                         | Map interaction should respond within 1 second                                                                                                                      |
| Issues                                 | Usability of the map can differ based on the device being used                                                                                                      |
|                                        |                                                                                                                                                                     |
| UC3 -- Search and Rank Wards           |                                                                                                                                                                     |
| UC3                                    | Search Wards                                                                                                                                                        |
| Description                            | The user searches for wards using keywords, and the system ranks results based on relevance.                                                                        |
| Actors                                 | User                                                                                                                                                                |
| Assumptions                            | The system has access to api ward data and keyword mappings                                                                                                         |
| Steps                                  | 1. User enters search query → 2. System processes keywords → 3. API call is made → 4. System ranks wards using scoring logic → 5. Results are displayed to the user |
| Variations                             | In case no matches are made, the results will display wards alphabetically by default.                                                                              |
| Non-functional                         | Results should be displayed within 2 seconds                                                                                                                        |
| Issues                                 | Ranking accuracy depends on limited predefined keywords                                                                                                             |
|                                        |                                                                                                                                                                     |
| UC4 -- Select Tags (Dataset Filtering) |                                                                                                                                                                     |
| UC4                                    | Select Tags                                                                                                                                                         |
| Description                            | The user selects one or more tags to filter, datasets that will be fetched.                                                                                         |
| Actors                                 | User                                                                                                                                                                |
| Assumptions                            | Tags are correctly mapped to datasets                                                                                                                               |
| Steps                                  | 1. System displays available tags → 2. User selects one or more options → 3. System stores selected tags → 4. Tags are passed to the next stage                     |
| Variations                             | Depending on the role selected on page 1, ""suggested tags"" are shown to bring forward tags of interest for the user type                                          |
| Non-functional                         | Tags may be grouped into topics.                                                                                                                                    |
| Issues                                 | Some tags may map to the same dataset or worse, one tag trying to fetch multiple datasets                                                                           |
|                                        |                                                                                                                                                                     |
| UC5 -- View Ranked Data (All wards)    |                                                                                                                                                                     |
| UC5                                    | View Ranked Data                                                                                                                                                    |
| Description                            | The user views one or more graphs, each representing ranking of all wards for the selected tag(s). E.g. crime                                                       |
| Actors                                 | User                                                                                                                                                                |
| Assumptions                            | At least one tag has been selected on page 3.                                                                                                                       |
| Steps                                  | 1. System receives selected tags → 2. System maps tags to datasets → 3. API calls are made → 4. Data is processed → 5. Graphs displaying ranked results are shown   |
| Variations                             | If data is unavailable, a message is displayed                                                                                                                      |
| Non-functional                         | Data should load within 3 seconds                                                                                                                                   |
| Issues                                 | Dependent on API availability, sensitive to different naming convensions in different datasets                                                                      |
|                                        |                                                                                                                                                                     |
| UC6 -- View Ward-Specific Data         |                                                                                                                                                                     |
| UC6                                    | View Ward Data                                                                                                                                                      |
| Description                            | The user sees detailed information about a selected ward depending on the tags selected.                                                                            |
| Actors                                 | User                                                                                                                                                                |
| Assumptions                            | A ward and at least one tag have been selected                                                                                                                      |
| Steps                                  | 1. User selects ward → 2. User selects tags → 3. System sends data via URL → 4. API calls are made → 5. Data is processed → 6. Results are displayed as graphs      |
| Variations                             | A message is displayed if no information is available.                                                                                                              |
| Non-functional                         | Visualisations should render clearly on phones                                                                                                                      |
| Issues                                 | Reliability of the latest data depends on an External API                                                                                                           |



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
