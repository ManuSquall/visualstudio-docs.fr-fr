---
title: Créer un package de solution SharePoint à l’aide de tâches MSBuild
description: Découvrez comment générer, nettoyer et valider un package de solution SharePoint (. wsp) à l’aide de tâches MSBuild de ligne de commande sur un ordinateur de développement.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f4c1d2e986b6a810cc568efd9577be87a38fdefb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873539"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Comment : créer un package de solution SharePoint à l’aide de tâches MSBuild
  Vous pouvez générer, nettoyer et valider un package SharePoint (*. wsp*) à l’aide de tâches MSBuild de ligne de commande sur un ordinateur de développement. Vous pouvez également utiliser ces commandes pour automatiser le processus de génération à l’aide de Team Foundation Server sur un ordinateur de Build.

## <a name="build-a-sharepoint-package"></a>Créer un package SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Pour créer un package SharePoint

1. Dans le menu **Démarrer** de Windows, choisissez **tous les programmes**  >  **accessoires**  >  **invite de commandes**.

2. Accédez au répertoire où se trouve votre projet SharePoint.

3. Entrez la commande suivante pour créer un package pour le projet. Remplacez *ProjectFileName* par le nom du projet.

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

1. Ouvrir une fenêtre d’invite de commandes.

2. Accédez au répertoire où se trouve votre projet SharePoint.

3. Entrez la commande suivante pour nettoyer un package pour le projet. Remplacez *ProjectFileName* par le nom du projet.

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

1. Ouvrir une fenêtre d’invite de commandes.

2. Accédez au répertoire où se trouve votre projet SharePoint.

3. Entrez la commande suivante pour valider un package pour le projet. Remplacez *ProjectFileName* par le nom du projet.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Par exemple, vous pouvez exécuter l’une des commandes suivantes pour valider un projet SharePoint appelé ListDefinition1.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Définir des propriétés dans un package SharePoint

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Pour définir une propriété dans un package SharePoint

1. Ouvrir une fenêtre d’invite de commandes.

2. Accédez au répertoire où se trouve votre projet SharePoint.

3. Entrez la commande suivante pour définir une propriété dans un package pour le projet. Remplacez *PropertyName* par la propriété que vous souhaitez définir.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Par exemple, vous pouvez exécuter la commande suivante pour définir le niveau d’avertissement.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Voir aussi
- [Créer des fonctionnalités SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Comment : ajouter et supprimer des éléments dans des fonctionnalités SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
