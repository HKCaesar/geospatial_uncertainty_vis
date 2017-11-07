# geospatial_uncertainty_vis

Python script to plot geospatial uncertainty in a mathematically rigorous manner.  We assume that all events to be plotted are of the same type, so we are concerned with the scenario of whether event1, event2, or event3 occurred at location (x,y).

Event locations are often reported via (latitude, longitude) as well as uncertainty in position.  We adopt the frequent assumption that errors are Gaussian in nature.  Positional uncertainty can be represented by a positional ellipse with width (sigma_x) and height (sigma_y) represented by uncertainty in longitude and latitude, respectively.  The eye is typically drawn to large objects (which are less certain in this case), so we can partially offset this effect by scaling opacity inversely with uncertainty, as shown below:

![Alt text](/example_plots/ellipse_uncertainty.png?raw=true "Optional Title")

The above plot cannot convey the joint likelihood (shown below) of an event at each position.  

![Alt text](/example_plots/gauss_probability_map.png?raw=true "Optional Title")

We can use this probability map to more accurately convey positional uncertainty by assigning the alpha channel (i.e. opacity) as the probability map. The opacity in this final image is proportional to the probability that an event occured at that location, and more accurately conveys the true uncertainty in event location.

![Alt text](/example_plots/gauss_uncertainty.png?raw=true "Optional Title")



################################

geospatial_uncertainty.py

dependencies:

	cv2
 	numpy
  	matplotlib

update line 15 with the correct '/path/to/geospatial_uncertainty_vis'

The python script generates a number of random points, computes the combined probability map, and visualizes location uncertainty by plotting the points on a map image.

To execute:

	cd /path/to/geospatial_uncertainty_vis
	python geospatial_uncertainty.py
