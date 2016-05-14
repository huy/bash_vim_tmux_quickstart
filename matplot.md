# matplot

**histogram**

  # histogram of place id
  place = df_train['place_id']
  place_hist = np.histogram(place, 10000)[0]
  
  plt.plot(place_hist)
  plt.grid(True)
  plt.show()

**bar**

  a,b = np.histogram([7,5,7,8], 3)
  plt.bar(b[:-1], a, width=1)  
  
**scatter**

  plt.scatter(df_train[df_train['place_id'] == 9544215131].x, df_train[df_train['place_id'] == 9544215131].y)
  plt.grid(True)
  plt.xlabel("X")
  plt.ylabel("Y")
  plt.tight_layout()
  plt.xlim(0,10)
  plt.ylim(0,10)
  plt.show()
