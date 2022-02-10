To edit the metadata of a particular Season in a show use the `seasons` attribute.

The mapping name is the season number (use 0 for specials).

A simple example is below:
```yaml
metadata:
  "Avatar: The Last Airbender":
    seasons:
      1:
        title: "Book One: Water"
        summary: >-
              After a lapse of 100 years, the Avatar-spiritual master of the elements-has returned. And just in 
              the nick of time. The Four Nations (Water, Earth, Fire, and Air) have become unbalanced. The Fire 
              Nation wants to rule the world, and its first conquest will be the Northern Water Tribe. It's up to 
              a 12-year-old Airbender named Aang to find a way to stop it. Join Aang, Katara, Sokka, Momo, and 
              Appa as they head north on the adventure of a lifetime.
      2:
        title: "Book Two: Earth"
        summary: >-
              Avatar Aang continues his quest to master the four elements before the end of summer. Together with
              Katara, Sokka, Momo, and Appa, he journeys across the Earth Kingdom in search of an Earthbending
              mentor. Along the way, he confronts Princess Azula, treacherous  daughter of Firelord Ozai and 
              sister to Prince Zuko. More powerful than her brother, Azula will stop nothing to defeat the Avatar. 
              But Aang and the gang find plenty of Earth Kingdom allies to help them along the way. From the swamps 
              of the South to the Earth King's palace, Avatar: Book 2 is an adventure like no other.
      3:
        title: "Book Three: Fire"
        summary: >-
              Having survived the terrible battle with Azula, Aang faces new challenges as he and his brave
              friends secretly enter the Fire Nation. Their quest is to find and defeat Firelord Ozai. Along
              the way, they discover that Ozai has plans of his own. The leader of the Fire Nation intends to 
              use the massive power of Sozin's comet to spread his dominion permanently across the four nations. 
              Short on time, Aang has a lot of bending to learn and no master to help him learn it. However, his 
              friends are there to help, and he finds unexpected allies deep in the heart of the Fire Nation. In 
              the spectacular four-part conclusion, Aang must fulfill his destiny and become a fully realized 
              Avatar, or watch the world go up in smoke.
```

The available attributes for each season are as follows

| Name            | Attribute         | Allowed Values                                  |
|:----------------|:------------------|:------------------------------------------------|
| Title           | `title`           | Text to change Title                            |
| Summary         | `summary`         | Text to change Summary                          |
| URL Poster      | `url_poster`      | URL of image publicly available on the internet |
| File Poster     | `file_poster`     | Path to image in the file system                |
| URL Background  | `url_background`  | URL of image publicly available on the internet |
| File Background | `file_background` | Path to image in the file system                |
