# Implementation

## Introduction
### System Overview
This system is a client-side, multi-page web application, which allows a user to browse and analyze data at a ward level in Bristol. The inputs required from a user include the user’s role, ward name, and data tags. These inputs are then passed in the URL of the application and used to dynamically retrieve and visualise data from external APIs.

### Dataset Description
The platform utilizes the Bristol Open Data API that offers its data sets in JSON format, commonly in GeoJSON format. The data set has features array, with each feature being a ward level record containing attributes (e.g. crime statistics, population metrics).

A total of 16 datasets are used, derived from an initial selection of 48 datasets, refined through filtering and mapping into 24 user-facing tags. Some tags share datasets but use pre-filtered API queries to reduce unnecessary data processing.

### Known Issues
Several limitations arise from the external API:

  1) Inconsistent ward identifiers (e.g. WARD, WARD_NAME)
  2) No standard schema across datasets
  3) Some datasets contain multiple irrelevant numeric fields

To handle this, the system uses fallback logic and dynamically selects usable numeric values, though this may not always represent the most meaningful metric.

### Configuration Data
The configuration of mapping used by the system is the (pissbot). In it, there is a unique mapping between the ID of the tag and the respective API URL. This mapping will enable the dynamic selection of datasets depending on the user’s choice.

## Project Structure
### Folder Structure 
<img width="750" height="750" alt="image" src="https://github.com/user-attachments/assets/bae9d3b5-2e42-4fd6-8609-3cf861948f45" />


### Jslint warnings

### Explaintion
The project follows a modular page-based structure where each file corresponds to a specific stage in the user journey. Separation of concerns is achieved by distributing responsibilities across pages, such as input collection (page 1, 2, 3, 4), processing (page 5, 6, 7), and visualisation (page 5, 7).

## Software Architecture

### Architechture Style
The system follows a client-side, data-driven architecture with elements of event-driven design. It is also stateless, as user data is passed between pages using URL parameters rather than persistent storage.

### Component Defination
| Component             | Responsibility                            |
| --------------------- | ----------------------------------------- |
| UI Layer              | User interaction (forms, map, checklists) |
| State Management      | URL parameter handling                    |
| Navigation Controller | Page transitions                          |
| Data Fetch Layer      | API calls via `fetch()`                   |
| Processing Layer      | Ranking, filtering, transformation        |
| Visualisation Layer   | Chart.js rendering                        |
| Configuration Layer   | Tag → dataset mapping                     |

### Explaination
The system separates concerns into distinct layers. User input is captured in the UI layer and passed through the navigation controller using URL parameters. The data fetch layer retrieves external datasets, which are processed and transformed before being rendered in the visualisation layer. This design ensures flexibility, allowing multiple user flows (map-based or search-based) to reach the same processing endpoints.

### Diagram

## Bristol Open Data API
### Class Diagrams
<img width="1293" height="772" alt="1" src="https://github.com/user-attachments/assets/abbed73c-8cd2-435f-bf0b-6cec7ba9e9f9" />
<img width="1053" height="636" alt="2" src="https://github.com/user-attachments/assets/c3abb008-0b7a-402a-9485-41352031f180" />
<img width="1405" height="782" alt="3" src="https://github.com/user-attachments/assets/8822ab46-7724-4277-8d05-a4891fc37676" />
<img width="1362" height="751" alt="4" src="https://github.com/user-attachments/assets/25edf21d-67b8-4bfb-903c-46c9a5113992" />

### Structure explaination
All datasets follow a similar structure:

   1) "features[] → array of records"
   2) "attributes{} → contains data values"

# User guide
TODO: Explain how each use-case works by providing step-by-step screenshots for each use-case. This should be based on a tested scenario.

## UC1 – Select Role
Steps:

   1) Open application
   2) Select “Mover”
   3) Redirect to map

Expected Result: 

   --> URL contains role=Mover
<img width="1920" height="1080" alt="1" src="https://github.com/user-attachments/assets/e731fb6d-4056-47c9-97a3-a67277ee87e5" />

## UC2 – Map Selection
Steps:

   1) Hover over Map
   2) Choose highlighted ward
   3) Redirect to tag selection
      
Expected resilts: 
    --> URL contains ward=Ward_ID&wardN=Ward_Name
    <img width="1920" height="1080" alt="2" src="https://github.com/user-attachments/assets/caf7221e-4e08-4e94-ae58-c4af811ac11d" />

## UC3 – Search and scoring system
Steps:

   1) Search key words
   2) Url forwards the search term
   3) System processes and scores the key words 
      
Expected resilts: 
    --> Wards listed by their name, code and keywords, dynamically apear by score
<img width="1920" height="1080" alt="5" src="https://github.com/user-attachments/assets/f9befba0-b945-43d9-8767-6af75359bce9" />
<img width="1920" height="1080" alt="6" src="https://github.com/user-attachments/assets/4e59fc99-bc52-4454-9c1a-6c6d846af9e6" />

## UC4 – Tag selelction (page 3 and 4)
Steps:

   1) Page loads a checklist with the list of 24 tags
   2) Click on interesting tags
   3) Each tag links to a dataset
      
Expected resilts: 
    --> Url forwards e.g "info=1&info=9&info=19&info=..."
<img width="1920" height="1080" alt="3" src="https://github.com/user-attachments/assets/e5174689-069d-4fde-9c7a-a4769350ee7f" />
<img width="1920" height="1080" alt="7" src="https://github.com/user-attachments/assets/8cd9765e-81ac-4c23-ac27-c9fda499d0d2" />

## UC5 – Ward Ranking by tag
Steps:

   1) Reads url e.g "info=1&info=9&info=19&info=..."
   2) Creates an arrey of strings
   3) Data is pulled using fetch() and filtered
      
Expected resilts: 
    --> Page displays 1 chart for each tag, ranking wards by tags/topics
 <img width="1920" height="1080" alt="8" src="https://github.com/user-attachments/assets/3b6b3453-bbb5-479c-af64-e024c26830d4" />
   
## UC6 – Data visulatisation sorted by ward
Steps:

   1) Reads url e.g "info=1&info=9&info=19&info=..." and "ward=Ward_ID&wardN=Ward_Name"
   2) Data is pulled using fetch() and filtered by ward
   3) Using the ward data, chart.js creates one pi chart and one bar graph
      
Expected resilts: 
    --> Page displays data of the selected tags by ward
  <img width="1920" height="1080" alt="4" src="https://github.com/user-attachments/assets/5eccb4b3-e424-4d57-bd1b-d0c1178d657c" />
  
