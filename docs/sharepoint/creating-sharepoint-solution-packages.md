---
title: Création de packages de solution SharePoint | Microsoft Docs
description: Créez et personnalisez des packages de déploiement pour les solutions SharePoint à l’aide du concepteur de packages. Explorez les outils d’empaquetage, les options du concepteur et la structure des dossiers.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bbe458f6ab4de01ffb224ae4e493bf23e3fc6ceb
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850557"
---
# <a name="create-sharepoint-solution-packages"></a>Créer des packages de solution SharePoint
  À l’aide du concepteur de packages, vous pouvez créer et personnaliser des packages de déploiement. Par exemple, vous pouvez ajouter des fonctionnalités et des éléments de projet SharePoint, réinitialiser le serveur IIS, définir des étendues d’activation de fonctionnalité et identifier les dépendances de fonctionnalités. Le concepteur génère également un manifeste, un fichier XML qui décrit chaque package.

## <a name="packaging-tools"></a>Outils d’empaquetage
 Vous pouvez utiliser le **Concepteur de packages** pour personnaliser le package et générer le manifeste. Vous pouvez inclure des éléments de projet SharePoint, configurer si le serveur Web doit être réinitialisé et définir le type de serveur de déploiement. Pour plus d’informations, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Vous pouvez également utiliser l' **Explorateur** de package pour modifier les fonctionnalités et les éléments de votre fichier de package (*. wsp*). Pour plus d’informations, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide de l’Explorateur](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)de package.

 Vous pouvez utiliser Visual Studio et MSBuild pour créer des fichiers de package (*. wsp*) afin de déployer votre solution SharePoint. Ce processus génère les fichiers manifeste nécessaires au déploiement de SharePoint. Pour plus d’informations, consultez [Comment : créer un package de solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Options du concepteur de packages
 Le tableau suivant répertorie les propriétés que vous pouvez personnaliser dans les packages SharePoint à l’aide du **Concepteur** de packages.

|Propriété du concepteur de packages|Description du paramètre par défaut|
|-------------------------------|------------------------------------|
|Nom|Obligatoire. Le nom par défaut du package est défini sur *ProjectName*.|
|Réinitialiser le serveur|facultatif. Sélectionnez cette option si vous souhaitez redémarrer le serveur Web après l’installation du fichier *. wsp* sur le serveur SharePoint.|
|Type de serveur de déploiement|facultatif. Représente le type de serveur qui héberge le package. Si ce paramètre n’est pas défini, la valeur par défaut est WebFrontEnd.<br /><br /> ApplicationServer : décrit un serveur qui héberge des services.<br /><br /> WebFrontEnd : décrit un serveur qui héberge des sites Web.|
|Éléments de la solution|Tous les éléments et fonctionnalités de projet SharePoint qui peuvent être ajoutés au package.|
|Éléments du package|facultatif. Tous les éléments et fonctionnalités SharePoint que vous souhaitez déployer dans votre package.|

## <a name="configure-the-packaging-process"></a>Configurer le processus d’empaquetage
 Après avoir développé des solutions SharePoint dans Visual Studio, vous pouvez personnaliser la façon dont les projets sont empaquetés.

 Le tableau suivant présente les deux cibles MSBuild que vous pouvez utiliser pour personnaliser la façon dont le fichier *. wsp* est créé.

|Cible|Description|
|------------|-----------------|
|BeforeLayout|Cible qui effectue des tâches immédiatement avant que les fichiers ne soient copiés dans un répertoire intermédiaire. Vous pouvez modifier les fichiers avant de créer un fichier de package (*. wsp*).|
|AfterLayout|Cible qui effectue des tâches immédiatement après que les fichiers ont été copiés dans un répertoire intermédiaire.|

 Pour plus d’informations, [Comment : personnaliser un package de solution SharePoint à l’aide de cibles MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Architecture d’empaquetage
 Les étapes suivantes se produisent lorsque vous créez un package SharePoint (*. wsp*) dans Visual Studio.

1. Les fonctionnalités et les packages sont validés pour s’assurer que la structure physique et sémantique du package est correcte.

2. Les fonctionnalités, les éléments de projet et les fichiers de package du package sont énumérés. Les fichiers manifeste pour les packages et les fonctionnalités sont transformés pour inclure toutes les informations nécessaires au déploiement et à l’activation. Les jetons sont remplacés par la valeur qualifiée complète.

3. La cible BeforeLayout MSBuild personnalisable est exécutée. Vous pouvez créer cette étape pour apporter des modifications personnalisées au package avant la création du fichier *. wsp* .

4. Les fichiers énumérés sont copiés dans un répertoire intermédiaire.

5. La cible de MSBuild AfterLayout personnalisable est exécutée. Vous pouvez créer cette étape pour apporter des modifications personnalisées au package avant la création du fichier *. wsp* .

6. Les fichiers du répertoire intermédiaire sont ajoutés au fichier *. wsp* .

## <a name="package-folder-structure"></a>Structure de dossiers de package
 Lorsque vous créez un package pour votre projet SharePoint, un fichier *. wsp* est créé pour vous dans le dossier *SolutionFolder\bin \\ \<BuildConfiguration>* Par exemple, si votre solution se trouve dans *C:\Visual Studio 2013 \ Projects\ListDefinition1* et que votre configuration de build est définie sur Release, le fichier *. wsp* se trouve dans *C:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Voir aussi
- [Comment : personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Comment : créer un package de solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Comment : créer un package de solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Comment : personnaliser un package de solution SharePoint à l’aide de cibles MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
