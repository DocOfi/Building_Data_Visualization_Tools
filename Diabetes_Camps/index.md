---
title: "Resources for Families with Diabetic Children"
author: "Edmund Julian Ofilada"
date: "April 4, 2018"
output: 
  html_document:
        code_folding: hide
        toc: true
        toc_depth: 2
        toc_float: true
        keep_md: true
---



# Synopsis

Having diabetes as a child is a big challenge not only to the child but to the whole family as well. The challenges are far too numerous to enumerate and every road you take seem to have a pothole lurking to derail the  journey or  put it to an end. For this project I will be focussing on a resource for diabetic kids that has proved to be very helpful, the diabetes camp.

The diabetes camp is a way for a child with diabetes to come to terms with his diabetes on his own. For the first time in his life, mom and dad are not there to tell him what to do next, to keep him safe, and prevent him from indulging in activities that are gratifying but harmful. It is a time to believe that I am not the only one in this world who has this disease and that other people share my feelings towards this disease.

With the help of R and packages created by wonderful people who share their talents freely, I hope to bring to light where diabetes camps are found in the Philippines and what they have to offer. Hopefully, this document will eventually find its way to the top of a google search for someone looking to provide help for his or her diabetic child in the Philippines.

# How did i become an expert at diabetes camps?

I don't consider myself an expert but I have attended a few as Project Coordinator for Project Oral Health for Juvenile Diabetics (POHJD). POHJD was a project I started in 1996 to help type 1 diabetic kids avail of free dental treatment. The project was based at St. Luke's Medical Center in Quezon City.


```r
library(dplyr)
library(leaflet)
library(mapview)
library(ggmap)

pohjd1Icon <- makeIcon(
  iconUrl = "https://docofi.github.io/extras/www/POHJD.png",
  iconWidth = 39, iconHeight = 95,
  iconAnchorX = 22, iconAnchorY = 94
  )

slmc <- geocode("St.Luke Medical Center, Quezon City, Philippines")
pohjdLatLong <- data.frame(
  lat = 14.62243,
  lng = 121.0235)
slmc <- geocode("St.Luke Medical Center, Quezon City, Philippines")

pohjdLatLong %>% 
  leaflet(options = leafletOptions(maxZoom = 18)) %>%
  addProviderTiles("OpenStreetMap.Mapnik") %>%
  addMarkers(icon = pohjd1Icon)
```

<!--html_preserve--><div id="htmlwidget-9c659fc69642c8060419" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-9c659fc69642c8060419">{"x":{"options":{"maxZoom":18,"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addProviderTiles","args":["OpenStreetMap.Mapnik",null,null,{"errorTileUrl":"","noWrap":false,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false}]},{"method":"addMarkers","args":[14.62243,121.0235,{"iconUrl":{"data":"https://docofi.github.io/extras/www/POHJD.png","index":0},"iconWidth":39,"iconHeight":95,"iconAnchorX":22,"iconAnchorY":94},null,null,{"clickable":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},null,null,null,null,null,null,null]}],"limits":{"lat":[14.62243,14.62243],"lng":[121.0235,121.0235]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->


<br>

I was granted the privilege to attend diabetes camps to share my knowledge about oral health problems that are common to children with diabetes. Yes, I was a dentist before I learned R. I used to extract teeth, now I extract bytes.

Diabetes Camps are usually held during the Holy Week. The Philippines is predominantly a Christian country and Holy Week is observed by having public and private schools and offices closed from Holy Wednesday till Good Friday. Diabetes camps take advantage of this break to hold their camp as the children don't have school, and doctors and nurses find it easy to take leave from their respective clinics and hospitals.

# Rainbow camp

Rainbow camp is a camp that is usually held in Hermosa, Bataan. The camp offers a chance to experience outdoor activities like a trek to a nearby hill that passes through a brook and a camp out under the stars for one night. 

Click on the minus sign to see familiar roads to orient yourself to the location of the camp in relation to other landmarks like the SCITEX. Click on the dot in the middle to see a video I took while attending Rainbow Camp.


```r
library(ggmap)
library(mapview)
library(sf)
bataan <- geocode("Hermosa, Bataan, Philippines")
###Source : https://maps.googleapis.com/maps/api/geocode/json?address=Hermosa%2C%20Bataan%2C%20Philippines
###      lon      lat
###1 120.4242 14.82691
pnt <- data.frame(x = 120.4242, y = 14.82691)
pnt <- st_as_sf(pnt, coords = c("x", "y"), crs = 4326)

mapview(pnt, popup = mapview:::popupIframe("https://www.youtube.com/embed/yc6OMXUSlLA", width = 300, height = 225), map.types = "OpenStreetMap.DE", zoom = 6)
```

