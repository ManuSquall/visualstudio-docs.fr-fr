---
title: 'Procédure : Créer un Package de Solution SharePoint à l’aide de tâches MSBuild | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f6fd87a9c666e3373515cf8df59d7cd9fd7c717
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624397"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Procédure : Créer un Package de Solution SharePoint à l’aide de tâches MSBuild
  Vous pouvez générer, nettoyer et valider un package SharePoint (*.wsp*) à l’aide des tâches MSBuild de ligne de commande sur un ordinateur de développement. Vous pouvez également utiliser ces commandes pour automatiser le processus de génération à l’aide de Team Foundation Server sur un ordinateur de build.

## <a name="build-a-sharepoint-package"></a>Créer un package SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Pour générer un package SharePoint

1.  Sur le Windows **Démarrer** menu, choisissez **tous les programmes** > **Accessoires** > **invite de commandes**.

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

## <a name="clean-a-sharepoint-package"></a>Nettoyer un package SharePoint

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

## <a name="validate-a-sharepoint-package"></a>Valider un package SharePoint

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

## <a name="set-properties-in-a-sharepoint-package"></a>Définir les propriétés dans un package SharePoint

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Pour définir une propriété dans un package SharePoint

1.  Ouvrez une fenêtre d’invite de commandes.

2.  Accédez au répertoire où se trouve votre projet SharePoint.

3.  Entrez la commande suivante pour définir une propriété dans un package pour le projet. Remplacez *PropertyName* avec la propriété que vous souhaitez définir.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Par exemple, vous pouvez exécutez la commande suivante pour définir le niveau d’avertissement.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Voir aussi
- [Créer des fonctionnalités de SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Guide pratique pour Personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Guide pratique pour Ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
