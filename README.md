# rM-templates
Templates for reMarkable tablet.  
Suppose our template is Kanban_fr.png.  
Put your terminal in working directory were is the template 'Kanban_fr.png'.  

# Templates preparation  
## convert and resize  
- ratio 3:4 i.e. 1404x1872 centered and filled with a white background    

```sh
magick Kanban_fr.jpg -resize 1404x1872 -background white -compose Copy -gravity center -extent 1404x1872 -unsharp 0x1 -quality 92 template.png; open Kanban_fr.png
open Kanban_fr.png  
```
## convert png en svg  
- no command line solution to convert png to svg
- open Inkscape  
1 - File / Document property (^+cmd+D) / page / Arch B  
2 - open template.png   
3 - save as template.svg   

# Templates export and configuration  
## copy files from mac to rM  
```sh
scp Kanban_fr.png root@192.168.1.20:/usr/share/remarkable/templates/Kanban_fr.png  
scp Kanban_fr.svg root@192.168.1.20:/usr/share/remarkable/templates/Kanban_fr.svg  
```

## update of configuration file '.json'  
- for organisational template use icons "\ue9dc" "\ue9da" "\ue9db"

- ouvrir le fichier .json sur la rM  
```sh
ssh root@192.168.1.20 
ssh root@10.11.99.1 
nano /usr/share/remarkable/templates/templates.json
```
- ajouter à la fin du fichier config (juste avant '] }' ) le texte suivant en adaptant le non de fichier
- ne pas donner le même "name" pour deux templates différents
- ne pas oublier la virgule entre bloques successifs
- une même icône peut être utilisée pour plusieurs templates
,
    {
      "name": "Kanban 4",
      "filename": "Kanban_fr",
      "iconCode": "\ue9db",
      "categories": [
        "Perso"
      ]
    }
- save and close  
^O ^X
- reboot rM