<!--html_preserve--><div id="htmlwidget-f07079c0d5104907ba1b" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-f07079c0d5104907ba1b">{"x":{"options":{"minZoom":1,"maxZoom":100,"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}},"bounceAtZoomLimits":false,"maxBounds":[[[-90,-370]],[[90,370]]]},"calls":[{"method":"addProviderTiles","args":["OpenStreetMap.DE",1,"OpenStreetMap.DE",{"errorTileUrl":"","noWrap":false,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false}]},{"method":"addCircleMarkers","args":[14.82691,120.4242,6,null,"pnt",{"lineCap":null,"lineJoin":null,"clickable":true,"pointerEvents":null,"className":"","stroke":true,"color":"#333333","weight":2,"opacity":0.9,"fill":true,"fillColor":"#6666FF","fillOpacity":0.6,"dashArray":null},null,null,"<html> <head> <style> #popup { font-family: Arial, Helvetica, sans-serif; width: 100%; border-collapse: collapse; }   div.scrollableContainer { max-height: 2000px; max-width: 2000px; margin: 0px; background: transparent; }   div::-webkit-scrollbar {   width: 5px;   height: 5px; } div::-webkit-scrollbar-button {   width: 0px;   height: 0px; } div::-webkit-scrollbar-thumb {   background: #666666;   border: 0px none #ffffff;   border-radius: 0px; } div::-webkit-scrollbar-thumb:hover {   background: #333333; } div::-webkit-scrollbar-thumb:active {   background: #333333; } div::-webkit-scrollbar-track {   background: #e1e1e1;   border: 0px none #ffffff;   border-radius: 50px; } div::-webkit-scrollbar-track:hover {   background: #e1e1e1; } div::-webkit-scrollbar-track:active {   background: #e1e1e1; } div::-webkit-scrollbar-corner {   background: transparent; }  .leaflet-popup { \tposition: absolute; \ttext-align: center; }  .leaflet-popup-content-wrapper { \tpadding: 1px; \ttext-align: left; \t-webkit-border-radius: 2px; \t        border-radius: 2px; }  .leaflet-popup-content { \tmargin: 1px 1px 1px 1px; \tline-height: 1.5; \toverflow-y: visible; \toverflow-x: visible; \twidth: 300px; \theight: 225px; }  .leaflet-popup-content p { \tmargin: 8px 0; }  .leaflet-popup-tip-container { \tmargin: auto; \twidth: 40px; \theight: 20px; \tposition: relative; \toverflow: hidden; }  .leaflet-popup-tip { \twidth: 15px; \theight: 15px; \tpadding: 1px;  \tmargin: -10px auto 0;  \t-webkit-transform: rotate(45deg); \t   -moz-transform: rotate(45deg); \t    -ms-transform: rotate(45deg); \t     -o-transform: rotate(45deg); \t        transform: rotate(45deg); }  .leaflet-popup-content-wrapper{ \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4); \twidth: 300px; \theight: 225px; }  .leaflet-popup-tip { \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4);  }  .leaflet-container a.leaflet-popup-close-button { \tposition: absolute; \ttop: 0; \tright: -20px; \tpadding: 3px 0px 0 0; \ttext-align: center; \twidth: 18px; \theight: 14px; \tfont: 16px/14px Tahoma, Verdana, sans-serif; \tcolor: #c3c3c3; \ttext-decoration: none; \tfont-weight: bold; \tbackground: transparent; \t}  .leaflet-container a.leaflet-popup-close-button:hover { \tcolor: #999; \t}  .leaflet-popup-scrolled { \toverflow: visible; \tborder-bottom: 1px solid #ddd; \tborder-top: 1px solid #ddd; \t}   <\/style> <\/head> <body>   <div class=\"scrollableContainer\"> <table class=\"popup scrollable\"> <table id=\"popup\">  <iframe src='https://www.youtube.com/embed/yc6OMXUSlLA' frameborder=0 width=300 height=225><\/iframe>  <\/table> <\/body> <\/html>",{"maxWidth":800,"minWidth":50,"maxHeight":null,"autoPan":true,"keepInView":false,"closeButton":true,"zoomAnimation":true,"closeOnClick":true,"className":""},"1",null,null]},{"method":"addScaleBar","args":[{"maxWidth":100,"metric":true,"imperial":true,"updateWhenIdle":true,"position":"bottomleft"}]},{"method":"addHomeButton","args":[120.4242,14.82691,120.4242,14.82691,"Zoom to pnt","<strong> pnt <\/strong>","bottomright"]},{"method":"addLayersControl","args":["OpenStreetMap.DE","pnt",{"collapsed":true,"autoZIndex":true,"position":"topleft"}]}],"limits":{"lat":[14.82691,14.82691],"lng":[120.4242,120.4242]}},"evals":[],"jsHooks":{"render":[{"code":"function(el, x, data) {\n  return (\n      function(el, x, data) {\n\n      // get the leaflet map\n      var map = this; //HTMLWidgets.find('#' + el.id);\n\n      // we need a new div element because we have to handle\n      // the mouseover output separately\n      // debugger;\n      function addElement () {\n      // generate new div Element\n      var newDiv = $(document.createElement('div'));\n      // append at end of leaflet htmlwidget container\n      $(el).append(newDiv);\n      //provide ID and style\n      newDiv.addClass('lnlt');\n      newDiv.css({\n      'position': 'relative',\n      'bottomleft':  '0px',\n      'background-color': 'rgba(255, 255, 255, 0.7)',\n      'box-shadow': '0 0 2px #bbb',\n      'background-clip': 'padding-box',\n      'margin': '0',\n      'padding-left': '5px',\n      'color': '#333',\n      'font': '9px/1.5 \"Helvetica Neue\", Arial, Helvetica, sans-serif',\n      });\n      return newDiv;\n      }\n\n      // check for already existing lnlt class to not duplicate\n      var lnlt = $(el).find('.lnlt');\n\n      if(!lnlt.length) {\n      lnlt = addElement();\n      //$(el).keypress(function (e) {\n      //  if (e.which == 32 || event.keyCode == 32) {\n      //    alert('space key is pressed');\n      //  }\n      //});\n      // grab the special div we generated in the beginning\n      // and put the mousmove output there\n      map.on('mousemove', function (e) {\n      lnlt.text(\n                           ' x: ' + L.CRS.EPSG3857.project(e.latlng).x.toFixed(0) +\n                           ' | y: ' + L.CRS.EPSG3857.project(e.latlng).y.toFixed(0) +\n                           ' | epsg: 3857 ' +\n                           ' | proj4: +proj=merc +a=6378137 +b=6378137 +lat_ts=0.0 +lon_0=0.0 +x_0=0.0 +y_0=0 +k=1.0 +units=m +nadgrids=@null +no_defs ' +\n                           ' | lon: ' + (e.latlng.lng).toFixed(5) +\n                           ' | lat: ' + (e.latlng.lat).toFixed(5) +\n                           ' | zoom: ' + map.getZoom() + ' ');\n      });\n      };\n      }\n      ).call(this.getMap(), el, x, data);\n}","data":null}]}}</script><!--/html_preserve-->

