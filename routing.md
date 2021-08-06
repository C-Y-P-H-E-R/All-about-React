# `React routing`
React routing is one of the biggest advantages, which react gives over many other frontend frameworks.

this can be understood in the following manner.
if we click a link, a request is made to the server to send the browser details 
for the page - link is supposed to lead us.
this process has two major disadvantages for any server.
  
  1) server now has to deal with requests from both frontend and backend.
  2) The code becomes comparatively more asynchronous and website performance is affected.

react router is a solution to reduce the frontend load from the server.
using this react handles all the requests local to your webapp/website.

`Installation`

Its installation is a piece of cake.
Just use the following command
      npm i react-router-dom

`syntax`
- ### import statements.
  1) there are four things to be imported in general.
      a) BrowserRouter (This is the main Router container)
      b) Route (This element is used to set the route to certain component on our webapp)
      c) Link (This element makes local redirection possible on the website)
      d) Switch (This is provides multiple component as choices while routing)
       
      Write the following commands to do it.
            import {BrowserRouter as Router, Route , Link, Switch} from 'react-router-dom'

- ###  Major syntax:

      <Router>
          <div className="sub__navbar">
              <Link className = "subnav__styling" to="/following"><h4>Following</h4></Link>
              <Link className = "subnav__styling" to="/recommended"><h4>Recommended</h4></Link>
          </div>
          <Switch>
              <Route exact path="/">
                  <Home />
              </Route>
              <Route exact path="/recommended">
                  <RecentArt />
              </Route>
          </Switch>
      </Router>

- ### use of exact and path keyword:
    - path keyword is used to specify the url to be redirected to, once the user clicks the Link.
    - Exact keyword is used to manage the behaviour of the Route element. if we do not add exact in the
      router element, it may take us to any subset of the path we defined in the path attribute.
      
      For instance:
                <Route path="/">
                    <Home />
                </Route>
                <Route path="/recommended">
                     <RecentArt />
                </Route>
           
      here, we did not add exact keyword. so if we click on the Link to take us to '/recommended',
      it will take us back to Home. 
      As it comes before in Switch and its path is a subset of '/recommended' path.
   
   
`Learn React routing in 15 minutes`

visit https://www.youtube.com/watch?v=aZGzwEjZrXc

------------------------------- END -------------------------------
     
        
        
