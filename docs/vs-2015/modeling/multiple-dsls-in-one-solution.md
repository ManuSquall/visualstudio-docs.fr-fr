---
title: Plusieurs DSL dans une solution | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668554"
---
# <a name="multiple-dsls-in-one-solution"></a>Utilisation de plusieurs langages spécifiques à un domaine dans une solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez empaqueter plusieurs DSL comme partie intégrante d'une seule solution de telle sorte qu'ils soient installés ensemble.

 Il existe différentes techniques pour intégrer plusieurs DSL. Pour plus d’informations, consultez [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) et [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) et [Personnalisation du comportement](../modeling/customizing-copy-behavior.md)de la copie.

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Pour créer plusieurs DSL dans la même solution

1. Créez au moins deux solutions DSL, ainsi qu'un projet VSIX, et ajoutez tous les projets à une solution unique.

   - Pour créer un projet VSIX : dans la boîte de dialogue **nouveau projet** , **sélectionnez C#visuel** , **extensibilité**, **projet VSIX**.

   - Créez au moins deux solutions DSL dans le répertoire de solutions VSIX.

        Pour chaque DSL, ouvrez une nouvelle instance de Visual Studio. Créez le DSL et spécifiez le même dossier de solution que la solution VSIX.

        Assurez-vous que vous créez chaque DSL avec une extension de nom de fichier différente.

   - Modifiez les noms des projets **DSL** et **DslPackage** afin qu’ils soient tous différents. Par exemple : `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - Dans chaque **DslPackage \* \ source.extension.TT**, mettez à jour cette ligne avec le nom de projet DSL correct :

        `string dslProjectName = "Dsl2";`

   - Dans la solution VSIX, ajoutez les projets \* DSL * et DslPackage.

        Il se peut que vous souhaitiez placer chaque paire dans son propre dossier de solution.

2. Regroupez les manifestes VSIX des DSL :

   1. Ouvrez _YourVsixProject_ **\Source.extension.manifest**.

   2. Pour chaque DSL, choisissez **Ajouter du contenu** et ajoutez :

       - `Dsl*` projet en tant que **Composant MEF**

       - `DslPackage*` projet en tant que **Composant MEF**

       - `DslPackage*` projet en tant que **package vs**

3. Générez la solution.

   Le VSIX résultant installera les deux DSL. Vous pouvez les tester à l’aide de la touche F5 ou déployer _YourVsixProject_ **\bin\Debug \\ \*. vsix**.

## <a name="see-also"></a>Voir aussi
 [Intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) [Personnalisation du comportement](../modeling/customizing-copy-behavior.md) de la copie
