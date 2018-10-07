# MERNPACK-DEMO
it's a project Framework Demo which combiend different technolgies for React App Development. 

The client side is based on Create React App Framework.
The server side was build with Express.
Semantic-ui is used for the UI design.
Usermangement with user authentication is build by OKTA.
Database is chosen as MongoDB.

How to use this Framework Demo for building a react project:

# 1.Install Environment 

You can use the following command to install this Demo:

* `cd client && npm install move in client folder to build client evironment.
* `cd ../server && npm install move in server folder to build server encironment.

# 2.Use Okta

Register okta account and get domain url and client_id from okta home page. Then copy them to paste in the client side app.js. 

<Router>

                {/*OKta configure copy domian address to instead of https://dev-783322.oktapreview.com/
                 and client_id 0oafzpuy0pvICjIhI0h7 by yourself from OKTA WebPage
                 */}
                <Security
                    issuer="https://dev-783322.oktapreview.com/oauth2/default"
                    client_id="0oafzpuy0pvICjIhI0h7"
                    redirect_uri={window.location.origin + '/implicit/callback'}
                    onAuthRequired={onAuthRequired}
                >
                    <div className="App">
                        <Layout>
                            <Switch>
                                <Route path="/" exact={true} component={Home}/>
                                <Route path='/implicit/callback' component={ImplicitCallback}/>
                                {/*use okta loginPage to secure component*/}
                                <SecureRoute path="/myprofile" component={Myprofile}/>
                                <SecureRoute path="/group" component={Group}/>
                                {/*OKTA customer loginPage*/}
                                {/*<Route*/}
                                    {/*path="/login"*/}
                                    {/*render={() => (*/}
                                        {/*<LoginPage baseUrl="https://dev-783322.oktapreview.com" />*/}
                                    {/*)}*/}
                                {/*/>*/}
                            </Switch>
                        </Layout>
                    </div>
                </Security>
            </Router>
        );
    }
}

The project is provided  as two ways of using okta login pages. One is default pages provided by OKTA, another one is a customerized  loginpage created by SigninWidget. You can use OKTA as a usermanagement tool.


# 3. Mongodb

You can change the url with your own mangodb url in server site app.js

//u can change the url by your self
mongoose.connect('mongodb://localhost:27017/login-dem');
mongoose.Promise = global.Promise;

# When your running the Demo, make sure the MongoDB is connected properly. 

# 4.Run this Demo
* Connetced to MongoDB
* `cd server && npm start move in server folder to start server.
* `cd ../client && npm start move in client folder to start client. Runs the app in the development mode.

Open http://localhost:3000 to view it in the browser.
