# Testing

## Test Plan

| Requirements ID | Test Case ID | Unit Tested                 | Integration Testing        | Input / Precondition         | Expected Outputs                         |
|-----------------|--------------|-----------------------------|----------------------------|------------------------------|------------------------------------------|
| FR1             | TC1.U1       | setUserRole()               |                            | User selects “Mover”         | Role stored as Mover                     |
| FR1             | TC1.U2       | setUserRole()               |                            | User selects “Business”      | Role stored as Business                  |
| FR1             | TC1.U3       | setUserRole()               |                            | User selects “Guest”         | Role stored as Guest                     |
| FR1             | TC1.I1       |                             | Role + Navigation          | Role selected → navigate     | Role persists in Page 2 URL              |
| FR1             | TC1.I2       |                             | Role + Session Handling    | Multiple role selections     | Only one role stored                     |
| FR2             | TC2.U1       | getWardFromMap()            |                            | Click valid ward polygon     | Ward ID returned                         |
| FR2             | TC2.U2       | mapHoverEffect()            |                            | Hover ward area              | Ward highlight shown                     |
| FR2             | TC2.U3       | wardClickHandler()          |                            | Click outside ward           | No ward selected                         |
| FR2             | TC2.I1       |                             | Map + Ward Rendering       | API ward data loaded         | All wards rendered                       |
| FR2             | TC2.I2       |                             | Ward + Navigation          | Click ward                   | Redirect with ward in URL                |
| FR2             | TC2.I3       |                             | Map + API Integration      | Valid JSON response          | Map renders correctly                    |
| FR3             | TC3.U1       | parseSearchQuery()          |                            | Input “central”              | Query split correctly                    |
| FR3             | TC3.U2       | validateSearchInput()       |                            | Empty input                  | All wards returned in alphadetical order |
| FR3             | TC3.U3       | normalizeSearchCase()       |                            | “CENTRAL” input              | Same results as lowercase                |
| FR3             | TC3.I1       |                             | Search + Result Generation | Valid query entered          | Matching wards displayed                 |
| FR3             | TC3.I2       |                             | Search + Ranking Trigger   | Search submitted             | Ranked results shown                     |
| FR3             | TC3.I3       |                             | Search + Navigation        | Click result                 | Redirect to ward page                    |
| FR4             | TC4.U1       | calculateNameScore()        |                            | Ward name match              | +5 score assigned                        |
| FR4             | TC4.U2       | calculateKeywordScore()     |                            | Keyword match found          | +3 score assigned                        |
| FR4             | TC4.U3       | handleNoMatchScore()        |                            | No match                     | Score = 0                                |
| FR4             | TC4.I1       |                             | Ranking + Sorting System   | Multiple wards scored        | Sorted descending order                  |
| FR4             | TC4.I2       |                             | Ranking + Display Output   | Valid query                  | Ranked list displayed                    |
| FR4             | TC4.I3       |                             | Ranking Stability          | Equal scores                 | Stable ordering maintained               |
| FR5             | TC5.U1       | selectTags()                |                            | Multiple checkboxes selected | Tag array created                        |
| FR5             | TC5.U2       | validateTagInput()          |                            | No selection                 | Empty tag array                          |
| FR5             | TC5.U3       | encodeTagsToURL()           |                            | Tags selected                | Proper URL encoding                      |
| FR5             | TC5.I1       |                             | Tag + URL Transmission     | Submit form                  | info values passed                       |
| FR5             | TC5.I2       |                             | Multi-tag Handling         | 5+ tags selected             | All tags transmitted                     |
| FR5             | TC5.I3       |                             | Tag Navigation Flow        | Submit selection             | Tags passed to next page                 |
| FR6             | TC6.U1       | mapTagToAPI()               |                            | Tag ID valid                 | Correct API endpoint returned            |
| FR6             | TC6.U2       | handleInvalidTag()          |                            | Invalid tag ID               | No dataset returned                      |
| FR6             | TC6.U3       | mapMultipleTags()           |                            | Multiple tags selected       | Multiple endpoints returned              |
| FR6             | TC6.I1       |                             | Tag + Dataset Linking      | Valid tags selected          | Correct datasets fetched                 |
| FR6             | TC6.I2       |                             | Multi-tag Mapping          | Multiple tags                | Multiple datasets loaded                 |
| FR6             | TC6.I3       |                             | Mapping Stability          | Rapid tag changes            | Correct endpoint resolved                |
| FR7             | TC7.U1       | fetchAPIData()              |                            | Valid endpoint               | Data retrieved                           |
| FR7             | TC7.U2       | handleAPIError()            |                            | Broken endpoint              | Error handled safely                     |
| FR7             | TC7.U3       | buildAPIRequest()           |                            | Ward + tag provided          | Correct request formed                   |
| FR7             | TC7.I1       |                             | API + Fetch Pipeline       | Valid response               | Data loaded successfully                 |
| FR7             | TC7.I2       |                             | Multi-API Requests         | Multiple tags                | Multiple fetch calls succeed             |
| FR7             | TC7.I3       |                             | Network Failure Handling   | No internet                  | Graceful fallback                        |
| FR8             | TC8.U1       | parseJSONData()             |                            | Raw API response             | Structured JSON output                   |
| FR8             | TC8.U2       | extractNumericFields()      |                            | Mixed dataset fields         | Only numeric values kept                 |
| FR8             | TC8.U3       | filterInvalidData()         |                            | Null/undefined values        | Clean dataset returned                   |
| FR8             | TC8.I1       |                             | API + Processing Pipeline  | Valid dataset                | Clean structured output                  |
| FR8             | TC8.I2       |                             | Multi-dataset Processing   | Multiple APIs                | All datasets processed                   |
| FR8             | TC8.I3       |                             | Large Data Handling        | Large dataset                | Processed without crash                  |
| FR9             | TC9.U1       | filterWardData()            |                            | ward = Ashley                | Only Ashley data shown                   |
| FR9             | TC9.U2       | filterTagData()             |                            | Tags selected                | Relevant filtered output                 |
| FR9             | TC9.U3       | handleEmptyWardData()       |                            | No ward match                | “No data available”                      |
| FR9             | TC9.I1       |                             | Full Display Pipeline      | ward + tags selected         | Charts rendered correctly                |
| FR9             | TC9.I2       |                             | Multi-chart Rendering      | multiple tags                | Multiple graphs displayed                |
| FR9             | TC9.I3       |                             | End-to-End Flow            | Full system input            | Correct final output shown               |
| FR16–18         | TC16.U2      | checkStorage()              |                            | Refresh                      | No stored data                           |
| FR16–18         | TC16.I1      |                             | System usage               | Use system                   | No persistence                           |
| FR16–18         | TC16.I2      |                             | API reload                 | Reload                       | Fresh data                               |
| NFR1            | TC19.U1      | measureLoadTime()           |                            | Load data                    | <3 seconds                               |
| NFR1            | TC19.U2      | measureLoadTime()           |                            | Large dataset                | Acceptable speed                         |
| NFR1            | TC19.I1      |                             | Full pipeline              | End-to-end                   | Timely load                              |
| NFR1            | TC19.I2      |                             | Multi-tag                  | Multiple tags                | Performance maintained                   |
| NFR2            | TC20.U1      | checkBrowserCompatibility() |                            | Chrome                       | Works                                    |
| NFR2            | TC20.U2      | checkBrowserCompatibility() |                            | Edge                         | Works                                    |
| NFR2            | TC20.I1      |                             | Chrome flow                | Full flow                    | No issues                                |
| NFR2            | TC20.I2      |                             | Edge flow                  | Full flow                    | No issues                                |
| NFR3            | TC21.U1      | handleAPIError()            |                            | API failure                  | Error message                            |
| NFR3            | TC21.U2      | handleAPIError()            |                            | Timeout                      | Graceful handling                        |
| NFR3            | TC21.I1      |                             | Error + UI                 | Fail → display               | Message shown                            |
| NFR3            | TC21.I2      |                             | Retry                      | Retry                        | Recovery works                           |
| NFR4            | TC22.U1      | measureSteps()              |                            | Complete task                | ≤5 steps                                 |
| NFR4            | TC22.U2      | measureSteps()              |                            | Complex flow                 | Efficient                                |
| NFR4            | TC22.I1      |                             | Full journey               | End-to-end                   | Within limit                             |
| NFR4            | TC22.I2      |                             | Alternative                | Alt flow                     | Within limit                             |
| NFR5            | TC23.U1      | checkResponsiveLayout()     |                            | Mobile view                  | Layout correct                           |
| NFR5            | TC23.U2      | checkResponsiveLayout()     |                            | Resize                       | Responsive                               |
| NFR5            | TC23.I1      |                             | Mobile flow                | Mobile                       | Works                                    |
| NFR5            | TC23.I2      |                             | Tablet flow                | Tablet                       | Works                                    |
| NFR6–7          | TC24.U1      | checkUIClarity()            |                            | Load UI                      | Clear visuals                            |
| NFR6–7          | TC24.U2      | checkPerformanceLowEnd()    |                            | Low-end device               | Acceptable performance                   |
| NFR6–7          | TC24.I1      |                             | Full system                | System                       | Usable UI                                |
| NFR6–7          | TC24.I2      |                             | Stress test                | Heavy load                   | Stable                                   |
| N/A             | TC-E2E1      |                             | Full user flow             | Role → Ward → Tags → View    | Correct graphs                           |
| N/A             | TC-E2E2      |                             | Search flow                | Search → Rank → Select       | Correct output                           |
| N/A             | TC-E2E3      |                             | Tag flow                   | Role → Tags → Ranking        | Graphs shown                             |
| N/A             | TC-E2E4      |                             | Error flow                 | Invalid search               | Fallback works                           |
| N/A             | TC-E2E5      |                             | Multi data                 | Multiple tags                | Datasets shown                           |
| N/A             | TC-E2E6      |                             | Failure handling           | API failure                  | Handled properly                         |

