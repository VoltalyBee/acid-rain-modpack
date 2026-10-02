# Acid Rain

## Mise à jour 1.0.3 : retrait de Sleep Deprived

**Sleep Deprived 1.1.2** et sa configuration ont été retirés à la demande de l’administratrice, à la suite de problèmes signalés chez certains joueurs. Les instances suivies par packwiz suppriment automatiquement le JAR à leur prochain lancement. Les joueurs gardent leur instance Prism et le ZIP actuel reste utilisable pour les nouvelles installations.

Pour désactiver aussi le mod sur le serveur, arrête-le chez ton hébergeur, retire `mods/sleep_deprived-1.1.2-forge-1.20.1.jar`, puis redémarre-le. La publication GitHub ne modifie pas les fichiers de l’hébergeur.

## Ajout 1.0.2 : Corpse x Curios API Compat

Ajout de **Corpse x Curios API Compat 3.1.3** et **BaguetteLib 1.1.6**, tous deux marqués comme fichiers de serveur. Les joueurs gardent leur instance Prism actuelle et n’ont aucun téléchargement individuel à effectuer pour cet ajout.

L’activation demande d’installer les deux JAR chez l’hébergeur, puis de redémarrer le serveur. Les étapes figurent dans [AJOUT_CURIOS_CORPSE_SERVEUR.md](AJOUT_CURIOS_CORPSE_SERVEUR.md). Les 83 références de contenu de l’instance des joueurs et leurs versions sont conservées.

## Correction 1.0.1 : installation sans téléchargement individuel

Easy NPC Bundle 7.12.1 utilise maintenant le Modrinth officiel de son auteur. Le code et les ressources sont identiques au fichier de l’export ; seul l’horodatage du manifeste change.

Le ZIP Prism fourni contient les deux fichiers originaux qui provoquaient la fenêtre de téléchargement manuel : Advanced Stands et Easy NPC Bundle. Il permet d’installer le pack actuel sans récupérer ces deux fichiers à la main. Après publication de 1.0.1, Easy NPC Bundle sera remplacé automatiquement par son équivalent Modrinth.

Advanced Stands est épinglé à sa version actuelle pour éviter qu’une mise à jour générale n’introduise une nouvelle demande manuelle. Sa page CurseForge indique « All Rights Reserved », alors que les métadonnées du JAR indiquent « Apache 2.0 ». Cette divergence doit être clarifiée avec l’auteur avant de réhéberger publiquement ce mod ou ses futures versions.

Pour rendre aussi ses futures mises à jour automatiques, l’auteur peut autoriser les téléchargements tiers sur CurseForge, publier une source alternative autorisée, ou accorder une permission de réhébergement. Inclure le fichier actuel dans le ZIP initial ne distribue pas ses futures versions aux instances déjà installées.

Les fichiers de `docs` conservent leurs octets lors des commits Git ; les empreintes de l’index sont recalculées pour la copie publiée, y compris les configurations converties en fins de ligne LF par GitHub Desktop.

Pack destiné aux joueurs du serveur Acid Rain de VoltalyBee.

- Minecraft : **1.20.1**
- Forge : **47.4.23**
- Version initiale du pack : **1.0.0**
- Contenu actuel : **77 fichiers de mods pour les joueurs, 2 ajouts pour le serveur, 4 shaders et 1 pack de ressources**

Les références correspondent aux fichiers exacts de l’export Prism fourni le 2 octobre 2026. Les mods et shaders se téléchargent depuis Modrinth ou CurseForge. Le dépôt contient leurs références, les empreintes de contrôle et les configurations du pack.

Consulte [INVENTAIRE.md](INVENTAIRE.md) pour la liste complète et les liens de chaque version. Le dossier `docs` contient le pack destiné à GitHub Pages. `INVENTAIRE.json` conserve l’inventaire actuel détaillé ; il faut le mettre à jour lors d’une évolution du contenu.

## Publier le pack

