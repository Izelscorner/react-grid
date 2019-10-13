This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Why I used react.js

Firstly using create react app, react gives a quick bootstrap project to instantly start developing and prototyping projects. Major reason grid/pagination easly could be component which can be used across all projects. It is a good practive where we can create multiple components and use seperation of conncerns. Also in this example I used state lift up patterm to share data across different components.
Pagination, table, and search dumb components are sharing same state through props controlled by the Grid smart controller/Component where all the child componets come together. For the sake of displaying javascript usage skill, I have implemented all the grid from ground, otherwise react has many different grid component libraries for usage. 

## Why I used Bootstrap
I used traditional bootstrap package for the styling, there is also react based bootstrap library, where components are react components. I thought displaying little bit of css usage would be nicer.  for this example Bootstrap has all the styles needed paginationn, table and form controls therefore I didn't have to write any css. If you would like to see more css I would be happy to discuss during the interview as well I normally use sass :)

## Search Fuctioality known issue
Currently name search is working on keypress change bind to input onChange with state, so this is making a request for every string user enters, this can be api costly and not preferable, we can solve this issue either adding a cancel to ajax call which is optimal, but I used native fetch functionality and could't find an option for that axios or many ajax libraries has this option. I believe curretly this is not supported in fetch api , other option could be using search button to make one search request. Another option would be using a debounce function where it delays api fetch until user finishes typing. 

## Example usage of Grid Component 
  
Fetching Data example , this can be customized based on the usage.
```
// Grid is expecting a promise for parsing the data further
// Data should contain "results" as Array and "count" as an integer
// We can improve this as well to be more generic and independent from backend.
function fetchData(params) {
  const querystring = new URLSearchParams(params);
  return fetch(`https://swapi.co/api/people/?${querystring.toString()}`).then((res) => res.json());
}

```

Column structure example
```
// Colum is an array of object which states header name and column name to match with backend.
const columns = [{columnHeader: 'Name', columnField:'name'}, 
                 {columnHeader: 'Hair Color', columnField:'hair_color'},
                 {columnHeader: 'Birth Year', columnField:'birth_year'},
                 {columnHeader: 'Height', columnField:'height'},
                 {columnHeader: 'Eye Color', columnField:'eye_color'},
                 {columnHeader: 'Skin Color', columnField:'skin_color'},
                ]
```

Grid Example
```
      // Final component and usage
      <Grid dataHandler={fetchData}
            paginationParam={'page'}
            searchParam={'search'}
            columns={columns}
      />
```

#### Component Props/Options
  **dataHandler:** Function/event propery and makes a ajax request to the api based on query parameters.  
  **paginationParam:** It's the name of the api query parameter for pagination, it can be customized for different api end points.  
  **searchParam:** It's the name of the api search parameter, it can be customized for different api end points. if user do not provide this parameter search textbox won't be displayed.  
  **columns:** Column structure and headers for generic grid usage for diffrent scenerios.

## Available Scripts

In the project directory, you can run:

### `yarn`

Run yarn command to install dependencies.

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.
