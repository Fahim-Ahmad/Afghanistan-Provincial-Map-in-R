# Afghanistan Provincial Map in R

```
library(tidyverse)
library(sf)

# unzip("input/afghan_province.zip", exdir = "input")
map <- st_read("input/afghan_province.shp")
map <- full_join(map, read.csv("input/map_labels.csv"), by = c("prov" = "province"))


map %>% 
  ggplot() +
  geom_sf(fill = "skyblue", color = "gray50", show.legend = F, alpha = 0.5) +
  geom_text(aes(position_x, position_y, label = prov), size = 3) +
  theme_void() +
  theme(plot.title = element_text(hjust = 0.5, size = 15)) +
  labs(title = "Afghanistan Provincial Map", fill = NULL) +
  NULL

ggsave("output/map_1.png", width = 12, height = 8)

```
![](map_1.png)


```
map %>% 
  ggplot() +
  geom_sf(aes(fill = prov), color = "gray50", show.legend = F, alpha = 0.5) +
  geom_text(aes(position_x, position_y, label = prov), size = 3) +
  theme_void() +
  theme(plot.title = element_text(hjust = 0.5, size = 15)) +
  labs(title = "Afghanistan Provincial Map", fill = NULL) +
  NULL

ggsave("output/map_2.png", width = 12, height = 8)

```

![](map_2.png)