<br>

Activities in all diabetes camps are designed to impart practical knowledge about how to manage diabetes. With great deal of care the concepts are taught tailored to the level of understanding of the audience. Lectures are minimized as these prove to be ineffective in motivating children and teens to adapt the behaviour that is being espoused. Instead, concepts are wrapped around fun activities that the children enjoy and will remember.

A typical curriculum for a diabetes camp will include the following key concepts:

- Blood Glucose Monitoring
- Insulin and its effect
- Hypoglycemia, Hyperglycemia and its prevention and management
- Food groups and eating the right kind of foods
- Complications of diabetes
- and if your're lucky there's a topic on oral health


# PSPME

PSPME stands for [Philippine Society of Pediatric Metabolism and Endocrinology](http://www.pspme.com.ph/). Managing children with diabetes technically belong to the province of pediatric endocrinologist but because the number of specialists in this specialty is so few, a lot of type 1 diabetics are managed by physicians with a different specialty. Even generalist manage juvenile diabetics in the provinces.

But the pediatric endocrinologist offers something more than other doctors who know how to manage diabetes. They offer an approach that is more attentive to the growth and development of children and teens. Addressing issues like developmental milestones and the child's perception of himself or herself as a person with diabetes, which are easily overlook by other specialties. 

Click on the point in the center of the map to see a picture of the camp site in 2013.  The site for the camp varies from year to year, which for some kids is an advantage as they get to see and experience different locales each year.



```r
batangas <- geocode("Nasugbu, Batnagas, Philippines")
###Source : https://maps.googleapis.com/maps/api/geocode/json?address=Nasugbu%2C%20Batnagas%2C%20Philippines
###      lon      lat
###1 120.689 14.09404
pnt <- data.frame(x = 120.689, y = 14.09404)
pnt <- st_as_sf(pnt, coords = c("x", "y"), crs = 4326)


img1 <- "https://docofi.github.io/extras/www/pspme.jpg"

mapview(pnt, map.types = "Esri.WorldImagery",
        popup = popupImage(img1, src = "remote"))
```

<!--html_preserve--><div id="htmlwidget-209c9e26e2c165b780ff" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-209c9e26e2c165b780ff">{"x":{"options":{"minZoom":1,"maxZoom":100,"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}},"bounceAtZoomLimits":false,"maxBounds":[[[-90,-370]],[[90,370]]]},"calls":[{"method":"addProviderTiles","args":["Esri.WorldImagery",1,"Esri.WorldImagery",{"errorTileUrl":"","noWrap":false,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false}]},{"method":"addCircleMarkers","args":[14.09404,120.689,6,null,"pnt",{"lineCap":null,"lineJoin":null,"clickable":true,"pointerEvents":null,"className":"","stroke":true,"color":"#333333","weight":2,"opacity":0.9,"fill":true,"fillColor":"#6666FF","fillOpacity":0.6,"dashArray":null},null,null,["<html> <head> <style> #popup { font-family: Arial, Helvetica, sans-serif; width: 100%; border-collapse: collapse; }   div.scrollableContainer { max-height: 2000px; max-width: 2000px; margin: 0px; background: transparent; }   div::-webkit-scrollbar {   width: 5px;   height: 5px; } div::-webkit-scrollbar-button {   width: 0px;   height: 0px; } div::-webkit-scrollbar-thumb {   background: #666666;   border: 0px none #ffffff;   border-radius: 0px; } div::-webkit-scrollbar-thumb:hover {   background: #333333; } div::-webkit-scrollbar-thumb:active {   background: #333333; } div::-webkit-scrollbar-track {   background: #e1e1e1;   border: 0px none #ffffff;   border-radius: 50px; } div::-webkit-scrollbar-track:hover {   background: #e1e1e1; } div::-webkit-scrollbar-track:active {   background: #e1e1e1; } div::-webkit-scrollbar-corner {   background: transparent; }  .leaflet-popup { \tposition: absolute; \ttext-align: center; }  .leaflet-popup-content-wrapper { \tpadding: 1px; \ttext-align: left; \t-webkit-border-radius: 2px; \t        border-radius: 2px; }  .leaflet-popup-content { \tmargin: 1px 1px 1px 1px; \tline-height: 1.5; \toverflow-y: visible; \toverflow-x: visible; \twidth: 300px; \theight: 100%px; }  .leaflet-popup-content p { \tmargin: 8px 0; }  .leaflet-popup-tip-container { \tmargin: auto; \twidth: 40px; \theight: 20px; \tposition: relative; \toverflow: hidden; }  .leaflet-popup-tip { \twidth: 15px; \theight: 15px; \tpadding: 1px;  \tmargin: -10px auto 0;  \t-webkit-transform: rotate(45deg); \t   -moz-transform: rotate(45deg); \t    -ms-transform: rotate(45deg); \t     -o-transform: rotate(45deg); \t        transform: rotate(45deg); }  .leaflet-popup-content-wrapper{ \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4); \twidth: 300px; \theight: 100%px; }  .leaflet-popup-tip { \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4);  }  .leaflet-container a.leaflet-popup-close-button { \tposition: absolute; \ttop: 0; \tright: -20px; \tpadding: 3px 0px 0 0; \ttext-align: center; \twidth: 18px; \theight: 14px; \tfont: 16px/14px Tahoma, Verdana, sans-serif; \tcolor: #c3c3c3; \ttext-decoration: none; \tfont-weight: bold; \tbackground: transparent; \t}  .leaflet-container a.leaflet-popup-close-button:hover { \tcolor: #999; \t}  .leaflet-popup-scrolled { \toverflow: visible; \tborder-bottom: 1px solid #ddd; \tborder-top: 1px solid #ddd; \t}   <\/style> <\/head> <body>   <div class=\"scrollableContainer\"> <table class=\"popup scrollable\"> <table id=\"popup\">  <image src='https://docofi.github.io/extras/www/pspme.jpg' width=300 height=100%>  <\/table> <\/body> <\/html>"],{"maxWidth":800,"minWidth":50,"maxHeight":null,"autoPan":true,"keepInView":false,"closeButton":true,"zoomAnimation":true,"closeOnClick":true,"className":""},"1",null,null]},{"method":"addScaleBar","args":[{"maxWidth":100,"metric":true,"imperial":true,"updateWhenIdle":true,"position":"bottomleft"}]},{"method":"addHomeButton","args":[120.689,14.09404,120.689,14.09404,"Zoom to pnt","<strong> pnt <\/strong>","bottomright"]},{"method":"addLayersControl","args":["Esri.WorldImagery","pnt",{"collapsed":true,"autoZIndex":true,"position":"topleft"}]}],"limits":{"lat":[14.09404,14.09404],"lng":[120.689,120.689]}},"evals":[],"jsHooks":{"render":[{"code":"function(el, x, data) {\n  return (\n      function(el, x, data) {\n\n      // get the leaflet map\n      var map = this; //HTMLWidgets.find('#' + el.id);\n\n      // we need a new div element because we have to handle\n      // the mouseover output separately\n      // debugger;\n      function addElement () {\n      // generate new div Element\n      var newDiv = $(document.createElement('div'));\n      // append at end of leaflet htmlwidget container\n      $(el).append(newDiv);\n      //provide ID and style\n      newDiv.addClass('lnlt');\n      newDiv.css({\n      'position': 'relative',\n      'bottomleft':  '0px',\n      'background-color': 'rgba(255, 255, 255, 0.7)',\n      'box-shadow': '0 0 2px #bbb',\n      'background-clip': 'padding-box',\n      'margin': '0',\n      'padding-left': '5px',\n      'color': '#333',\n      'font': '9px/1.5 \"Helvetica Neue\", Arial, Helvetica, sans-serif',\n      });\n      return newDiv;\n      }\n\n      // check for already existing lnlt class to not duplicate\n      var lnlt = $(el).find('.lnlt');\n\n      if(!lnlt.length) {\n      lnlt = addElement();\n      //$(el).keypress(function (e) {\n      //  if (e.which == 32 || event.keyCode == 32) {\n      //    alert('space key is pressed');\n      //  }\n      //});\n      // grab the special div we generated in the beginning\n      // and put the mousmove output there\n      map.on('mousemove', function (e) {\n      lnlt.text(\n                           ' x: ' + L.CRS.EPSG3857.project(e.latlng).x.toFixed(0) +\n                           ' | y: ' + L.CRS.EPSG3857.project(e.latlng).y.toFixed(0) +\n                           ' | epsg: 3857 ' +\n                           ' | proj4: +proj=merc +a=6378137 +b=6378137 +lat_ts=0.0 +lon_0=0.0 +x_0=0.0 +y_0=0 +k=1.0 +units=m +nadgrids=@null +no_defs ' +\n                           ' | lon: ' + (e.latlng.lng).toFixed(5) +\n                           ' | lat: ' + (e.latlng.lat).toFixed(5) +\n                           ' | zoom: ' + map.getZoom() + ' ');\n      });\n      };\n      }\n      ).call(this.getMap(), el, x, data);\n}","data":null}]}}</script><!--/html_preserve-->


