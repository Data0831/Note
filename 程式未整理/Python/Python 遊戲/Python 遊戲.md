# Python pygame


## MainSurf
### create
`syntax: surface.obj = pg.display.set_mode(tuple:(width, height))`
**EXAMPLE**
```python=
import pygame as pg
pg.init()# inital pygame
screen = pg.display.set_mode((500, 600))
```
### main screen update
`syntax: None = pg.display.update()`
**EXAMPLE**
```python=
while 1:
    pg.display.update()
```
### set caption, icon
**EXAMPLE**
```python=
pg.display.set_caption("Space War")
pg.display.set_icon(Surface )
```

### blit
**EXAMPLE**
```python=
screen.blit(surface, surface.rect)
```
***
## Event 
### quit

`syntax: event.list = pg.event.get()`
**EXAMPLE**
```python=
running = True
while running:
    for event in pg.event.get():
        if event.type == pg.QUIT:
            running = False

pg.quit()
```

### keydown
`syntax: event.list.type`
**EXAMPLE**
```python=
for event in pg.event.get():
    if event.type == pg.KEYDOWN:
        if event.key == pg.K_SPACE:
            pass # do something
```
### mousedown, get pos
`syntax: eventype == pg.MOUSEBUTTONDOWN`
**EXAMPLE**
```python=
if eventype == pg.MOUSEBUTTONDOWN:
	x,y = pg.mouse.get_pos()
```
[精確座標移動](/WQ7ElPijRKG7K1zmajdGIQ?view#pygame-座標精確移動)
***
## Time
### clock.obj
`syntax: clock.obj = pg.time.Clock()`
`clock.obg.tick(int)`

**EXAMPLE**
```python=
clock = pg.time.Clock()#create clock obj
while(1)
    clock.tick(60)# max active 60 times per second
```

### get time
**EXAMPLE**
```python=
now = pg.time.get_ticks()
# return int(ms)
```
***
## Surf
### create, fill
`syntax: None = surface.fill(tuple:(color))`

**EXAMPLE**
```python=
new_surface = pg.Surface((50,40))#size(width, heigh)
new_surface.fill((255,0,0))# color(R,G,B)
```
### surf rect
**EXAMPLE**
```python=
surface.rect = surface.rect.get_rect()
```
### surface transform scale, set colorkey
**EXAMPLE**
```python=
new_surf = pg.transform.scale(old_surf, (50,40)) #old, size
new_surf.set_colorkey((0,0,0)) # color
```

### rotate, copy
**EXAMPLE**
```python=
new_surf = pg.transform.rotate(surf, 3) #old, rotate_degree
```
```python=
surf = surf_ori.copy()
```

***
## sprite
### sprite paremeter delete
**EXAMPLE**
```python=
class Player(pg.sprite.Sprite):
    def __init__(self):
        pg.sprite.Sprite.__init__(self)
        self.image = pg.Surface((50,40))
        self.rect = self.image.get_rect()# sprite 有rect參數
        self.rect.x = 200
    def update(self):
        if die:
            self.kill()#delete self or player.kill()
```
|sprite data|type|
|-----------|---|
|self.image|surf|
|self.rect|rect|
|self.alive|bool|

|rect position| | |
|-|-|-|
|x,y|top|topright|
|left|center|right|
|bottomleft|bottom|bottomright|

### sprite group update draw
**EXAMPLE**
```python=
all_sprite = pg.sprite.Group()
all_sprite.add(player)# sprite.obj

all_sprite.update()

all_sprite.draw(screen)# surf
```
### sprite collide
**EXAMPLE**
```python=
hits = pg.sprite.Groupcollide(rocks, bullets, True, True)
# 消失物件 = pg.sprite.Groupcollide(sp.group, sp.group, 是否刪除, 是否刪除)
# list([[rock, bullet], [rock, bullet]])
hits = pg.sprite.spritecollide(player, bullets, True)
```

### circle collide
**EXAMPLE**
```python=
hits = pg.sprite.spritecollide(player, bullets, Truepg.sprite.collide_circle)
```

```python=
class Player(pg.sprite.Sprite):
    def __init__(self):
        pg.sprite.Sprite.__init__(self)
        self.radius = 5
```

***
## Key
**EXAMPLE**
```python=
key_pressed = pg.key_get_pressed()
# 回傳list，list裡存著一串bool，代表鍵盤有沒有被按著
if key_pressed[pg.K_RIGHT]:# pg.K_RIGHT->int
    pass# do something
if key_pressed[pg.K_a]:# pg.K_RIGHT->int
    pass# do something
```
***
## Image
### load image, blit in screen
`syntax: surf.obj = pg.image.load(path).convert()`
**EXAMPLE**
```python=
background_img = pg.image.load("D:\img\img.png").convert()
screen.blit(background_img)# surface
```

### image transform scale, set colorkey
**EXAMPLE**
```python=
new_img = pg.transform.scale(old_img, (50,40)) #old, size
new_img.set_colorkey((0,0,0)) # color
```
### rotate, copy
**EXAMPLE**
```python=
new_surf = pg.transform.rotate(surf, 3) #old, rotate_degree
```
連續轉動會失真->讓他只轉一次->記住每次轉的角度
轉動中心點會變->記住舊平面中心->複製到轉動後
```python=
degree += 3
surf_ori = surf
surf = surf_ori.copy()

center = self.rect.center
surf = pg.transform.rotate(surf_ori, degree)
serf.rect = self.image.get_rect()
self.rect.center = center
```
***
## Draw
### draw color on surface
**EXAMPLE**
```python=
pg.draw.circle(self.image, RED, self.rect.center, self.radius)
```
### draw rect.obj
**EXAMPLE**
```python=
outline_rect = pg.Rect(x, y, wid, hei)
fill_rect = pg.Rect(x, y, wid, hei)
pg.draw.rect(surf, GREEN, fill_rect)
pg.draw.rect(surf, WHITE, outline_rect, 2)
# surf, color, rect, bor-wid
```
***
## Font
### font, font to surface blit
**EXAMPLE**
```python=
font_path = pg.font.match_font("arial")# 尋找font路徑
# return str
font = pg.font.Font(font_path, size)# 創建font.obj
# size = font-size
text_surface = font.render(text, True, WHITE)
# text = string, 抗拒齒, color
text_rect = text_surface.get_rect()
text_rect.centerx = x
text_rect.top = y
surf.blit(text_surface, text_rect)
```

***

## Music
### Sound
**EXAMPLE**
```python=
pg.mixer.init()
music = pg.mixer.Sound("path")
# return Sound.obj
music.set_volumn(0.5)
music.play(-1)
# times
```
### music
**EXAMPLE**
```python=
pg.mixer.music.load("path")
#return None
pg.mixer.music.play(-1)
pg.mixer.music.set_volumn(0.5)
# times
```

# 注意事項
x.y不能用浮點數，會強制轉乘整數
