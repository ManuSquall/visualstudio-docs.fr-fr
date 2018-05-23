---
title: 'Comment : créer un Package de Solution SharePoint à l’aide de tâches MSBuild | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 392724510e3145450cbea8ee70d23037ded073a1
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Comment : créer un package de solution SharePoint à l’aide de tâches MSBuild
  Vous pouvez générer, nettoyer et valider un package SharePoint (.wsp) à l’aide des tâches MSBuild de ligne de commande sur un ordinateur de développement. Vous pouvez également utiliser ces commandes pour automatiser le processus de génération à l’aide de Team Foundation Server sur un ordinateur de build.  
  
## <a name="building-a-sharepoint-package"></a>Création d’un Package SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Pour créer un package SharePoint  
  
1.  Sur les fenêtres **Démarrer** menu, choisissez **tous les programmes**, **Accessoires**, **invite de commandes**.  
  
2.  Accédez au répertoire où se trouve votre projet SharePoint.  
  
3.  Entrez la commande suivante pour créer un package pour le projet. Remplacez *ProjectFileName* avec le nom du projet.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Par exemple, vous pouvez exécuter l’une des commandes suivantes pour empaqueter un projet SharePoint appelé ListDefinition1.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="cleaning-a-sharepoint-package"></a>Nettoyage d’un Package SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Pour nettoyer un package SharePoint  
  
1.  Ouvrez une fenêtre d’invite de commandes.  
  
2.  Accédez au répertoire où se trouve votre projet SharePoint.  
  
3.  Entrez la commande suivante pour nettoyer un package pour le projet. Remplacez *ProjectFileName* avec le nom du projet.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Par exemple, vous pouvez exécuter l’une des commandes suivantes pour nettoyer un projet SharePoint appelé ListDefinition1.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validating-a-sharepoint-package"></a>Validation d’un Package SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Pour valider un package SharePoint  
  
1.  Ouvrez une fenêtre d’invite de commandes.  
  
2.  Accédez au répertoire où se trouve votre projet SharePoint.  
  
3.  Entrez la commande suivante pour valider un package pour le projet. Remplacez *ProjectFileName* avec le nom du projet.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Par exemple, vous pouvez exécuter l’une des commandes suivantes pour valider un projet SharePoint appelé ListDefinition1.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="setting-properties-in-a-sharepoint-package"></a>Définition des propriétés dans un Package SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Pour définir une propriété dans un package SharePoint  
  
1.  Ouvrez une fenêtre d’invite de commandes.  
  
2.  Accédez au répertoire où se trouve votre projet SharePoint.  
  
3.  Entrez la commande suivante pour définir une propriété dans un package pour le projet. Remplacez *PropertyName* avec la propriété que vous souhaitez définir.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Par exemple, vous pourriez exécuter la commande suivante pour définir le niveau d’avertissement.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Création de fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Guide pratique pour ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  