# Camp COPE

COPE stands for Children Overcoming Diabetes Problems Everywhere. The 
[Philippine Center for Diabetes Education Foundation, Inc (Diabetes Center)](http://www.pcdef.org/camp-cope) is the organization behind Camp Cope. The first time I attended their camp, they had it in Laguna, but now they have taken a liking to Tagaytay. Having the camp in Tagaytay takes advantage of the cool weather and the provincial surrounding. Plus Tagaytay has been developing several educational tourism sites that are perfect to pique the interest of children like zoos and parks. The camp offers a different destination every year for the children to enjoy.

Click on the point in the center again to see the theme for the camp in 2015.


```r
tagaytay <- geocode("Tagaytay Haven Hotel, Mendez, Tagaytay")
###Source : https://maps.googleapis.com/maps/api/geocode/json?address=Tagaytay%20Haven%20Hotel%2C%20Mendez%2C%20Tagaytay
###       lon      lat
###1 120.9166 14.09706
pnt <- data.frame(x = 120.9166, y = 14.09706)
pnt <- st_as_sf(pnt, coords = c("x", "y"), crs = 4326)


img2 <- "https://docofi.github.io/extras/www/campcope.jpg"

mapview(pnt, map.types = "Esri.WorldImagery",
        popup = popupImage(img2, src = "remote"))
```

<!--html_preserve--><div id="htmlwidget-f3db6d1779e040e019e5" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-f3db6d1779e040e019e5">{"x":{"options":{"minZoom":1,"maxZoom":100,"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}},"bounceAtZoomLimits":false,"maxBounds":[[[-90,-370]],[[90,370]]]},"calls":[{"method":"addProviderTiles","args":["Esri.WorldImagery",1,"Esri.WorldImagery",{"errorTileUrl":"","noWrap":false,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false}]},{"method":"addCircleMarkers","args":[14.09706,120.9166,6,null,"pnt",{"lineCap":null,"lineJoin":null,"clickable":true,"pointerEvents":null,"className":"","stroke":true,"color":"#333333","weight":2,"opacity":0.9,"fill":true,"fillColor":"#6666FF","fillOpacity":0.6,"dashArray":null},null,null,["<html> <head> <style> #popup { font-family: Arial, Helvetica, sans-serif; width: 100%; border-collapse: collapse; }   div.scrollableContainer { max-height: 2000px; max-width: 2000px; margin: 0px; background: transparent; }   div::-webkit-scrollbar {   width: 5px;   height: 5px; } div::-webkit-scrollbar-button {   width: 0px;   height: 0px; } div::-webkit-scrollbar-thumb {   background: #666666;   border: 0px none #ffffff;   border-radius: 0px; } div::-webkit-scrollbar-thumb:hover {   background: #333333; } div::-webkit-scrollbar-thumb:active {   background: #333333; } div::-webkit-scrollbar-track {   background: #e1e1e1;   border: 0px none #ffffff;   border-radius: 50px; } div::-webkit-scrollbar-track:hover {   background: #e1e1e1; } div::-webkit-scrollbar-track:active {   background: #e1e1e1; } div::-webkit-scrollbar-corner {   background: transparent; }  .leaflet-popup { \tposition: absolute; \ttext-align: center; }  .leaflet-popup-content-wrapper { \tpadding: 1px; \ttext-align: left; \t-webkit-border-radius: 2px; \t        border-radius: 2px; }  .leaflet-popup-content { \tmargin: 1px 1px 1px 1px; \tline-height: 1.5; \toverflow-y: visible; \toverflow-x: visible; \twidth: 300px; \theight: 100%px; }  .leaflet-popup-content p { \tmargin: 8px 0; }  .leaflet-popup-tip-container { \tmargin: auto; \twidth: 40px; \theight: 20px; \tposition: relative; \toverflow: hidden; }  .leaflet-popup-tip { \twidth: 15px; \theight: 15px; \tpadding: 1px;  \tmargin: -10px auto 0;  \t-webkit-transform: rotate(45deg); \t   -moz-transform: rotate(45deg); \t    -ms-transform: rotate(45deg); \t     -o-transform: rotate(45deg); \t        transform: rotate(45deg); }  .leaflet-popup-content-wrapper{ \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4); \twidth: 300px; \theight: 100%px; }  .leaflet-popup-tip { \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4);  }  .leaflet-container a.leaflet-popup-close-button { \tposition: absolute; \ttop: 0; \tright: -20px; \tpadding: 3px 0px 0 0; \ttext-align: center; \twidth: 18px; \theight: 14px; \tfont: 16px/14px Tahoma, Verdana, sans-serif; \tcolor: #c3c3c3; \ttext-decoration: none; \tfont-weight: bold; \tbackground: transparent; \t}  .leaflet-container a.leaflet-popup-close-button:hover { \tcolor: #999; \t}  .leaflet-popup-scrolled { \toverflow: visible; \tborder-bottom: 1px solid #ddd; \tborder-top: 1px solid #ddd; \t}   <\/style> <\/head> <body>   <div class=\"scrollableContainer\"> <table class=\"popup scrollable\"> <table id=\"popup\">  <image src='https://docofi.github.io/extras/www/campcope.jpg' width=300 height=100%>  <\/table> <\/body> <\/html>"],{"maxWidth":800,"minWidth":50,"maxHeight":null,"autoPan":true,"keepInView":false,"closeButton":true,"zoomAnimation":true,"closeOnClick":true,"className":""},"1",null,null]},{"method":"addScaleBar","args":[{"maxWidth":100,"metric":true,"imperial":true,"updateWhenIdle":true,"position":"bottomleft"}]},{"method":"addHomeButton","args":[120.9166,14.09706,120.9166,14.09706,"Zoom to pnt","<strong> pnt <\/strong>","bottomright"]},{"method":"addLayersControl","args":["Esri.WorldImagery","pnt",{"collapsed":true,"autoZIndex":true,"position":"topleft"}]}],"limits":{"lat":[14.09706,14.09706],"lng":[120.9166,120.9166]}},"evals":[],"jsHooks":{"render":[{"code":"function(el, x, data) {\n  return (\n      function(el, x, data) {\n\n      // get the leaflet map\n      var map = this; //HTMLWidgets.find('#' + el.id);\n\n      // we need a new div element because we have to handle\n      // the mouseover output separately\n      // debugger;\n      function addElement () {\n      // generate new div Element\n      var newDiv = $(document.createElement('div'));\n      // append at end of leaflet htmlwidget container\n      $(el).append(newDiv);\n      //provide ID and style\n      newDiv.addClass('lnlt');\n      newDiv.css({\n      'position': 'relative',\n      'bottomleft':  '0px',\n      'background-color': 'rgba(255, 255, 255, 0.7)',\n      'box-shadow': '0 0 2px #bbb',\n      'background-clip': 'padding-box',\n      'margin': '0',\n      'padding-left': '5px',\n      'color': '#333',\n      'font': '9px/1.5 \"Helvetica Neue\", Arial, Helvetica, sans-serif',\n      });\n      return newDiv;\n      }\n\n      // check for already existing lnlt class to not duplicate\n      var lnlt = $(el).find('.lnlt');\n\n      if(!lnlt.length) {\n      lnlt = addElement();\n      //$(el).keypress(function (e) {\n      //  if (e.which == 32 || event.keyCode == 32) {\n      //    alert('space key is pressed');\n      //  }\n      //});\n      // grab the special div we generated in the beginning\n      // and put the mousmove output there\n      map.on('mousemove', function (e) {\n      lnlt.text(\n                           ' x: ' + L.CRS.EPSG3857.project(e.latlng).x.toFixed(0) +\n                           ' | y: ' + L.CRS.EPSG3857.project(e.latlng).y.toFixed(0) +\n                           ' | epsg: 3857 ' +\n                           ' | proj4: +proj=merc +a=6378137 +b=6378137 +lat_ts=0.0 +lon_0=0.0 +x_0=0.0 +y_0=0 +k=1.0 +units=m +nadgrids=@null +no_defs ' +\n                           ' | lon: ' + (e.latlng.lng).toFixed(5) +\n                           ' | lat: ' + (e.latlng.lat).toFixed(5) +\n                           ' | zoom: ' + map.getZoom() + ' ');\n      });\n      };\n      }\n      ).call(this.getMap(), el, x, data);\n}","data":null}]}}</script><!--/html_preserve-->


