# Ajouter Corpse x Curios API Compat au serveur Acid Rain

Minecraft **1.20.1**, Forge **47.4.23**, références du pack **1.0.2**.

Les versions retenues sont **Corpse x Curios API Compat 3.1.3** et **BaguetteLib 1.1.6**. Elles proviennent du Modrinth officiel, avec leurs empreintes vérifiées. BaguetteLib 1.1.6 conserve la génération 1.x de la bibliothèque utilisée par cette version stable de l’extension.

## Installation chez l’hébergeur

1. Arrête le serveur depuis le panneau de ton hébergeur.
2. Extrais **Acid_Rain_Curios_Corpse_Serveur.zip** sur ton PC.
3. Envoie les **deux fichiers JAR du dossier `mods`** dans le dossier `mods` de ton serveur :
   - `corpsecurioscompat-1.20.1-Forge-3.1.3.jar`
   - `baguettelib-1.20.1-Forge-1.1.6.jar`
4. Si une autre version de BaguetteLib est déjà installée, conserve un seul JAR pour ce mod. Vérifie aussi la présence de **Corpse** et **Curios API** sur le serveur ; leurs versions inventoriées dans Acid Rain sont `1.20.1-1.0.23` et `5.14.1+1.20.1`.
5. Redémarre le serveur et vérifie qu’il termine son démarrage.
6. Teste la récupération d’un accessoire Curios depuis un corps avec un objet de peu de valeur.

L’archive est un petit ajout au serveur. Elle ne contient pas l’ensemble du serveur ni les autres mods.

## Joueurs

Les deux projets sont annoncés par leur auteur comme mods de serveur. Ils sont donc référencés avec `side = "server"` dans packwiz. Les joueurs utilisent leur instance Prism actuelle ; ils n’ont pas à réimporter le ZIP, à chercher un JAR ni à installer ces deux mods.

La publication sur GitHub décrit le pack. Elle ne copie pas les fichiers chez ton hébergeur : l’installation dans son panneau reste à faire pour activer cette fonctionnalité sur le serveur.

## Sources officielles

- Corpse x Curios API Compat 3.1.3 : https://modrinth.com/mod/corpse-x-curios-api-compat/version/zgt34xjo
- BaguetteLib 1.1.6 : https://modrinth.com/mod/baguettelib/version/vLbvKK04

Les deux projets et les métadonnées de leurs JAR indiquent la licence MIT. Les JAR sont conservés sans modification.
