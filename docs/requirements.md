# Requirements

## User Needs

### User stories

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

| USE-CASE ID    | USE-CASE NAME                                                                                                                                                       |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| UC1            | Select Role                                                                                                                                                         |
| Description    | The user will choose a role, either Mover, Business, or Resident, to personalize the experience and influence available data options.                               |
| Actors         | User                                                                                                                                                                |
| Assumptions    | The system is accessible via a supported web browser                                                                                                                |
| Steps          | 1. User opens the application → 2. System displays role options → 3. User selects a role → 4. System stores the selected role and proceeds to the next page         |
| Variations     | The user can continue as a guest without choosing a specific role.                                                                                                  |
| Non-functional | The chosen role should be processed immediately.                                                                                                                    |
| Issues         | Role selection does not significantly change system functionality                                                                                                   |
|                |                                                                                                                                                                     |
| UC2            | Select Ward (Map interaction)                                                                                                                                       |
| Description    | The user chooses a ward through the interactive map interface                                                                                                       |
| Actors         | User                                                                                                                                                                |
| Assumptions    | The map loads correctly and displays all wards                                                                                                                      |
| Steps          | 1. User navigates to map page → 2. System displays ward map → 3. User hovers or clicks a ward → 4. System captures and stores the selected ward                     |
| Variations     | Alternatively, the user could utilize the search functionality (UC3)                                                                                                |
| Non-functional | Map interaction should respond within 1 second                                                                                                                      |
| Issues         | Usability of the map can differ based on the device being used                                                                                                      |
|                |                                                                                                                                                                     |
| UC3            | Search and Rank Wards                                                                                                                                               |
| Description    | The user searches for wards using keywords, and the system ranks results based on relevance.                                                                        |
| Actors         | User                                                                                                                                                                |
| Assumptions    | The system has access to api ward data and keyword mappings                                                                                                         |
| Steps          | 1. User enters search query → 2. System processes keywords → 3. API call is made → 4. System ranks wards using scoring logic → 5. Results are displayed to the user |
| Variations     | In case no matches are made, the results will display wards alphabetically by default.                                                                              |
| Non-functional | Results should be displayed within 2 seconds                                                                                                                        |
| Issues         | Ranking accuracy depends on limited predefined keywords                                                                                                             |
|                |                                                                                                                                                                     |
| UC4            | Select Tags (Dataset Filtering)                                                                                                                                     |
| Description    | The user selects one or more tags to filter, datasets that will be fetched.                                                                                         |
| Actors         | User                                                                                                                                                                |
| Assumptions    | Tags are correctly mapped to datasets                                                                                                                               |
| Steps          | 1. System displays available tags → 2. User selects one or more options → 3. System stores selected tags → 4. Tags are passed to the next stage                     |
| Variations     | Depending on the role selected on page 1, ""suggested tags"" are shown to bring forward tags of interest for the user type                                          |
| Non-functional | Tags may be grouped into topics.                                                                                                                                    |
| Issues         | Some tags may map to the same dataset or worse, one tag trying to fetch multiple datasets                                                                           |
|                |                                                                                                                                                                     |
| UC5            | View Ranked Data (All wards)                                                                                                                                        |
| Description    | The user views one or more graphs, each representing ranking of all wards for the selected tag(s). E.g. crime                                                       |
| Actors         | User                                                                                                                                                                |
| Assumptions    | At least one tag has been selected on page 3.                                                                                                                       |
| Steps          | 1. System receives selected tags → 2. System maps tags to datasets → 3. API calls are made → 4. Data is processed → 5. Graphs displaying ranked results are shown   |
| Variations     | If data is unavailable, a message is displayed                                                                                                                      |
| Non-functional | Data should load within 3 seconds                                                                                                                                   |
| Issues         | Dependent on API availability, sensitive to different naming convensions in different datasets                                                                      |
|                |                                                                                                                                                                     |
| UC6            | View Ward-Specific Data                                                                                                                                             |
| Description    | The user sees detailed information about a selected ward depending on the tags selected.                                                                            |
| Actors         | User                                                                                                                                                                |
| Assumptions    | A ward and at least one tag have been selected                                                                                                                      |
| Steps          | 1. User selects ward → 2. User selects tags → 3. System sends data via URL → 4. API calls are made → 5. Data is processed → 6. Results are displayed as graphs      |
| Variations     | A message is displayed if no information is available.                                                                                                              |
| Non-functional | Visualisations should render clearly on phones                                                                                                                      |
| Issues         | Reliability of the latest data depends on an External API                                                                                                           |


<img width="1031" height="741" alt="usecase" src="https://github.com/user-attachments/assets/5bd09de4-8dc6-47a3-b9c8-fd4cd4b578b9" />


## Software Requirements Specification
### Functional requirements
    FR1 (UC1), The system must allow the user to select a role and store it for use across pages
    FR2 (UC2), The system must allow the user to select a ward using an interactive map
    FR3 (UC3), The system must allow the user to search for wards using keywords
    FR4 (UC3), The system must rank wards based on keyword relevance using a scoring system
    FR5 (UC4), The system must allow the user to select one or more tags to filter data
    FR6 (UC4), The system must map selected tags to corresponding datasets
    FR7 (UC5, UC6), The system must retrieve data from external APIs based on selected tags and/or ward
    FR8 (UC5, UC6), The system must process retrieved data into a usable format
    FR9 (UC6), The system must display ward-specific data based on selected ward and tags

    FR10 (UC5), The system should display ranked data for all wards based on selected tags
    FR11 (UC5, UC6), The system should present data using graphical visualisations
    FR12 (UC2, UC3), The system should allow multiple navigation paths (map and search)

    FR13 (UC4), The system could suggest relevant tags based on selected role
    FR14 (UC4), The system could allow users to refine or reset their selections
    FR15 (UC2), The system could highlight wards dynamically on map interaction

    FR16 (N/A), The system won’t include user account creation or login functionality
    FR17 (N/A), The system won’t store user data persistently in a database
    FR18 (N/A), The system won’t provide real-time live data updates


### Non-Functional Requirements
    NFR1 (UC5, UC6), The system must load and display API data within 3 seconds under normal conditions
    NFR2 (UC1–UC6), The system must function correctly on modern web browsers (e.g. Chrome, Edge)
    NFR3 (UC5, UC6), The system must handle failed API responses gracefully

    NFR4 (UC1–UC6), The system should allow users to complete key tasks within 3–5 interactions
    NFR5 (UC1–UC6), The system should display correctly on mobile devices

    NFR6 (UC5, UC6), The system could enhance visual clarity with improved styling and layout
    NFR7 (UC5, UC6), The system could optimise performance for lower-end devices