# Davao Diabetes Camp

The diabetes camp in Davao is run by one of the graduates of the PSPEM and I believe that she is still the lone Pediatric Endocrinologist in the island of Mindanao. The camp in Davao is not held yearly, which underscores the burden borne by this different organizations in order to have children with diabetes have something to look forward to during the summer. And believe me, the children are already counting the number of days till the next camp even before they board the bus going back to their parents. Once a kid experiences camp, he or she we'll want to go back. Unfortuantely, not everyone can be accomodated every year to make room for newly diagnosed kids.

If you want to see the video of the camp in Davao, which was held in Samal island, one of the tourist spots in Davao, click on the point in the middle of the map. The Point in the map is located somewhat inland that is because the map is centerd on the centroid of Samal island but the camp itself is located in one of the resorts near the coastline.


```r
davao <- geocode("samal Island, Davao, Philippines")
###Source : https://maps.googleapis.com/maps/api/geocode/json?address=samal%20Island%2C%20Davao%2C%20Philippines
###       lon      lat
###1 125.7188 7.103312
pnt <- data.frame(x = 125.7188, y = 7.103312)
pnt <- st_as_sf(pnt, coords = c("x", "y"), crs = 4326)

mapview(pnt, popup = mapview:::popupIframe("https://www.youtube.com/embed/NVMguNlSsKU", width = 300, height = 225), map.types = "OpenStreetMap.DE", zoom = 6)
```