Le dépôt est [https://github.com/VoltalyBee/acid-rain-modpack](https://github.com/VoltalyBee/acid-rain-modpack). Le dossier `docs` est destiné à GitHub Pages : **Settings → Pages → Deploy from a branch → main → /docs → Save**.

Après publication, le manifeste est accessible ici :

```text
https://voltalybee.github.io/acid-rain-modpack/pack.toml
```

Cette adresse doit afficher le contenu du fichier `pack.toml` avant de distribuer l’instance Prism aux joueurs.

## Relier Prism

Place `packwiz-installer-bootstrap.jar` dans le dossier Minecraft de l’instance. Dans **Modifier l’instance → Paramètres → Commandes personnalisées**, active les commandes propres à l’instance et ajoute cette commande avant lancement :

```text
"$INST_JAVA" -jar "$INST_MC_DIR/packwiz-installer-bootstrap.jar" --pack-folder "$INST_MC_DIR" -s client https://voltalybee.github.io/acid-rain-modpack/pack.toml
```

Un premier lancement associe les fichiers de cette instance au pack. Les lancements suivants appliquent les changements publiés. Un téléchargement manuel peut être demandé par l’installateur lorsqu’un auteur limite les téléchargements via les applications tierces ; il faut suivre sa fenêtre de téléchargement.

Les préférences graphiques identifiées et les réglages des shaders sont marqués `preserve = true` : leurs modifications locales sont conservées. Les configurations communes du pack suivent les versions publiées. Les options générales de Minecraft et l’historique des joueurs sont gérés par leur instance.

## Préparer une mise à jour

Installe l’outil [packwiz](https://packwiz.infra.link/installation/) sur ton PC. Sur Windows, télécharge l’archive Windows depuis le lien indiqué dans cette documentation, puis place `packwiz.exe` à la racine de ton dépôt local, à côté de ce README. L’exécutable est exclu de Git.

Ouvre un terminal dans le dossier `docs`. Ces exemples supposent que `packwiz.exe` se trouve dans son dossier parent :

```powershell
..\packwiz.exe list
..\packwiz.exe update mods/open-parties-and-claims.pw.toml
..\packwiz.exe refresh
```

Pour choisir une version précise de CurseForge ou Modrinth, utilise son lien de version :

```powershell
..\packwiz.exe curseforge install LIEN_DE_LA_VERSION_CURSEFORGE
..\packwiz.exe modrinth install LIEN_DE_LA_VERSION_MODRINTH
```

Les mots `LIEN_DE_LA_VERSION_...` sont des valeurs à remplacer. Pour supprimer un mod :

```powershell
..\packwiz.exe remove mods/NOM_DU_MOD.pw.toml
```

Les shaders sont référencés dans `shaderpacks`, avec `side = "client"`. Leur commande de mise à jour utilise le chemin de leur fiche, par exemple :

```powershell
..\packwiz.exe update shaderpacks/complementary-reimagined.pw.toml
```

Choisis les versions qui doivent fonctionner avec ton serveur, puis teste-les sur une copie de ton instance. Ajuste la version `version = "1.0.0"` dans `pack.toml`, mets à jour l’inventaire, exécute `refresh`, et publie les changements avec **Commit to main → Push origin** dans GitHub Desktop. La publication Pages doit être terminée avant d’annoncer la mise à jour aux joueurs. Les changements nécessaires sur le serveur Minecraft se font dans le panneau de l’hébergeur.

Pour obtenir une liste Markdown depuis les fiches courantes :

```powershell
..\packwiz.exe utils markdown
```

Le guide détaillé fourni avec le kit explique la création du dépôt et l’installation dans Prism.

## Documentation officielle

- [Packwiz et l’installateur](https://packwiz.infra.link/tutorials/installing/packwiz-installer/)
- [Ajouter et modifier des fichiers](https://packwiz.infra.link/tutorials/creating/adding-mods/)
- [Commandes personnalisées de Prism](https://prismlauncher.org/wiki/help-pages/custom-commands/)
- [Publier un dossier avec GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
