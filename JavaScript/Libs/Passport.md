`npm install passport passport-local passport-local-mongoose express-session`

```javascript
// Requires
const passport = require("passport");
const passportLocalMongoose = require("passport-local-mongoose");
const session = require("express-session");

// Use by express
app.use(session({
	secret: "jfoidsjfoasjfoasjfosadjiog",
	resave: false,
	saveUninitialized: fals
}));
app.use(passport.initialize());
app.use(passport.session());

// Betwen defining schema and model....
userSchema.plugin(passportLocalMongoose);

// After defining model...
passport.use(User.createStrategy());
passport.serializeUser(User.serializeUser());
passport.deserializeUser(User.deserializeUser());

// User Creation
User.register(
	{ username: username },
	password,
	function(err, user) {
		// err set if error, otherwise:
		passport.authenticate('local')(req, res, function() {
			res.redirect("/loggedInPageRoute");
		});
	}
);

// Login Attempt
const user = new User({
	username: req.body.username,
	password: req.body.password
});
req.login(user, (err) => {
	// check for err, otherwise:
	passport.authenticate("local")(req, res, function() {
		res.redirect("/secrets");
	});
});

// On logout
req.logout(() => { res.redirect('/login'); }

// On restricted page:
if (req.isAuthenticated()) {
	// render page
} else {
	// redirect to login page
}


```