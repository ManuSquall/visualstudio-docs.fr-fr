---
title: Utilisation de plusieurs langages spécifiques à un domaine dans une solution
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d9e4ae8239994a7524cdd1da0b3cfe05ea42d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808182"
---
# <a name="multiple-dsls-in-one-solution"></a>Utilisation de plusieurs langages spécifiques à un domaine dans une solution

Vous pouvez empaqueter plusieurs DSL comme partie intégrante d'une seule solution de telle sorte qu'ils soient installés ensemble.

Il existe différentes techniques pour intégrer plusieurs DSL. Pour plus d’informations, consultez [l’intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) et [Comment : Ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) et [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Créer plusieurs DSL dans la même solution

1. Créer un nouveau **projet VSIX** projet.

2. Créez deux ou plusieurs projets DSL dans le répertoire de solution VSIX.

   - Pour chaque DSL, ouvrez une nouvelle instance de Visual Studio. Créez le DSL et spécifiez le même dossier de solution que la solution VSIX.

   - Assurez-vous que vous créez chaque DSL avec une extension de nom de fichier différente.

   - Modifier les noms de la **Dsl** et **DslPackage** projets afin qu’ils soient tous différents. Par exemple : `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - Dans chaque **DslPackage\*\source.extension.tt**, mettre à jour de cette ligne vers le nom du projet Dsl correct :

      `string dslProjectName = "Dsl2";`

   - Dans la solution VSIX, ajoutez les Dsl * et DslPackage\* projets. Il se peut que vous souhaitiez placer chaque paire dans son propre dossier de solution.

2. Regroupez les manifestes VSIX des DSL :

   1. Ouvrez _YourVsixProject_**\source.extension.manifest**.

   2. Pour chaque DSL, choisissez **ajouter du contenu** et ajoutez :

       - `Dsl*` projet comme un **composant MEF**

       - `DslPackage*` projet comme un **composant MEF**

       - `DslPackage*` projet comme un **Package VS**

3. Générez la solution.

   Le VSIX résultant installera les deux DSL. Vous pouvez les tester en utilisant F5 ou déployer _YourVsixProject_**\bin\Debug\\\*.vsix**.

## <a name="see-also"></a>Voir aussi

- [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Guide pratique pour ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personnalisation du comportement de la copie](../modeling/customizing-copy-behavior.md)