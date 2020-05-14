---
title: Guide pratique pour changer le répertoire de sortie de build
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37342796f2dd94138136bb837cf6007d19d350c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114256"
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
   > Certains projets comprendront par défaut le cadre et l’exécution dans la voie de construction. Pour modifier cela, cliquez à droite sur le nœud du projet dans **Solution Explorer**, sélectionnez Edit **Project File**, et ajoutez ce qui suit :
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

- [Page de construction, Concepteur de projets (C)](../ide/reference/build-page-project-designer-csharp.md)
- [Page De propriété générale (projet)](/cpp/build/reference/general-property-page-project)
- [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)
