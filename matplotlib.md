# matplotlib

**show plot in the web page**

    %matplotlib inline
    
**histogram**

histogram of place id

    place = df_train['place_id']
    place_hist = np.histogram(place, 10000)[0]
    
    plt.plot(place_hist)
    plt.grid(True)
    plt.show()

**bar**

    a,b = np.histogram([7,5,7,8], 3)
    plt.bar(b[:-1], a, width=1)  
  
**scatter**

    xs = df_train[df_train['place_id'] == 9544215131].x
    ys = df_train[df_train['place_id'] == 9544215131].y
    plt.scatter(xs, ys)
    plt.grid(True)
    plt.xlabel("X")
    plt.ylabel("Y")
    plt.tight_layout()
    plt.xlim(0,10)
    plt.ylim(0,10)
    plt.show()

We can zoom in to a certain area by changing e.g `plt.xlim(5,6)` , `plt.ylim(0,2)`

**using colormap**
    
    colors = plt.cm.rainbow(np.linspace(0,1,20))
    
this create list of 20 different colors, `np.linspace(0,1,20)` return array of 20 numbers that divide interval [0,1] evently 

    tail = list(df_placecounts[-20:].index)
    for color, place_id in enumerate(tail):
        place = df_train[df_train['place_id'] == place_id]
        plt.scatter(place.x, place.y, color=colors[i], linewidth=0)
    
**change size of the canvas**

    figure(1, figsize=(12,12))

**put legend in best location**

    plt.legend((es_bar[0], lucene_bar[0]), ('ES', 'Lucene'), loc='best')
    
It will try to put the legend a location that doesn't interfer the plot


**references**

* http://nbviewer.jupyter.org/github/WeatherGod/AnatomyOfMatplotlib/blob/master/AnatomyOfMatplotlib-Part1-Figures_Subplots_and_layouts.ipynb
* http://matplotlib.org/users/pyplot_tutorial.html