<!--html_preserve--><div id="htmlwidget-df70ee417d8672911dc0" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-df70ee417d8672911dc0">{"x":{"options":{"minZoom":1,"maxZoom":100,"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}},"bounceAtZoomLimits":false,"maxBounds":[[[-90,-370]],[[90,370]]]},"calls":[{"method":"addProviderTiles","args":["OpenStreetMap.DE",1,"OpenStreetMap.DE",{"errorTileUrl":"","noWrap":false,"zIndex":null,"unloadInvisibleTiles":null,"updateWhenIdle":null,"detectRetina":false,"reuseTiles":false}]},{"method":"addCircleMarkers","args":[7.103312,125.7188,6,null,"pnt",{"lineCap":null,"lineJoin":null,"clickable":true,"pointerEvents":null,"className":"","stroke":true,"color":"#333333","weight":2,"opacity":0.9,"fill":true,"fillColor":"#6666FF","fillOpacity":0.6,"dashArray":null},null,null,"<html> <head> <style> #popup { font-family: Arial, Helvetica, sans-serif; width: 100%; border-collapse: collapse; }   div.scrollableContainer { max-height: 2000px; max-width: 2000px; margin: 0px; background: transparent; }   div::-webkit-scrollbar {   width: 5px;   height: 5px; } div::-webkit-scrollbar-button {   width: 0px;   height: 0px; } div::-webkit-scrollbar-thumb {   background: #666666;   border: 0px none #ffffff;   border-radius: 0px; } div::-webkit-scrollbar-thumb:hover {   background: #333333; } div::-webkit-scrollbar-thumb:active {   background: #333333; } div::-webkit-scrollbar-track {   background: #e1e1e1;   border: 0px none #ffffff;   border-radius: 50px; } div::-webkit-scrollbar-track:hover {   background: #e1e1e1; } div::-webkit-scrollbar-track:active {   background: #e1e1e1; } div::-webkit-scrollbar-corner {   background: transparent; }  .leaflet-popup { \tposition: absolute; \ttext-align: center; }  .leaflet-popup-content-wrapper { \tpadding: 1px; \ttext-align: left; \t-webkit-border-radius: 2px; \t        border-radius: 2px; }  .leaflet-popup-content { \tmargin: 1px 1px 1px 1px; \tline-height: 1.5; \toverflow-y: visible; \toverflow-x: visible; \twidth: 300px; \theight: 225px; }  .leaflet-popup-content p { \tmargin: 8px 0; }  .leaflet-popup-tip-container { \tmargin: auto; \twidth: 40px; \theight: 20px; \tposition: relative; \toverflow: hidden; }  .leaflet-popup-tip { \twidth: 15px; \theight: 15px; \tpadding: 1px;  \tmargin: -10px auto 0;  \t-webkit-transform: rotate(45deg); \t   -moz-transform: rotate(45deg); \t    -ms-transform: rotate(45deg); \t     -o-transform: rotate(45deg); \t        transform: rotate(45deg); }  .leaflet-popup-content-wrapper{ \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4); \twidth: 300px; \theight: 225px; }  .leaflet-popup-tip { \tbackground: #4c4c4c; \tbox-shadow: 0 3px 14px rgba(0,0,0,0.4);  }  .leaflet-container a.leaflet-popup-close-button { \tposition: absolute; \ttop: 0; \tright: -20px; \tpadding: 3px 0px 0 0; \ttext-align: center; \twidth: 18px; \theight: 14px; \tfont: 16px/14px Tahoma, Verdana, sans-serif; \tcolor: #c3c3c3; \ttext-decoration: none; \tfont-weight: bold; \tbackground: transparent; \t}  .leaflet-container a.leaflet-popup-close-button:hover { \tcolor: #999; \t}  .leaflet-popup-scrolled { \toverflow: visible; \tborder-bottom: 1px solid #ddd; \tborder-top: 1px solid #ddd; \t}   <\/style> <\/head> <body>   <div class=\"scrollableContainer\"> <table class=\"popup scrollable\"> <table id=\"popup\">  <iframe src='https://www.youtube.com/embed/NVMguNlSsKU' frameborder=0 width=300 height=225><\/iframe>  <\/table> <\/body> <\/html>",{"maxWidth":800,"minWidth":50,"maxHeight":null,"autoPan":true,"keepInView":false,"closeButton":true,"zoomAnimation":true,"closeOnClick":true,"className":""},"1",null,null]},{"method":"addScaleBar","args":[{"maxWidth":100,"metric":true,"imperial":true,"updateWhenIdle":true,"position":"bottomleft"}]},{"method":"addHomeButton","args":[125.7188,7.103312,125.7188,7.103312,"Zoom to pnt","<strong> pnt <\/strong>","bottomright"]},{"method":"addLayersControl","args":["OpenStreetMap.DE","pnt",{"collapsed":true,"autoZIndex":true,"position":"topleft"}]}],"limits":{"lat":[7.103312,7.103312],"lng":[125.7188,125.7188]}},"evals":[],"jsHooks":{"render":[{"code":"function(el, x, data) {\n  return (\n      function(el, x, data) {\n\n      // get the leaflet map\n      var map = this; //HTMLWidgets.find('#' + el.id);\n\n      // we need a new div element because we have to handle\n      // the mouseover output separately\n      // debugger;\n      function addElement () {\n      // generate new div Element\n      var newDiv = $(document.createElement('div'));\n      // append at end of leaflet htmlwidget container\n      $(el).append(newDiv);\n      //provide ID and style\n      newDiv.addClass('lnlt');\n      newDiv.css({\n      'position': 'relative',\n      'bottomleft':  '0px',\n      'background-color': 'rgba(255, 255, 255, 0.7)',\n      'box-shadow': '0 0 2px #bbb',\n      'background-clip': 'padding-box',\n      'margin': '0',\n      'padding-left': '5px',\n      'color': '#333',\n      'font': '9px/1.5 \"Helvetica Neue\", Arial, Helvetica, sans-serif',\n      });\n      return newDiv;\n      }\n\n      // check for already existing lnlt class to not duplicate\n      var lnlt = $(el).find('.lnlt');\n\n      if(!lnlt.length) {\n      lnlt = addElement();\n      //$(el).keypress(function (e) {\n      //  if (e.which == 32 || event.keyCode == 32) {\n      //    alert('space key is pressed');\n      //  }\n      //});\n      // grab the special div we generated in the beginning\n      // and put the mousmove output there\n      map.on('mousemove', function (e) {\n      lnlt.text(\n                           ' x: ' + L.CRS.EPSG3857.project(e.latlng).x.toFixed(0) +\n                           ' | y: ' + L.CRS.EPSG3857.project(e.latlng).y.toFixed(0) +\n                           ' | epsg: 3857 ' +\n                           ' | proj4: +proj=merc +a=6378137 +b=6378137 +lat_ts=0.0 +lon_0=0.0 +x_0=0.0 +y_0=0 +k=1.0 +units=m +nadgrids=@null +no_defs ' +\n                           ' | lon: ' + (e.latlng.lng).toFixed(5) +\n                           ' | lat: ' + (e.latlng.lat).toFixed(5) +\n                           ' | zoom: ' + map.getZoom() + ' ');\n      });\n      };\n      }\n      ).call(this.getMap(), el, x, data);\n}","data":null}]}}</script><!--/html_preserve-->

