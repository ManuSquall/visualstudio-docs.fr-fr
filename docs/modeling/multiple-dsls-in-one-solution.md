---
title: Utilisation de plusieurs langages spécifiques à un domaine dans une solution
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5d21d3954a402e7ce8eb26c34d6a6a5c237309a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658346"
---
# <a name="multiple-dsls-in-one-solution"></a>Utilisation de plusieurs langages spécifiques à un domaine dans une solution

Vous pouvez empaqueter plusieurs DSL comme partie intégrante d'une seule solution de telle sorte qu'ils soient installés ensemble.

Il existe différentes techniques pour intégrer plusieurs DSL. Pour plus d’informations, consultez [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) et [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) et [Personnalisation du comportement](../modeling/customizing-copy-behavior.md)de la copie.

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Créer plusieurs DSL dans la même solution

1. Créez un projet de **projet VSIX** .

2. Créez deux projets DSL ou plus dans le répertoire de la solution VSIX.

   - Pour chaque DSL, ouvrez une nouvelle instance de Visual Studio. Créez le DSL et spécifiez le même dossier de solution que la solution VSIX.

   - Assurez-vous que vous créez chaque DSL avec une extension de nom de fichier différente.

   - Modifiez les noms des projets **DSL** et **DslPackage** afin qu’ils soient tous différents. Par exemple : `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - Dans chaque **DslPackage \* \ source.extension.TT**, mettez à jour cette ligne avec le nom de projet DSL correct :

      `string dslProjectName = "Dsl2";`

   - Dans la solution VSIX, ajoutez les projets \* DSL * et DslPackage. Il se peut que vous souhaitiez placer chaque paire dans son propre dossier de solution.

2. Regroupez les manifestes VSIX des DSL :

   1. Ouvrez _YourVsixProject_ **\Source.extension.manifest**.

   2. Pour chaque DSL, choisissez **Ajouter du contenu** et ajoutez :

       - `Dsl*` projet en tant que **Composant MEF**

       - `DslPackage*` projet en tant que **Composant MEF**

       - `DslPackage*` projet en tant que **package vs**

3. Générez la solution.

   Le VSIX résultant installera les deux DSL. Vous pouvez les tester à l’aide de la touche F5 ou déployer _YourVsixProject_ **\bin\Debug \\ \*. vsix**.

## <a name="see-also"></a>Voir aussi

- [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Guide pratique pour ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personnalisation du comportement de la copie](../modeling/customizing-copy-behavior.md)