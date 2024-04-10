# DOOM style 3d (raycasting) game in Python (based on Wolfenstein 3d)
By StanislavPetrovV: https://github.com/StanislavPetrovV 

https://github.com/StanislavPetrovV/DOOM-style-Game

Control: 'WASD' + mouse

## Twenkid's fixes, 10.4.2024

```python
class SpriteObject:  ...  image = pg.transform.scale(self.image, (int(proj_width), int(proj_height)))
class Weapon: ...  [pg.transform.smoothscale(img, (int(self.image.get_width() * scale), int(self.image.get_height() * scale)))
class RayCasting: get_objects_to_render: ...  wall_column = pg.transform.scale(wall_column, (int(SCALE), int(proj_height)))
```
On pygame 2.0.1, SDL 2.0.14, Py 3.9.7

Otherwise erros (pygame wants int, receives float):
```
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
Traceback (most recent call last):
  File "Z:\DOOM-style-Game\main.py", line 73, in <module>
    game = Game()
  File "Z:\DOOM-style-Game\main.py", line 26, in __init__
    self.new_game()
  File "Z:\DOOM-style-Game\main.py", line 34, in new_game
    self.weapon = Weapon(self)
  File "Z:\DOOM-style-Game\weapon.py", line 8, in __init__
    [pg.transform.smoothscale(img, (self.image.get_width() * scale, self.image.get_height() * scale))
  File "Z:\DOOM-style-Game\weapon.py", line 8, in <listcomp>
    [pg.transform.smoothscale(img, (self.image.get_width() * scale, self.image.get_height() * scale))
TypeError: integer argument expected, got float
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
Traceback (most recent call last):
  File "Z:\DOOM-style-Game\main.py", line 74, in <module>
    game.run()
  File "Z:\DOOM-style-Game\main.py", line 68, in run
    self.update()
  File "Z:\DOOM-style-Game\main.py", line 41, in update
    self.raycasting.update()
  File "Z:\DOOM-style-Game\raycasting.py", line 105, in update
    self.get_objects_to_render()
  File "Z:\DOOM-style-Game\raycasting.py", line 22, in get_objects_to_render
    wall_column = pg.transform.scale(wall_column, (SCALE, proj_height))
TypeError: integer argument expected, got float

libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile
Traceback (most recent call last):
  File "Z:\DOOM-style-Game\main.py", line 74, in <module>
    game.run()
  File "Z:\DOOM-style-Game\main.py", line 68, in run
    self.update()
  File "Z:\DOOM-style-Game\main.py", line 42, in update
    self.object_handler.update()
  File "Z:\DOOM-style-Game\object_handler.py", line 76, in update
    [sprite.update() for sprite in self.sprite_list]
  File "Z:\DOOM-style-Game\object_handler.py", line 76, in <listcomp>
    [sprite.update() for sprite in self.sprite_list]
  File "Z:\DOOM-style-Game\sprite_object.py", line 67, in update
    super().update()
  File "Z:\DOOM-style-Game\sprite_object.py", line 53, in update
    self.get_sprite()
  File "Z:\DOOM-style-Game\sprite_object.py", line 50, in get_sprite
    self.get_sprite_projection()
  File "Z:\DOOM-style-Game\sprite_object.py", line 26, in get_sprite_projection
    image = pg.transform.scale(self.image, (proj_width, proj_height))
TypeError: integer argument expected, got float
```

![doom](/sreenshots/0.jpg)
