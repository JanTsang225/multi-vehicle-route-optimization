# Overview

### Motivation:

This project was inspired by my church fellowship, where weekly meetings are attended by 30–60 people. Many attendees rely on others for rides, especially those living farther away. Since the attendees vary slightly each week, planning efficient driving routes manually can be time-consuming. I created this project to automatically generate optimized driving routes, minimizing total travel distance and making it easier for volunteer drivers.

### Objective:

Develop a Python-based solution to optimize delivery-style routes for multiple drivers, accounting for realistic constraints such as vehicle capacity, maximum stops, and designated final destinations. The goal was to minimize total travel distance while ensuring all attendees are transported efficiently.

### Approach & Customization:

- Implemented and adapted an existing OR-Tools routing algorithm to suit the specific needs of the weekly fellowship rides.

- Designed a scalable prioritization system to balance between:

      Standard shortest distance routes, and

      Prioritization of proximity to the final stop with a slight bias for convenience

- Applied data analysis and visualization to assess route efficiency and present results clearly.

### Methodology

1. Load the location of all canditates including attendees and absentees. Some of the candidates are also drivers.
2. Clean the data and filter out attendees who require transportation.
3. Use Nominatim from geopy.geocoders to convert postcodes into geographic coordinates (latitude and longitude).
4. Connect to OpenRouteService and use the coordinates to calculate the route distance between each location, ultimately creating    a distance matrix.
5. Adapt the basic code provided in the OR-Tools documentation by adding constraints that match the problem requirements:
   - a. All vehicles depart from the depot (meeting place).
   - b. Each vehicle has a different terminal, which corresponds to the driver’s home.
   - c. Vehicle capacities vary (typically 3 or 4 seats), so passengers are assigned accordingly.
   - d. Priority is given to attendees living farther from the depot, as they are expected to face greater travel inconvenience.
   - e. Attendees who live too far from both the depot and the driver’s home are excluded, in order to keep the driver’s journey          convenient.
6. Apply the scalable prioritization system, balancing:
   - Standard shortest distance routing, and
   - Prioritization of proximity to the final stop, with a bias toward driver and passenger convenience.

7. Print the resulting routes in text format.
8. Visualize the routes by plotting both the assigned and unassigned locations on an HTML map.
### Key Skills & Tools:

Python | SQL | OR-Tools | Pandas | Data Visualization | Optimization Algorithms | Algorithm Adaptation | Problem-Solving

### Outcome:

- Generated optimized routes for multiple drivers under weekly changing constraints.

- Successfully demonstrated how custom prioritization improves total travel distance and convenience for drivers.

- Produced a reproducible workflow for analyzing and visualizing optimized routes, making weekly planning much easier for the fellowship group.

### Example Output
<img width="547" height="362" alt="image" src="https://github.com/user-attachments/assets/317ed133-3cba-451c-a408-2cd2eac28916" />

<img width="512" height="633" alt="image" src="https://github.com/user-attachments/assets/3ec4acf4-7e6a-4a38-a7b0-fefc6be74eb7" />