Thank you for reading up to this point I hope you enjoyed this little presentation and may you pass on what you have learned to someone who has a diabetic kid in the family.

The different organizations that hold the camps may be reached thru the following links:

[Rainbow Camp Foundation Philippines Incorporated](http://www.isdfi.org/societies/rc/)
Address: 52 Apitong Street, 1808, Marikina, Metro Manila
Phone: (02) 942 0313
email: 

[Philippine Society of Pediatric Metabolism and Endocrinology](http://www.pspme.com.ph/)
Address: Medical Arts Building Room 240
Cardinal Santos Medical Center
Wilson St, Greenhills
San Juan, Metro Manila
Phone: (632) 727-7655  /  (632) 727-0001 (loc. 840)
email: admin@pspme.com.ph

[Philippine Center for Diabetes Education Foundation, Inc (Diabetes Center)](http://www.pcdef.org/camp-cope)
Address:2nd Floor, Hall C, Makati Medical Center, 	
2 Amorsolo St., Legaspi Village, 	 
Makati City
Phone: +632 892 1064 /  +632 888 8999 local 2287
Mobile: +63998 567 8978 /  +63922 808 0538
email: diabetescenter@pcdef.org
Facebook: http://www.facebook.com/diabcenterRP
Instagram: diabetes.center
Twitter: @DiabCtrPhil

You may inquire about the Davao Diabetes Camp through the
[Philippine Society of Pediatric Metabolism and Endocrinology](http://www.pspme.com.ph/)
Address: Medical Arts Building Room 240
Cardinal Santos Medical Center
Wilson St, Greenhills
San Juan, Metro Manila
Phone: (632) 727-7655  /  (632) 727-0001 (loc. 840)
email: admin@pspme.com.ph

