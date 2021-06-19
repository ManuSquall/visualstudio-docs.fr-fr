---
title: Exporter et enregistrer des cartes de code
description: Découvrez comment enregistrer des cartes de code dans le cadre d’un projet Visual Studio, sous la forme d’une image ou d’un fichier XPS.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e58e06c48ed9fa3a9d459c6c615abae4d4b4823f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385680"
---
# <a name="share-code-maps"></a>Partager des cartes de code

Vous pouvez enregistrer des cartes de code dans le cadre d’un projet Visual Studio, sous la forme d’une image ou d’un fichier XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Partager une carte de code avec d’autres utilisateurs de Visual Studio

Utilisez le menu **Fichier** pour enregistrer la carte.

-ou-

Pour enregistrer la carte dans le cadre d’un projet spécifique, dans la barre d’outils de la carte, choisissez **partager**  >  **déplacer Move \<CodeMapName> . dgml dans**, puis choisissez le projet dans lequel vous souhaitez enregistrer la carte.

![Déplacer une carte dans un autre projet](../modeling/media/codemapsmovemapmenu.png)

Visual Studio enregistre la carte en tant que fichier *. dgml* que vous pouvez partager avec d’autres utilisateurs de Visual Studio Enterprise et Visual Studio Professional.

> [!NOTE]
> Avant de partager une carte avec les utilisateurs de Visual Studio Professional, veillez à développer tous les groupes, à afficher les nœuds masqués et les liens entre les groupes, et à récupérer les nœuds supprimés que vous souhaitez afficher sur la carte. Sinon, les utilisateurs ne pourront pas afficher ces éléments.
>
> L’erreur suivante peut se produire quand vous enregistrez une carte se trouvant dans un projet de modélisation ou ayant été copiée à partir d’un projet de modélisation vers un autre emplacement :
>
> « Impossible d’enregistrer *fileName* en dehors du répertoire du projet. Les éléments liés ne sont pas pris en charge. »
>
> Visual Studio affiche l’erreur, mais crée quand même la version enregistrée. Pour éviter cette erreur, créez la carte en dehors du projet de modélisation. Vous pouvez ensuite l’enregistrer à l’emplacement que vous souhaitez. Le fait de copier le fichier vers un autre emplacement de la solution, puis de tenter de l’enregistrer, ne fonctionnera pas.

## <a name="export-a-code-map-as-an-image"></a>Exporter une carte de code en tant qu’image

Lorsque vous exportez une carte de code en tant qu’image, vous pouvez la copier dans d’autres applications, telles que Microsoft Word ou PowerPoint.

1. Dans la barre d’outils de la carte de code, choisissez **partager** l'  >  **e-mail en tant qu’image** ou **copier l’image**.

2. Collez l’image dans une autre application.

## <a name="export-the-map-as-an-xps-file"></a>Exporter la carte en tant que fichier XPS

Lorsque vous exportez une carte de code sous la forme d’un fichier XPS, vous pouvez la voir dans des visionneuses XML ou XAML comme Internet Explorer.

1. Dans la barre d’outils de la carte de code, choisissez **partager** des  >  **e-mails comme portable XPS** ou **Enregistrer comme portable XPS**.

2. Accédez à l’emplacement auquel enregistrer le fichier.

3. Nommez la carte de code. Assurez-vous que la zone **type** de fichier est définie sur **fichiers XPS ( \* . Xps)**. Choisissez **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Mapper des dépendances avec des cartes de code](../modeling/map-dependencies-across-your-solutions.md)
