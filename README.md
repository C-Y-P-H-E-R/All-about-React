# `All-about-React`
This is my react guide.
note: this is only for revision purpose only.

### 1) download:  
     npx create-react-app project_name --use-npm
     note: { if you use yarn, and want to download the app using npm, then add --use-npm at the end. }

### 2) file-structure: 
     a) public: contains the index.html file on which the components will be finally rendered. 
        also, is used to keep images and adding external css.
     b) src: this is the root folder of our project and contains all the components and custom css for the project.
     c) package.json: this is the blueprint of all the dependencies and scripts in the project.
     d) .gitignore: this is the file used to add files which are supposed to be skipped by git before pushing on github.
     e) node_modules: this directory contains all the modules necessary for running react and node.
     
### 3) using createElement():
  
    `without JSX`:  
        
        - the createElement() function comes from the class React. it is used to create a new element to be rendered on the web-page.
        - it may be h1,h2,p,a or an element of any sort.

        SYNTAX: 
            React.createElement("h1",{style: {color: "red"}},"Hello world")
                  - 1st parameter defines the type of element.
                  - 2nd parameter defines properties being passed in the element.
                  - 3rd parameter defines the innerHTML being passed.

        - Using createElement() to render multiple nested elements.

        SYNTAX:
             a)   React.createElement("div",null, React.createElement("h1",null,"Hello world!"));
                  - Third parameter will now contain another react element instead of some innerHTML.
             b)   React.createElement("ul",null,
                    React.createElement("li",null,"Hello"),
                    React.createElement("li",null,"World")
                  )
    
    `with JSX`:
        
        - Babel: it does all the hardwork of converting the entered JSX to the language understood by the browser.
          Inshort, JSX is possible only because of babel.
        
        SYNTAX:
            React.createElement(
              <ul>
                <li> Hello </li>
                <li> World </li>
              </ul>
            )

### 4) Basic JSX:
    
    a) JSX can be called a fusion of HTML and Javascript, and can be simply called React Javascript.
    
    SYNTAX: 
      let myvar = {
        name: "CYPHER",
        status: "Active"
      }
      
      using the JS object in JSX,
      <h1>{myvar.name} is {myvar.status}</h1>

### 5) React Components:
    - React Components are functions used to return fragments of UI.
    - A react component contains two parts compulsorily :
        -- Function body (must return something)
        -- Export statement
        
            a) `Creating React component`
                  SYNTAX:
                      function Hello() {
                        return <h1>hello world</h1>
                      }
                      
                      <Hello />
                note: always keep the first letter of a React component 'Capital'.

### 6) React props:
    - props are basically a set of key-value pairs that can be passed from parent-to-child component.
    important points to remember:
        - props keyword is for an object.
        - Object.keys(props) holds special meaning, returns an array of all keys present in the props obj.
        - destructuring of an object is useful to use direct keynames to access prop values.

    `Rendering lists and lists of objects`:
        SYNTAX: 
            const list = [
                { id: 1, name: "abc"},
                { id: 2, name: "def"},
                { id: 3, name: "ghi"}
            ]
            
           return(
                <div>
                    {
                       props.list.map(item => {
                          return <h1 key={item.id}>{item.name}</h1>
                       }) 
                    }
                </div>
           )
     
     `Conditional Rendering`:
          SYNTAX:
              function Comp(props) {
                  (props.name === "kush") ? console.log(`hello ${props.name}`) : console.log(`hello Stranger`)
              }
              
              <Comp name="kushagra" />
          
          - note: using ternary is optional, one can always use if-else ladder for reasoning.
      
     `React Fragments`:
          - these are used to wrap items before returning them to the parent component.
          - their benefit is that, the react fragments are ignored by the web browser.
      
          SYNTAX:
              ways of implementing react fragments
                  -- <> & </>
                  -- <React.Fragment> & </React.Fragment>
     
     `Array Destructuring`:
          - array destructuring is very important while handling states.
              SYNTAX:
                  const [first,second,third] = ["Hi","Kushagra","sharma"]
                  console.log(first);   // output --> Hi
                  console.log(second);  // output --> Kushagra
                  
                  const [, ,third] = ["Hi","Kushagra","sharma"]
                  console.log(third);   // output --> sharma

### 7) React States:
    - State is nothing but a special name given to an array of two elements.
    - element one is nothing but some data.
    - element two is always a method used to modify that data.
    
    SYNTAX:
        const [data, setData] = useState("this is data"); 
            - in above declaration, array destructuring is used to create the state.
        <button onClick={() => setData("The state is now changed")} />
            - in the above declaration, the state is changed using onClick event handler.
            - the state-method must always be passed as a callback.
            
### 8) useEffect hook: 
    - the website is not just a collection of beautiful UI.
    - we can add external processes or effects to the Website too.
    - all that can be managed by useEffect hook
    
    SYNTAX:
        useEffect(() => {
            console.log(val1);
        });
        useEffect(() => {
            console.log(val2);
        })
         
        const [val1, setVal1] = useState("");
        const [val2, setVal2] = useState("");
        
        note: here since useEffect is not defined with a dependency array, 
              even if you change the value of one variable, react re-renders 
              other variable too, each time. if one useEffect is fired, the other
              one fires itself.
              thats why creating a dependency array and adding values to it is imp.
        
        useEffect(() => {
            console.log(val1);
        },[val1]);
        useEffect(() => {
            console.log(val2);
        },[val2])
        
                now if you update one variable, only one useEffect will be fired.
                that would be the one associated to that variable.

### 9) Fetching data using useEffect:
    - we can fetch data from a url using fetch api in useEffect
    
    const [data,setData] = useState(null)
    useEffect(() => {
      fetch("https://api.github.com/users/C-Y-P-H-E-R")
      .then(res => res.json())
      .then(setData(res))
      .catch(console.error)
    })
    // note the above code fetches json-object data from github-users-api and stores it to data-state.

### 10) useReducer hook:
    - this hook is used in place of useState, when we want to add some toggle functionality to our code.
    - like in toggling light/dark mode for website.
    
    SYNTAX:
    
    const [checked,toggle] = useReducer(
      checked => !checked,
      false
    );

 
 #### `so guys this was all about the react basics that one needs to have to start building react applications.`
