# Elite Lab 3: Views

## Intro
In order to flex your newly learned responsive design skills, we will be creating a basic personal portfolio web site.

There are two pages:
* The Home page
* The Lab Exercise page

The Lab Exercise page will be a sandbox for us to throw some HTML and CSS around.

The Home page will eventually be copied into your final project. Feel free to continue customizing this page after the lab is over.

### Quick References
Read up on Flask Templates: https://flask.palletsprojects.com/en/1.1.x/tutorial/templates/
HTML Intro and mega reference: https://www.w3schools.com/html/html_intro.asp
CSS Intro and mega reference: https://www.w3schools.com/css/css_intro.asp

## Set Up
* Open up your terminal (Terminal for Mac, Ubuntu for PC)

* Navigate to your projects folder. For example, if you keep all your projects in a folder called "workspace", then
```
cd workspace
```

  * If you do not have a folder yet, then run these two commands
  ```
  mkdir workspace
  cd workspace
  ```

* Fork and clone this github repository
  * Step 1, go to the upper right hand of this web page and click "Fork"
  * Step 2, after you have navigated to your new page (make sure it has your username on it) go to the Green button that says "Code" at the top right of this page. Click Code, and then copy the link there.
  * Step 3, go to your terminal (where you have navigated to your projects folder) and type this in
  ```
  git clone <url of your forked repository>
  ```

* Open VSCode at your project folder. It should look like:
```
code elite-lab-views/
```

* Go to your VSCode menu (should be top of screen for Mac, or top of the window for Windows), and click on the `Terminal` item. Inside that menu, click `New Terminal`

* A new terminal screen should appear in your VSCode window. Use this terminal screen from now on.

* Activate your virtual environment
```
python3 -m venv venv
source venv/bin/activate
```

* Install the dependencies to your virtual environment
```
pip3 install -r requirements.txt
```

* Spin up the local web server with:
```
python3 -m flask run
```

## Lab Steps

Lab today will have 2 sections:

* Section 1: We will be editing exercise.html and exercise.css to put some concepts in practice.
* Section 2: You will have time to fill in your portfolio site with details from your resume. This will eventually be used for your final project, so feel free to keep working on it afterwards.


### Section 1
Before we do anything, let's take a look at our website to see what we are editing! Start your server with `python3 -m flask run`. You should see something that looks like this:
```
➜ python3 -m flask run    
 * Environment: development
 * Debug mode: on
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 250-700-815
```

Go visit the link your terminal gave you: `http://127.0.0.1:5000/`

Click on `Lab Exercise` at the top nav menu. You should now be at `http://127.0.0.1:5000/exercise`


#### Task 1
Notice that our text in the middle says `Move me to the left!`

* Edit the `exercise.css` file to move the text that says `Move me to the left!` to the left.
  * Quick hint, if you make changes to css files, you may need to hard refresh.
    * For Mac Users, you can do this with `Cmd + Shift + R`
    * For Windows Users, you can do this with `Ctrl + F5`

Take some time to figure this out yourself. If stumped, take a look at the instructions below:

#### Answer 1
* Find what div class the text `Move me to the left!` is. Take a look into `exercise.html`.
* Notice that it looks like this:
```html
<div class="text-overlay">
  <h1>Move me to the left!</h1>
</div>
```
* The class here is `text-overlay`. In order for us to change the style of that class, we need to find the appropriate selector in `exercise.css`.
* Go to `exercise.css` and find the rules that apply to class `text-overlay` (hint, classes have a `.` in front. So we are looking for `.text-overlay`)
* Notice that class has a property called `text-align: center;`
* We want to change the value of this property to be `left`.
* Make this change and go verify that it worked! (Remember, you may need to hard refresh)

What we did here was make the association between HTML and CSS code. By looking at our HTML tags and finding what properties it has (class,, id, or element name), we can then see which rules apply to it in our CSS code. By matching the CSS selector to the HTML element, we can change those rules and make the HTML appearance change!

#### Task 2
* Now move over into `exercise.html`
* Find the html comment that says `<!-- Add your own content below -->`
* Add a row with your contact info in 3 columns
  * Name
  * Contact Email
  * Where you are based from

* Add 3 rows with 3 projects you worked on
  * 1 column should be a title
  * 1 column should be a description

* The contact info row should break at the small breakpoint
* The project rows should break at the medium breakpoint

Please take some time to figure this out on your own. I have provided a sample html section right above the part you need to edit. You can copy this code to get the basic layout.

#### Answer 2
Let's first handle the contact info.
* First create a new row
```html
<div class="row">
</div>
```
* This will create a new row in our html code (but with no content yet)
* Remember, we want 3 columns here, so let's create 3 empty columns
```html
<div class="row">
  <div class="col">
  </div>
  <div class="col">
  </div>
  <div class="col">
  </div>
</div>
```
* This will create 3 empty columns throughout our row (but remember, theres no content yet.)
* Now fill in your contact information into each row. It should look like (but obviously not match)
```html
<div class="row">
  <div class="col">
    Kevin K
  </div>
  <div class="col">
    myemail@gmail.com
  </div>
  <div class="col">
    Greater Los Angeles area
  </div>
</div>
```

Take a look at your page now (you may need to refresh). You should see the content appear evenly spaced throughout your row. Remember, that bootstrap will automatically space these columns evenly if you don't give it any values!

Now let's focus on making it responsive. Remember, we have 3 columns, that need to break at the medium breakpoint (meaning that it should stack on top of each other BELOW the medium breakpoint).

* 12 divided by 3 is 4. So each column should take 4 units
* Remember that we use `md` as the abbreviation for the medium breakpoint
* Therefore, the class name should be `col-md-4`
* Change the classname of each column to be `col-md-4` instead of `col`

Next let's add the project rows.

* Create a new row below your contact info row
```html
<div class="row">
  ... (this is your contact info row)
</div>

<div class="row">
</div>
```
* This time we need two cols. Also remember that we want this one to break at the small breakpoint. 
* 12 divided by 2 is 6
* We use `sm` as an abbreviation for the small breakpoint
* Therefore the class name should be `col-sm-6`.

* Now create two columns with the class `col-sm-6`. Fill in your project info as well. It should look like:
```html
<div class="row">
  <div class="col-sm-6">
    Web App Project
  </div>
  <div class="col-sm-6">
    I made a cool website with a chatroom in this class
  </div>
</div>
```

* Add two more rows like this, and you are done!

Notice how easy it is to add new rows and content. Your HTML tags are used to structure the layout of your page, while your text can fill in the spaces that you have laid out. Try and get the hang of how the bootstrap class names work. Once you do, then writing responsive websites will come easy.

### Section 2

In this section, you will edit the contents of `index.html` to fill in your personal accomplishments, information, etc.

Use the information from the resume assignment to help fill in the home page.

Basic steps you should complete:
* Fill in the Experience/Projects/Accomplishments content
* Replace the image cards with your own images and provide some sort of title or caption
* Replace the blurb, banner, and footer with your details.

You guys are completely free to remove, move around, edit, change, and add content. I've attempted to make as blank of a personal resume website for you as possible. In the end, it's up to you on how much you want to make it yours.

Reach out if you are stuck, don't know how to do something, or have any questions in general.

Your content here will eventually end up on your final project (which will be deployed to the web). Feel free to keep tweaking and adding to this throughout the rest of our course! I'm always happy to help outside of class hours.
