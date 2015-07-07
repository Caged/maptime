### Welcome
A brief intro.  Who I am.  What I do.  Why you should make maps.

### What we're going to create
Describe what we're creating and what we'll learn.  We're creating a fire map of Oregon which the data was taken from oregon.gov.

### Intro to MapBox Studio
Not comprehensive.  Talk about the editor.  The CartoCSS markup.
Start by changing a few properties.

### Incendio!
Ask people to import [fire](https://data.oregon.gov/Natural-Resources/2005-2014-Fire-Data/9nkj-mp3y) data source that lives on MapBox.

### Playing With Fire
* Create new project using Mapbox Light
* Add caged.aa3fadad to source
* Create new stylesheet "fire"
* Make the points appear as a marker

```css
#fires {
   marker-width: 3;
 }
```

![](./images/step-1.png)

Point out markers in the ocean and oddly even-spaced points inside Oregon as a good example to be mindful of the conclusions we make about data.

* Change to orangered color, remove outline.

```css
#fires {
  marker-width: 3;
  marker-fill: orangered;
  marker-line-width: 0;
 }
 ```

 ![](./images/step-2.png)

* Note how not all markers aren't drawn.  Enabled `marker-allow-overlap`.

Talk about the disperety between Medford and Portland.  There are about 77k people in Medford vs. about 620k people in Portland.  

Q. What could that tell us about the fires?
A. More people != more fires.  

Q. What do we *think* might be causing the fires in Medford?
A. ...Later

```css
#fires {
  marker-width: 3;
  marker-fill: orangered;
  marker-line-width: 0;
  marker-allow-overlap: true;
  marker-opacity: 0.2;
 }
 ```

  ![](./images/step-3.png)

* Style recent (>=2014) fires a different color.

Discuss the need for some kind of spreadsheet application or a database.  Something that helps you ask questions of the data to find out what message you're trying to convey.

```css
#fires {
  marker-width: 3;
  marker-fill: orangered;
  marker-line-width: 0;
  marker-allow-overlap: true;
  marker-opacity: 0.2;

  [year >= 2014] {
    marker-width: 6;
  }
 }
 ```

![](./images/step-4.png)


* Use description to style "motorist" a different direction.

```css
#fires {
  marker-width: 3;
  marker-fill: orangered;
  marker-line-width: 0;
  marker-allow-overlap: true;
  marker-opacity: 0.2;

  [year >= 2014] {
    marker-width: 6;
  }

  [cause='motorist'] {
   marker-fill: purple;
   marker-opacity: 0.5;
  }
 }
 ```

![](./images/step-5.png)

* Change cause to lightning.  Talk about how it aligns with Medford.

```css
#fires {
  marker-width: 2;
  marker-fill: orangered;
  marker-line-width: 0;
  marker-allow-overlap: true;
  marker-opacity: 0.5;
  marker-comp-op: hard-light;

  [year >= 2014] {
    marker-width: 4;
  }

  [cause='lightning'] {
   marker-fill: purple;
   marker-opacity: 0.5;
  }
 }
```

![](./images/step-6.png)


* Move on to using an emoji or vector symbol for fire

Add flame.svg to the inside of your mapbox studio project file.

```css
#fires {
  marker-file: url(flame.svg);
  marker-width: 4;
  marker-fill: orangered;
  marker-line-width: 0;
  marker-allow-overlap: true;
  marker-opacity: 0.5;
  marker-comp-op: hard-light;

  [year >= 2014] {
    marker-width: 6;
  }

  [cause='lightning'] {
   marker-fill: purple;
   marker-opacity: 0.5;
  }
 }
 ```

 ![](./images/step-7.png)
 

### What next? Things you can do at home
* If we get done too fast, move on to talk about adjusting zoom levels.

* Followup questions:  

Q. Why do you think there are no fires in South eastern Oregon? It's not an ocean, so what gives?  
A. Dataset doesn't include federal lands or "How to be mislead with data."

* Finally, we can change styles to dark background and just play around with
  different colors to get a look we're after.
* Find data. Have fun. Be responsible.


### Notes
* Metadata isn't basically nonexistent.  Probably around here somewhere http://www.oregon.gov/ODF/Pages/index.aspx
* NFCA - No Fire Crew Action
* About 12% of fires have no description and location.  
