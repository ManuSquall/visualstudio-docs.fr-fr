---
title: Modèle de projet VSIX | Microsoft Docs
description: Découvrez comment utiliser le modèle de projet VSIX pour encapsuler les extensions Visual Studio dans un projet VSIX, puis publier le package sur le Visual Studio Marketplace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8f8e5e9f9a5a21600aa894ee8b7f6c3730bc1fc7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062262"
---
# <a name="vsix-project-template"></a>Modèle de projet VSIX

Vous pouvez utiliser le modèle de projet VSIX pour encapsuler une ou plusieurs extensions Visual Studio dans un projet VSIX, puis publier le package sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

 Le déploiement VSIX prend en charge les VSPackages, les assemblys, les composants MEF, les modèles de projet, les modèles d’élément, les contrôles de boîte à outils et les types d’extension personnalisés.

> [!NOTE]
> Pour utiliser des projets VSIX, vous devez installer le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations sur le kit de développement logiciel (SDK) Visual Studio, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Où trouver le modèle de projet VSIX

Le modèle de projet VSIX est disponible dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».  Il existe à la fois une version C# et Visual Basic.

> [!TIP]
> Vous devez vous assurer que .NET Framework 4,5 ou une version ultérieure est spécifié dans la zone de liste déroulante en haut de la boîte de dialogue **nouveau projet** .

## <a name="uses-of-the-vsix-project-template"></a>Utilisations du modèle de projet VSIX

Le modèle de projet VSIX a deux utilisations principales :

- Pour déployer des modèles de projet, des modèles d’élément et des extensions.

- Pour encapsuler les sorties de plusieurs extensions dans un package de déploiement.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empaquetage d’une extension dans un projet VSIX vide

Vous pouvez empaqueter une extension existante, ou une extension qui n’a pas encore de prise en charge VSIX, en l’encapsulant dans un projet VSIX vide. L’extension à inclure dans un wrapper doit être d’un type pris en charge par le [schéma VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Pour empaqueter une extension à l’aide d’un projet VSIX

1. Générez les projets qui composent votre extension.

2. Créez un projet VSIX à l’aide du modèle de **projet VSIX** .

    *Source. extension. vsixmanifest* s’ouvre dans le **Concepteur de manifeste**.

3. Sous l’onglet **ressources** , cliquez sur le bouton **nouveau** .

    La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

4. Dans la liste **type** , choisissez le type d’extension à ajouter.

5. Pour ajouter une extension ou un élément de contenu qui est inclus dans la solution actuelle (par exemple, un modèle d’élément ou un assembly compilé), procédez comme suit :

   1. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

   2. Dans la liste **projet** , choisissez le nom de l’extension.

   3. Dans la zone **incorporer dans ce dossier** , entrez le nom d’un dossier dans lequel incorporer l’élément multimédia, puis choisissez le bouton **OK** .

6. Pour ajouter une extension ou un élément de contenu qui n’est pas inclus dans la solution actuelle, procédez comme suit :

   1. Dans la zone de liste **source** , choisissez **fichier sur FileSystem**.

   2. Dans le champ **chemin d’accès** , entrez le chemin d’accès complet au fichier d’extension compilé ou compressé, ou utilisez le bouton **Parcourir** pour accéder au fichier.

   3. Dans la zone **incorporer dans ce dossier** , entrez le nom d’un dossier dans lequel incorporer l’élément multimédia, puis choisissez le bouton **OK** .

7. Si vous souhaitez que votre package inclue des extensions supplémentaires, ajoutez-les de la même manière.

8. Générez la solution.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère un fichier *. vsix* qui contient un fichier manifeste VSIX, un fichier [Content_Types]*. xml* et tous les composants d’extension que vous avez ajoutés au projet.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le schéma d’extension VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
