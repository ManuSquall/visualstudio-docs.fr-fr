---
title: Guide pratique pour changer le répertoire de sortie de build
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4c2f2445bc7139c5bbc80a35905e24c319c9dfa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284644"
---
# <a name="how-to-change-the-build-output-directory"></a>Guide pratique pour changer le répertoire de sortie de build

Vous pouvez spécifier l’emplacement de sortie généré par votre projet en fonction de la configuration (pour Debug, Release ou les deux).

## <a name="change-the-build-output-directory"></a>Changer le répertoire de sortie de build

1. Pour ouvrir les pages de propriétés du projet, cliquez avec le bouton droit sur le nœud du projet dans l’**Explorateur de solutions**, puis sélectionnez **Propriétés**.

2. Sélectionnez l’onglet approprié en fonction du type de votre projet :

   - Pour C#, sélectionnez l’onglet **Générer**.
   - Pour Visual Basic, sélectionnez l’onglet **Compiler**.
   - Pour C++ ou JavaScript, sélectionnez l’onglet **Général**.

3. Dans la liste déroulante de configuration située dans la partie supérieure, choisissez la configuration pour laquelle vous voulez changer l’emplacement du fichier de sortie (**Debug**, **Release** ou **Toutes les configurations**).

4. Recherchez l’entrée du chemin de sortie dans la page. Elle varie en fonction du type de votre projet :

   - **Chemin de sortie** pour les projets C# et JavaScript
   - **Chemin de sortie de la génération** pour les projets Visual Basic
   - **Répertoire de sortie** pour les projets Visual C++

   Tapez le chemin vers lequel générer la sortie (absolu ou relatif au répertoire racine du projet) ou choisissez **Parcourir** pour accéder à ce dossier.

   ![Propriété de chemin de sortie pour un projet Visual Studio C#](media/output-path.png)
   
   > [!NOTE]
   > Certains projets comportent par défaut l’infrastructure et le runtime dans le chemin de la Build. Pour modifier cette valeur, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions**, sélectionnez **modifier le fichier projet**, puis ajoutez le code suivant :
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Si la sortie n’est pas générée à l’emplacement que vous avez spécifié, vérifiez que vous créez la configuration correspondante (par exemple, **Debug** ou **Release**) en la sélectionnant dans la barre de menus de Visual Studio.
>
> ![Sélecteur de configuration de build dans Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Voir aussi

- [Générer, page du concepteur de projets (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Général, page de propriétés (projet)](/cpp/build/reference/general-property-page-project)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)
