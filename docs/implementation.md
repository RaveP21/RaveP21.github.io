# Implementation

## Introduction
TODO: Describe the system implemented (Describe the dataset. Are there any known issues? Describe any configuration data).

### System Overview
The system is a client-side, multi-page web application that enables users to explore and analyse ward-level data for Bristol. It collects three key inputs—user role, ward, and data tags—which are passed through the application via URL parameters and used to dynamically retrieve and visualise data from external APIs.

### Dataset Description
The system integrates with the Bristol Open Data API, which provides datasets in JSON format, typically structured as GeoJSON. Each dataset contains a features array, where each feature represents a ward-level record with associated attributes (e.g. crime statistics, population metrics).

A total of 16 datasets are used, derived from an initial selection of 48 datasets, refined through filtering and mapping into 24 user-facing tags. Some tags share datasets but use pre-filtered API queries to reduce unnecessary data processing.

### Known Issues
Several limitations arise from the external API:

  1) Inconsistent ward identifiers (e.g. WARD, WARD_NAME)
  2) No standard schema across datasets
  3) Some datasets contain multiple irrelevant numeric fields

To handle this, the system uses fallback logic and dynamically selects usable numeric values, though this may not always represent the most meaningful metric.

### Configuration Data
The system uses a configuration mapping object (pissbot) that links each tag ID to a specific API endpoint. This allows dynamic dataset selection based on user input and acts as the core mechanism connecting frontend interaction to backend data retrieval.

## Project Structure
TODO: Provide an outline of the project folder structure and the role of each file within it.
provide a table listing the number of jslint warnings/reports for each module.

### Folder Structure 
<img width="750" height="750" alt="image" src="https://github.com/user-attachments/assets/bae9d3b5-2e42-4fd6-8609-3cf861948f45" />


### Jslint warnings

### Explaintion
The project follows a modular page-based structure where each file corresponds to a specific stage in the user journey. Separation of concerns is achieved by distributing responsibilities across pages, such as input collection (page 1, 2, 3, 4), processing (page 5, 6, 7), and visualisation (page 5, 7).

## Software Architecture
TODO: Describe the major components of your architecture. Are any particular architectural styles being used?

### Architechture Style
The system follows a client-side, data-driven architecture with elements of event-driven design. It is also stateless, as user data is passed between pages using URL parameters rather than persistent storage.

### Component Defination

### Explaination
The system separates concerns into distinct layers. User input is captured in the UI layer and passed through the navigation controller using URL parameters. The data fetch layer retrieves external datasets, which are processed and transformed before being rendered in the visualisation layer. This design ensures flexibility, allowing multiple user flows (map-based or search-based) to reach the same processing endpoints.

### Diagram

![Insert your component Diagram here](images/component.png)

## Bristol Open Data API
TODO: Document each query to Bristol Open Data

![UML Class diagrams representing JSON query results](images/class1.png)
TODO: Repeat as necessary

### Class Diagrams

### Structure explaination
All datasets follow a similar structure:

   1) "features[] → array of records"
   2) "attributes{} → contains data values"
   3) "geometry{} → spatial data (for map datasets)"

# User guide
TODO: Explain how each use-case works by providing step-by-step screenshots for each use-case. This should be based on a tested scenario.

## UC1 – Select Role
Steps:

   1) Open application
   2) Select “Mover”
   3) Redirect to map

Expected Result:

   --> URL contains role=Mover

## UC2 – Map Selection
etc
etc
