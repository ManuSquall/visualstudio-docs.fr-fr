---
title: Création de Packages de Solution SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e0fd1a6f424e45b8982d4e05ea501186c45b96aa
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692000"
---
# <a name="creating-sharepoint-solution-packages"></a>Création de packages de solution SharePoint
  À l’aide du Concepteur de packages, vous pouvez créer et personnaliser des packages de déploiement. Par exemple, vous pouvez ajouter des éléments de projet SharePoint et des fonctionnalités, réinitialiser le serveur IIS, définir des étendues de l’activation de fonctionnalité et identifier les dépendances de fonctionnalité. Le concepteur génère également un manifeste, un fichier XML qui décrit chaque package.  
  
## <a name="packaging-tools"></a>Outils d’empaquetage
 Vous pouvez utiliser la **Concepteur de packages** pour personnaliser le package et générer le manifeste. Vous pouvez inclure des éléments de projet SharePoint, configurer si le serveur Web doit être réinitialisé et définir le type de serveur de déploiement. Pour plus d’informations, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un Package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
 Vous pouvez également utiliser le **Explorateur de package** pour modifier les fonctionnalités et les éléments de votre fichier de package (.wsp). Pour plus d’informations, consultez [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un Package à l’aide de l’Explorateur de package](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
 Vous pouvez utiliser Visual Studio et MSBuild pour créer des fichiers de package (.wsp) pour déployer votre solution SharePoint. Ce processus génère les fichiers manifestes nécessaires au déploiement de SharePoint. Pour plus d’informations, consultez [Comment : créer un SharePoint Package](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b) et [Comment : créer un Package de Solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).  
  
## <a name="package-designer-options"></a>Options du Concepteur de package
 Le tableau suivant présente les propriétés que vous pouvez personnaliser dans les packages SharePoint avec les **Concepteur de packages**.  
  
|Propriété de Concepteur de package|Description du paramètre par défaut|  
|-------------------------------|------------------------------------|  
|Name|Obligatoire. Le nom par défaut du package a la valeur *nom_projet*.|  
|Réinitialiser le serveur Web|Facultatif. Sélectionnez si vous souhaitez redémarrer le serveur Web une fois le fichier .wsp est installé sur le serveur SharePoint.|  
|Type de serveur de déploiement|Obligatoire. Par défaut, l’étendue est définie à ApplicationServer.<br /><br /> ApplicationServer : Décrit un serveur qui héberge des services.<br /><br /> WebFrontEnd : Décrit un serveur qui héberge des sites Web.|  
|Éléments dans la Solution|Tous les éléments de projet SharePoint et des fonctionnalités qui peuvent être ajoutées au package.|  
|Éléments dans le Package|Facultatif. Tous les éléments SharePoint et les fonctionnalités que vous souhaitez déployer dans votre package.|  
  
## <a name="configure-the-packaging-process"></a>Configurer le processus d’empaquetage
 Une fois que vous développez des solutions SharePoint dans Visual Studio, vous pouvez personnaliser comment les projets sont empaquetés.  
  
 Le tableau suivant présente les deux cibles MSBuild que vous pouvez utiliser pour personnaliser la façon dont le fichier .wsp est créé.  
  
|une cible|Description|  
|------------|-----------------|  
|BeforeLayout|La cible qui exécute des tâches avant que les fichiers sont copiés dans un répertoire intermédiaire. Vous pouvez modifier les fichiers avant de créer un fichier de package (.wsp).|  
|AfterLayout|La cible qui exécute des tâches immédiatement après que les fichiers sont copiés dans un répertoire intermédiaire.|  
  
 Pour plus d’informations, [Comment : personnaliser un Package de Solution SharePoint à l’aide de cibles de MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).  
  
## <a name="packaging-architecture"></a>Architecture d’empaquetage
 Les étapes suivantes se produisent lorsque vous créez un package SharePoint (.wsp) dans Visual Studio.  
  
1.  Les fonctionnalités et les packages sont validés pour vous assurer que la structure physique et sémantique du package est correcte.  
  
2.  Fonctionnalités, des éléments de projet et des fichiers de package dans le package sont énumérées. Les fichiers manifeste pour les packages et les fonctionnalités sont transformés afin d’inclure toutes les informations nécessaires pour le déploiement et d’activation. Les jetons sont remplacés par la valeur qualifiée complet.  
  
3.  La cible BeforeLayout MSBuild personnalisable est effectuée. Vous pouvez créer cette étape pour apporter des modifications personnalisées au package avant le fichier .wsp est créé.  
  
4.  Les fichiers énumérés sont copiés dans un répertoire intermédiaire.  
  
5.  La cible MSBuild AfterLayout personnalisable est effectuée. Vous pouvez créer cette étape pour apporter des modifications personnalisées au package avant le fichier .wsp est créé.  
  
6.  Les fichiers dans le répertoire intermédiaire sont ajoutés au fichier .wsp.  
  
## <a name="package-folder-structure"></a>Structure de dossiers de package
 Lorsque vous empaquetez votre projet SharePoint, un fichier .wsp est créé pour vous dans le créez\\*BuildConfiguration* dossier. Par exemple, si votre solution se trouve dans *lecteur*: \Visual Studio 2013\Projects\ListDefinition1 et votre configuration de build est définie pour la mise en production, le fichier .wsp se trouve dans *lecteur*: \Visual Studio 2013\ Projects\ListDefinition1\bin\Release.  
  
## <a name="see-also"></a>Voir aussi
 [Guide pratique pour personnaliser un package de solution SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Comment : ajouter et supprimer des fonctionnalités et des éléments dans un Package à l’aide du Concepteur de packages](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)   
 [Comment : créer un Package SharePoint](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)   
 [Comment : créer un Package de Solution SharePoint à l’aide de tâches MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)   
 [Guide pratique pour personnaliser un package de solution SharePoint à l’aide de cibles MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)  
  
 