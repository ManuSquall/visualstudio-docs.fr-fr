---
title: Exporter et enregistrer des cartes de code
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: abfe8d6160d023a99e9a49480baada9acb0c8243
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="share-code-maps"></a>Partager des cartes de code

Vous pouvez enregistrer des cartes de code en tant que partie d’un projet Visual Studio, en tant qu’image ou en tant que fichier XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Partager une carte de code avec d’autres utilisateurs de Visual Studio

Utilisez le menu **Fichier** pour enregistrer la carte.

- ou -

Pour enregistrer la carte en tant que partie d’un projet spécifique, sur la barre d’outils de la carte, choisissez **partage** > **déplacer \<CodeMapName > .dgml vers**, puis choisissez le projet où vous souhaitez enregistrer le carte.

![Déplacer une carte dans un autre projet](../modeling/media/codemapsmovemapmenu.png)

Visual Studio enregistre la carte en tant qu’un *.dgml* fichier que vous pouvez partager avec d’autres utilisateurs de Visual Studio Enterprise et Visual Studio Professional.

> [!NOTE]
> Avant de partager une carte avec les utilisateurs de Visual Studio Professional, veillez à développer tous les groupes, à afficher les nœuds masqués et les liens entre les groupes, et à récupérer les nœuds supprimés que vous souhaitez afficher sur la carte. Sinon, les utilisateurs ne pourront pas afficher ces éléments.
>
> L’erreur suivante peut se produire quand vous enregistrez une carte se trouvant dans un projet de modélisation ou ayant été copiée à partir d’un projet de modélisation vers un autre emplacement :
>
> « Impossible d’enregistrer *fileName* en dehors du répertoire du projet. Les éléments liés ne sont pas pris en charge. »
>
> Visual Studio affiche l’erreur, mais crée quand même la version enregistrée. Pour éviter cette erreur, créez la carte en dehors du projet de modélisation. Vous pouvez ensuite l’enregistrer à l’emplacement que vous souhaitez. Le fait de copier le fichier vers un autre emplacement de la solution, puis de tenter de l’enregistrer, ne fonctionnera pas.

## <a name="export-a-code-map-as-an-image"></a>Exporter une carte de code en tant qu’image

Lorsque vous exportez une carte de code en tant qu’image, vous pouvez le copier dans d’autres applications, telles que Microsoft Word ou PowerPoint.

1. Dans la barre d’outils de la carte de code, choisissez **partage** > **par courrier électronique en tant qu’Image** ou **copier l’Image**.

2. Collez l’image dans une autre application.

## <a name="export-the-map-as-an-xps-file"></a>Exporter la carte en tant que fichier XPS

Lorsque vous exportez une carte de code en tant que fichier XPS, vous pouvez le voir dans des visionneuses XML ou XAML comme Internet Explorer.

1. Dans la barre d’outils de la carte de code, choisissez **partage** > **par courrier électronique en tant que XPS Portable** ou **enregistrer en tant que XPS Portable**.

2. Accédez à l’emplacement auquel enregistrer le fichier.

3. Nommez la carte de code. Assurez-vous que le **enregistrer en tant que type** zone est définie sur **fichiers XPS (\*.xps)**. Choisissez **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Mapper les dépendances avec des cartes de code](../modeling/map-dependencies-across-your-solutions.md)