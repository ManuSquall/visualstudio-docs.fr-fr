---
title: Visualisation des données avec R
description: Guide pratique pour tracer des données à partir de programmes R dans Visual Studio, à l’aide de fenêtres de traçage.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 64b5ac36edf6c5f506628f9af88ba36bd62c71c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851827"
---
# <a name="create-visual-data-plots-with-r"></a>Créer des tracés de données visuels avec R

Le traçage est une partie essentielle du flux de travail d’un scientifique des données. Dans les Outils R pour Visual Studio (RTVS), toutes les activités de traçage sont centrées sur une ou plusieurs fenêtres de traçage, qui sont conçues pour améliorer votre productivité avec cette activité.

![Image de traçage](media/plotting-hero-image.png)

:::row:::
    :::column:::
        ![Icône représentant une caméra pour les vidéos](../install/media/video-icon.png "Regarder une vidéo")
    :::column-end:::
    :::column:::
        [Regardez une vidéo (youtube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) sur le traçage avec R (2 min 2 s).
    :::column-end:::
:::row-end:::

## <a name="the-plot-window"></a>La fenêtre de tracés

Une fenêtre de tracés contient une série de tracés, où chaque tracé est généré par une commande `plot`. Par exemple, si vous utilisez `plot(1:100)`, une nouvelle fenêtre de tracés est créée si aucune n’est disponible actuellement :

![Tracé linéaire de 1 à 100](media/plotting-1-to-100.png)

Techniquement parlant, les commandes `plot` R affichent leur sortie sur un périphérique d’affichage R. Une fenêtre de tracés restitue le contenu d’un périphérique graphique R, c’est pourquoi un numéro de périphérique est affecté à chaque fenêtre de tracés.

Les fenêtres de tracés sont indépendantes des projets Visual Studio et restent ouvertes quand vous chargez et fermez les projets.

La génération d’un tracé utilise la fenêtre de tracés « active » et enregistre tout tracé précédent dans l’historique de tracés (consultez [Historique de tracés](#plot-history)). Par exemple, entrez `plot(100:1)` et le premier tracé est remplacé par une ligne vers le bas.

Comme toutes les autres fenêtres de Visual Studio, la fenêtre de tracés prend en charge les dispositions personnalisées (voir [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)). Les fenêtres de tracés peuvent être ancrées à différents emplacements dans le cadre de Visual Studio, redimensionnées dans ce cadre ou extraites entièrement du cadre pour un redimensionnement indépendant.

Le redimensionnement d’une fenêtre de tracé provoque toujours le réaffichage du tracé, afin de fournir la meilleure qualité d’image. Vous voulez généralement redimensionner un tracé avant de l’exporter vers un fichier ou vers le Presse-papiers à l’aide des commandes décrites dans la section suivante.

## <a name="plot-window-commands"></a>Commandes de la fenêtre de tracés

La barre d’outils de la fenêtre de tracés contient les commandes applicables, dont la plupart sont également disponibles via le menu des  >  **tracés** d’outils R.

| Bouton | Commande | Description |
| --- | --- | --- |
| ![Bouton Nouvelle fenêtre de tracés](media/plotting-toolbar-01-new-plot-window.png) | Nouvelle fenêtre de tracés | Crée une fenêtre de tracés distincte avec son propre historique. Voir [Plusieurs fenêtres de tracés](#multiple-plot-windows). |
| ![Bouton Activer la fenêtre de tracés](media/plotting-toolbar-02-activate-plot-window.png) | Activer la fenêtre de tracés | Définit la fenêtre de tracés active comme fenêtre active, afin que les commandes `plot` ultérieures soient affichées dans cette fenêtre. Voir [Plusieurs fenêtres de tracés](#multiple-plot-windows). Voir [Plusieurs fenêtres de tracés](#multiple-plot-windows). |
| ![Bouton Fenêtre d’historique des tracés](media/plotting-toolbar-03-plot-history.png) | Fenêtre d’historique des tracés | Ouvre une fenêtre avec tous les tracés dans l’historique affichés sous forme de miniatures. Voir [Historique de tracés](#plot-history). |
| ![Boutons Historique des tracés](media/plotting-toolbar-04-plot-history-arrows.png) | Tracé précédent/suivant |  Accès au tracé précédent ou suivant dans l’historique. Vous pouvez également parcourir l’historique avec Ctrl+Alt+F11 (Précédent) et Ctrl+Alt+F12 (Suivant). Voir [Historique de tracés](#plot-history). |
| ![Bouton Enregistrer en tant qu’image](media/plotting-toolbar-05-save-as-image.png)| Enregistrer en tant qu’image | Invite à entrer un nom de fichier et enregistre le tracé actuel (le contenu de la fenêtre, à la taille de la fenêtre) dans un fichier image. Les formats disponibles sont `.png`, `.jpg`, `.bmp` et `.tif`. |
| ![Bouton Enregistrer au format PDF](media/plotting-toolbar-06-save-as-pdf.png)| Enregistrer au format PDF | Enregistre le tracé actuel dans un fichier PDF, à l’aide de la taille de fenêtre actuelle. Le tracé sera réaffiché si le fichier PDF est mis à l’échelle. |
| ![Bouton Copier en tant qu’image bitmap](media/plotting-toolbar-07-copy-as-bitmap.png)| Copier en tant qu’image bitmap | Copie le tracé dans le Presse-papiers sous forme de bitmap raster, à l’aide de la taille de fenêtre actuelle. |
| ![Bouton Copier en tant que métafichier](media/plotting-toolbar-08-copy-as-metafile.png)| Copier en tant que métafichier | Copie le tracé dans le Presse-papiers en tant que [métafichier Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). |
| ![Bouton Supprimer le tracé](media/plotting-toolbar-09-remove-plot.png)| Supprimer le tracé | Supprime le tracé actuel de l’historique. |
| ![Bouton Effacer tous les tracés](media/plotting-toolbar-10-clear-all-plots.png) | Effacer tous les tracés | Supprime tous les tracés de l’historique (affiche une invite de confirmation). |

## <a name="multiple-plot-windows"></a>Plusieurs fenêtres de tracés

Comme les scientifiques des données travaillent souvent avec de nombreux tracés provenant de différents datasets, RTVS vous permet de créer autant de fenêtres de tracés indépendantes que vous le souhaitez. Vous pouvez ensuite organiser ces fenêtres comme vous le souhaitez dans le cadre de Visual Studio ou en dehors de ce cadre. (Pour obtenir des informations générales sur l’ancrage et le redimensionnement des fenêtres, consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).)

Vous créez une nouvelle fenêtre de tracés à l’aide du **bouton de barre d’outils ou de** la  >    >  **fenêtre de tracés** tracés. La nouvelle fenêtre de tracés devient la fenêtre *active*, qui est l’emplacement où les nouveaux tracés sont affichés. Pour changer la fenêtre active, basculez vers elle et sélectionnez le bouton de barre d’outils **Activer la fenêtre de tracés** ou cliquez sur **Outils R** > **Tracés** > **Activer la fenêtre de tracés**.

Les tracés sont aussi des objets indépendants, ce qui signifie que vous pouvez les copier ou les déplacer entre les fenêtres de tracés à l’aide d’une opération de glisser-déplacer avec la souris, ou à l’aide des commandes **Copier**, **Couper** et **Coller** du menu contextuel et du menu **Edition**.

Le comportement par défaut pour le glisser-déplacer est copier ; pour déplacer, glisser-déplacer tout en appuyant sur la touche **MAJ** .

## <a name="plot-history"></a>Historique de tracés

Les commandes de tracés sont conservées dans l’historique de tracés pour chaque fenêtre. Ainsi, tout le traçage dans une session est conservé. Pour naviguer dans l’historique, utilisez les boutons fléchés de la barre d’outils de la fenêtre de tracés, ou **Appuyez sur CTRL** + **ALT** + **F11** et **CTRL** + **ALT** + **F12**. Vous pouvez également supprimer des tracés uniques ou effacer tous les tracés de la fenêtre à l’aide des boutons de la barre d’outils ou des commandes de menu des **Outils R**  >   .

Pour afficher l’intégralité de la collection de tracés, ouvrez la fenêtre historique des tracés à l’aide du bouton de barre d’outils ou de la  >    >  **fenêtre historique des tracés** des outils R.
L’historique vous donne une liste des miniatures pour les tracés qui ont été affichés dans cette fenêtre, regroupés par fenêtres de tracés (ou appareils). Les boutons de zoom dans la barre d’outils permettent de changer la taille des miniatures.

![Fenêtre d’historique des tracés](media/plotting-plot-history-window.png)

Pour ouvrir un tracé dans sa fenêtre associée, double-cliquez sur ce tracé, sélectionnez-le, puis sélectionnez le bouton **afficher le tracé** de la barre d’outils. Vous pouvez également cliquer avec le bouton droit sur le tracé et sélectionner **afficher le tracé**. Vous pouvez également sélectionner un tracé individuel et le copier, le couper ou le supprimer à partir du menu contextuel ou **Edit** .

La durée de vie de votre historique de tracés dans toutes les fenêtres est liée à la durée de vie de votre session R interactive. Si vous réinitialisez votre session R, ou si vous quittez et redémarrez Visual Studio, votre historique de tracés est réinitialisé.

## <a name="programmatically-manipulate-plot-windows"></a>Manipuler des fenêtres de tracés par programmation

Vous pouvez manipuler les fenêtres de tracés par programmation à partir de code R, en utilisant des numéros de périphériques pour identifier des fenêtres de tracés spécifiques.

- `dev.list()` : répertorie tous les périphériques d’affichage dans la session R active.
- `dev.new()` : crée un périphérique d’affichage (une nouvelle fenêtre de tracés).
- `dev.set(<device number>)` : définit le périphérique tracé actif.
- `dev.off()` : supprime le périphérique actif.