## Test Runs

| Use-Case ID | Requirement ID | Test Case ID | Status |
|-------------|----------------|--------------|--------|
| UC1         | FR1            | TC1.U1       | Pass   |
| UC1         | FR1            | TC1.U2       | Pass   |
| UC1         | FR1            | TC1.U3       | Pass   |
| UC1         | FR1            | TC1.I1       | Pass   |
| UC1         | FR1            | TC1.I2       | Pass   |
| UC2         | FR2            | TC2.U1       | Pass   |
| UC2         | FR2            | TC2.U2       | Pass   |
| UC2         | FR2            | TC2.U3       | Pass   |
| UC2         | FR2            | TC2.I1       | Pass   |
| UC2         | FR2            | TC2.I2       | Pass   |
| UC2         | FR2            | TC2.I3       | Pass   |
| UC3         | FR3            | TC3.U1       | Pass   |
| UC3         | FR3            | TC3.U2       | Pass   |
| UC3         | FR3            | TC3.U3       | Pass   |
| UC3         | FR3            | TC3.I1       | Pass   |
| UC3         | FR3            | TC3.I2       | Pass   |
| UC3         | FR3            | TC3.I3       | Pass   |
| UC3         | FR4            | TC4.U1       | Pass   |
| UC3         | FR4            | TC4.U2       | Pass   |
| UC3         | FR4            | TC4.U3       | Pass   |
| UC3         | FR4            | TC4.I1       | Pass   |
| UC3         | FR4            | TC4.I2       | Pass   |
| UC3         | FR4            | TC4.I3       | Pass   |
| UC4         | FR5            | TC5.U1       | Pass   |
| UC4         | FR5            | TC5.U2       | Pass   |
| UC4         | FR5            | TC5.U3       | Pass   |
| UC4         | FR5            | TC5.I1       | Pass   |
| UC4         | FR5            | TC5.I2       | Pass   |
| UC4         | FR5            | TC5.I3       | Pass   |
| UC4         | FR6            | TC6.U1       | Pass   |
| UC4         | FR6            | TC6.U2       | Pass   |
| UC4         | FR6            | TC6.U3       | Pass   |
| UC4         | FR6            | TC6.I1       | Pass   |
| UC4         | FR6            | TC6.I2       | Pass   |
| UC4         | FR6            | TC6.I3       | Pass   |
| UC5, UC6    | FR7            | TC7.U1       | Pass   |
| UC5, UC6    | FR7            | TC7.U2       | Pass   |
| UC5, UC6    | FR7            | TC7.U3       | Pass   |
| UC5, UC6    | FR7            | TC7.I1       | Pass   |
| UC5, UC6    | FR7            | TC7.I2       | Pass   |
| UC5, UC6    | FR7            | TC7.I3       | Pass   |
| UC5, UC6    | FR8            | TC8.U1       | Pass   |
| UC5, UC6    | FR8            | TC8.U2       | Pass   |
| UC5, UC6    | FR8            | TC8.U3       | Pass   |
| UC5, UC6    | FR8            | TC8.I1       | Pass   |
| UC5, UC6    | FR8            | TC8.I2       | Pass   |
| UC5, UC6    | FR8            | TC8.I3       | Pass   |
| UC6         | FR9            | TC9.U1       | Pass   |
| UC6         | FR9            | TC9.U2       | Pass   |
| UC6         | FR9            | TC9.U3       | Pass   |
| UC6         | FR9            | TC9.I1       | Pass   |
| UC6         | FR9            | TC9.I2       | Pass   |
| UC6         | FR9            | TC9.I3       | Pass   |
| N/A         | FR16–18        | TC16.U2      | Pass   |
| N/A         | FR16–18        | TC16.I1      | Pass   |
| N/A         | FR16–18        | TC16.I2      | Pass   |
| UC5, UC6    | NFR1           | TC19.U1      | Pass   |
| UC5, UC6    | NFR1           | TC19.U2      | Pass   |
| UC5, UC6    | NFR1           | TC19.I1      | Pass   |
| UC5, UC6    | NFR1           | TC19.I2      | Pass   |
| UC1–UC6     | NFR2           | TC20.U1      | Pass   |
| UC1–UC6     | NFR2           | TC20.U2      | Pass   |
| UC1–UC6     | NFR2           | TC20.I1      | Pass   |
| UC1–UC6     | NFR2           | TC20.I2      | Pass   |
| UC5, UC6    | NFR3           | TC21.U1      | Pass   |
| UC5, UC6    | NFR3           | TC21.U2      | Pass   |
| UC5, UC6    | NFR3           | TC21.I1      | Pass   |
| UC5, UC6    | NFR3           | TC21.I2      | Pass   |
| UC1–UC6     | NFR4           | TC22.U1      | Pass   |
| UC1–UC6     | NFR4           | TC22.U2      | Pass   |
| UC1–UC6     | NFR4           | TC22.I1      | Pass   |
| UC1–UC6     | NFR4           | TC22.I2      | Pass   |
| UC1–UC6     | NFR5           | TC23.U1      | Pass   |
| UC1–UC6     | NFR5           | TC23.U2      | Pass   |
| UC1–UC6     | NFR5           | TC23.I1      | Pass   |
| UC1–UC6     | NFR5           | TC23.I2      | Pass   |
| UC5, UC6    | NFR6–7         | TC24.U1      | Pass   |
| UC5, UC6    | NFR6–7         | TC24.U2      | Pass   |
| UC5, UC6    | NFR6–7         | TC24.I1      | Pass   |
| UC5, UC6    | NFR6–7         | TC24.I2      | Pass   |
| N/A         | N/A            | TC-E2E1      | Pass   |
| N/A         | N/A            | TC-E2E2      | Pass   |
| N/A         | N/A            | TC-E2E3      | Pass   |
| N/A         | N/A            | TC-E2E4      | Pass   |
| N/A         | N/A            | TC-E2E5      | Pass   |
| N/A         | N/A            | TC-E2E6      | Pass   |
