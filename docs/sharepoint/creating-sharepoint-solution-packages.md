---
title: Création de Packages de Solution SharePoint | Microsoft Docs
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
ms.openlocfilehash: 8f7afee863d36796bb481f9aca2c24a9ba891ae7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952723"
---
# <a name="create-sharepoint-solution-packages"></a>Créer des packages de solution SharePoint
  À l’aide du Concepteur de packages, vous pouvez créer et personnaliser des packages de déploiement. Par exemple, vous pouvez ajouter des éléments de projet SharePoint et des fonctionnalités, réinitialiser le serveur IIS, définir des étendues de l’activation de fonctionnalité et identifier les dépendances de fonctionnalité. Le concepteur génère également un manifeste, un fichier XML qui décrit chaque package.

## <a name="packaging-tools"></a>Outils d’empaquetage
 Vous pouvez utiliser la **Concepteur de packages** pour personnaliser le package et générer le manifeste. Vous pouvez inclure des éléments de projet SharePoint, configurer si le serveur Web doit être réinitialisé et définissez le type de serveur de déploiement. Pour plus d'informations, voir [Procédure : Ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Vous pouvez également utiliser le **Explorateur de package** pour modifier les fonctionnalités et les éléments dans votre fichier de package (*.wsp*). Pour plus d'informations, voir [Procédure : Ajouter et supprimer des fonctionnalités et des éléments dans un Package à l’aide de l’Explorateur de package](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Vous pouvez utiliser Visual Studio et MSBuild pour créer le package (*.wsp*) fichiers à déployer votre solution SharePoint. Ce processus génère les fichiers manifestes nécessaires au déploiement de SharePoint. Pour plus d'informations, voir [Procédure : Créer un Package de Solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Options du Concepteur de package
 Le tableau suivant présente les propriétés que vous pouvez personnaliser dans les packages de SharePoint avec le **Concepteur de packages**.

|Propriété de Concepteur de package|Description du paramètre par défaut|
|-------------------------------|------------------------------------|
|Nom|Obligatoire. Le nom par défaut du package est défini sur *nom_projet*.|
|Réinitialiser le serveur Web|Facultatif. Sélectionnez si vous souhaitez redémarrer le serveur Web après la *.wsp* fichier est installé sur le serveur SharePoint.|
|Type de serveur de déploiement|Obligatoire. Par défaut, l’étendue est définie à ApplicationServer.<br /><br /> ApplicationServer : Décrit un serveur qui héberge les services.<br /><br /> WebFrontEnd : Décrit un serveur qui héberge des sites Web.|
|Éléments dans la Solution|Tous les éléments de projet SharePoint et des fonctionnalités qui peuvent être ajoutées au package.|
|Éléments dans le Package|Optionnel. Tous les éléments SharePoint et des fonctionnalités que vous souhaitez déployer dans votre package.|

## <a name="configure-the-packaging-process"></a>Configurer le processus d’empaquetage
 Une fois que vous développez des solutions SharePoint dans Visual Studio, vous pouvez personnaliser la façon dont les projets sont empaquetés.

 Le tableau suivant présente les deux cibles MSBuild que vous pouvez utiliser pour personnaliser la *.wsp* fichier est créé.

|une cible|Description|
|------------|-----------------|
|BeforeLayout|La cible qui effectue les tâches juste avant que les fichiers sont copiés dans un répertoire intermédiaire. Vous pouvez modifier les fichiers avant de créer un fichier de package (*.wsp*).|
|AfterLayout|La cible qui effectue les tâches immédiatement après que les fichiers sont copiés dans un répertoire intermédiaire.|

 Pour plus d’informations, [Comment : Personnaliser un package de solution SharePoint à l’aide de cibles MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Architecture d’empaquetage
 Les étapes suivantes se produisent lorsque vous créez un package SharePoint (*.wsp*) dans Visual Studio.

1. Les fonctionnalités et les packages sont validés pour vous assurer que la structure physique et sémantique du package est correcte.

2. Les fonctionnalités, les éléments de projet et les fichiers de package dans le package sont énumérés. Les fichiers manifeste pour les packages et les fonctionnalités sont transformés afin d’inclure toutes les informations nécessaires pour le déploiement et d’activation. Les jetons sont remplacés par la valeur qualifiée complet.

3. La cible BeforeLayout MSBuild personnalisable est effectuée. Vous pouvez créer cette étape pour apporter des modifications personnalisées au package avant la *.wsp* fichier est créé.

4. Les fichiers énumérés sont copiés dans un répertoire intermédiaire.

5. La cible MSBuild AfterLayout personnalisable est effectuée. Vous pouvez créer cette étape pour apporter des modifications personnalisées au package avant la *.wsp* fichier est créé.

6. Les fichiers du répertoire intermédiaire sont ajoutés à la *.wsp* fichier.

## <a name="package-folder-structure"></a>Structure de dossiers de package
 Lorsque vous empaquetez votre projet SharePoint, un *.wsp* fichier est créé pour vous dans le *créez\\\<BuildConfiguration >* dossier. Par exemple, si votre solution se trouve dans *C:\Visual Studio 2013\Projects\ListDefinition1* et votre configuration de build est définie sur la version, le *.wsp* fichier se trouve dans *C:\Visual Studio 2013\ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Guide pratique pour Ajouter et supprimer des fonctionnalités et des éléments dans un package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Guide pratique pour Créer un Package de Solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Guide pratique pour Créer un Package de Solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Guide pratique pour Personnaliser un package de solution SharePoint à l’aide de cibles de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
