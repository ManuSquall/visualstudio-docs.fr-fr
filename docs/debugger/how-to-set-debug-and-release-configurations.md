---
title: 'Comment : définir debug et release configurations | Documents Microsoft'
ms.custom: H1HackMay2017
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ae43c5cab67d79450cea1dc024da98fe25c5375
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34690664"
---
# <a name="how-to-set-debug-and-release-configurations-in-visual-studio"></a>Comment : définir debug et release de configurations dans Visual Studio
Les projets Visual Studio ont des configurations Release et Debug distinctes pour votre programme. Comme le nom l'indique, vous générez la version Debug pour le débogage et la version Release pour la distribution de la version finale.  
  
La configuration Debug de votre programme est compilée avec des informations de débogage relatives aux symboles et aucune optimisation. L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.  
  
La configuration Release de votre programme ne contient pas d’informations de débogage relatives aux symboles et est entièrement optimisée. Déboguer des informations peuvent être générées dans les fichiers .pdb, [selon les options du compilateur](#BKMK_symbols_release) qui sont utilisés. Création des fichiers .pdb peut être très utile si vous devez ultérieurement déboguer votre version release.  
  
Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).  
  
Vous pouvez modifier la configuration de build à partir de la **générer** menu, à partir de la barre d’outils ou dans les pages de propriétés du projet. Les pages de propriétés du projet sont spécifiques au langage. La procédure suivante montre comment changer la configuration de build à partir du menu et de la barre d'outils. Pour plus d’informations sur la façon de modifier la configuration de build dans les projets dans différentes langues, consultez la section Voir aussi.  
  
## <a name="change-the-build-configuration"></a>Modifier la configuration de build  
  
1.  À partir de la **générer** menu, sélectionnez **Configuration Manager**, puis sélectionnez **déboguer** ou **version**.  
  
2.  Dans la barre d’outils, choisissez **déboguer** ou **version** à partir de la **Configurations de Solution** zone de liste.  
  
     ![configuration de build de barre d’outils](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Cette barre d'outils n'est pas disponible dans les éditions Express. Vous pouvez utiliser la **Générer Solution (F6)** et **démarrer le débogage F5** des éléments de menu pour choisir la configuration.

## <a name="BKMK_symbols_release"></a>Générer des fichiers de symboles (.pdb) pour une build

Pour la plupart des types de projet, les fichiers .pdb sont générés par défaut pour les versions debug et versions release, mais les paramètres par défaut sont différents en fonction de votre type de projet spécifique et la version de Visual Studio. Vous pouvez configurer si le compilateur génère les fichiers .pdb et quel type d’informations de débogage à inclure.

> [!IMPORTANT] 
> Le débogueur chargera uniquement un fichier .pdb pour un fichier exécutable qui correspond exactement au fichier .pdb créé lors de la génération du fichier exécutable (autrement dit, le fichier .pdb doit être le fichier d'origine ou une copie du fichier .pdb d'origine). Pour plus d’informations, consultez l’entrée de blog intitulée [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with? (Pourquoi Visual Studio exige-t-il que les fichiers de symboles du débogueur correspondent exactement aux fichiers binaires avec lesquels ils ont été créés ?)](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Chaque type de projet peut avoir une manière différente de la définition de ces options.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Générer des fichiers de symboles pour un projet c#, ASP.NET ou Visual Basic

Pour plus d’informations sur les paramètres de projet pour les configurations debug en c#, consultez [paramètres pour une configuration c# Debug du projet](../debugger/project-settings-for-csharp-debug-configurations.md). Pour Visual Basic, consultez [cette rubrique](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Cliquez sur le projet dans l’Explorateur de solutions et choisissez **propriétés**.

2. Choisissez un **version** ou **déboguer** construire à partir de la **Configuration** liste.

2. Choisissez **générer** paramètres, puis cliquez sur le **avancé** bouton.

    En Visual Basic, vous choisissez la **compiler** paramètres et la **Options avancées de compilation** bouton à la place.

3. Choisissez **complète**, **portable**, ou **pdb_only** dans les **les informations de débogage** zone de liste (**générer des infos de débogage** en Visual Basic).

    Le format portable est le format inter-plateformes plus récent pour .NET Core. Pour plus d’informations sur les options, consultez [boîte de dialogue Paramètres de génération avancés (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Générer des fichiers PDB pour les builds en C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Générez votre projet.

    Les fichiers de symboles sont créés dans le même dossier que le fichier exécutable ou fichier de sortie principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Générer des fichiers de symboles pour un projet C++

1. Cliquez sur le projet dans l’Explorateur de solutions et choisissez **propriétés**.

2. Choisissez un **version** ou **déboguer** construire à partir de la **Configuration** liste.

2. Sous **l’éditeur de liens > débogage**, sélectionnez souhaitée des options pour **générer des infos de débogage**.

    Pour plus d’informations sur les paramètres de projet pour les configurations debug c++, consultez [paramètres pour une configuration de débogage C++ du projet](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Configurer les options de génération de fichiers de base de données de programme

    Dans la plupart des projets C++, la valeur par défaut est `$(OutDir)$(TargetName).pdb`, ce qui génère des fichiers .pdb dans le dossier de sortie.

    ![Générer des fichiers PDB pour les builds en C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Générez votre projet.

    Les fichiers de symboles sont créés dans le même dossier que le fichier exécutable ou fichier de sortie principal.
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les fichiers de symboles (.pdb) et les fichiers sources dans le débogueur Visua Studio](../debugger/debugger-settings-and-preparation.md)  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Paramètres de projet pour une Configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)
