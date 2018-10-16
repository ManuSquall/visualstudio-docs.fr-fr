---
title: Définir debug et release des configurations | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: reference
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
ms.openlocfilehash: 18689a82fe2ae7c66eb8e8d6ef9bd115e2950cac
ms.sourcegitcommit: 50b19010b2e2b4736835350710e2edf93b980b56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49073987"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Définir debug et release de configurations dans Visual Studio

Les projets Visual Studio ont des configurations Release et Debug distinctes pour votre programme. Vous générez la version debug pour le débogage et la version release pour la distribution de la version finale.

Dans la configuration debug, votre programme est compilé sans informations de débogage symboliques et aucune optimisation. L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.

La configuration release de votre programme ne possède aucune information de débogage symboliques et est entièrement optimisée. Déboguer des informations peuvent être générées dans les fichiers .pdb, [selon les options du compilateur](#BKMK_symbols_release) qui sont utilisés. Création des fichiers .pdb peut être utile si vous devez ultérieurement déboguer votre version release.

Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

Vous pouvez modifier la configuration de build à partir de la **Build** menu, à partir de la barre d’outils, ou dans les pages de propriétés du projet. Les pages de propriétés du projet sont spécifiques au langage. La procédure suivante montre comment changer la configuration de build à partir du menu et de la barre d'outils. Pour plus d’informations sur la modification de la configuration de build dans les projets dans différents langages, consultez le [Voir aussi](#see-also) section ci-dessous.

## <a name="change-the-build-configuration"></a>Modifier la configuration de build

Pour modifier la configuration de build, soit :

* À partir de la **Build** menu, sélectionnez **Configuration Manager**, puis sélectionnez **déboguer** ou **version**.

ou

* Dans la barre d’outils, choisissez **déboguer** ou **version** à partir de la **Configurations de Solution** liste.

  ![configuration de build de barres d’outils](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Générer des fichiers de symboles (.pdb) pour une build

Vous pouvez choisir de générer des fichiers de symboles (.pdb) et les informations à inclure de débogage. Pour la plupart des types de projet, le compilateur génère des fichiers de symboles par défaut pour le débogage et les versions release, tandis que les autres paramètres par défaut diffèrent par type de projet et la version de Visual Studio.

> [!IMPORTANT]
> Le débogueur chargera uniquement un fichier .pdb pour un fichier exécutable qui correspond exactement au fichier .pdb créé lors de la génération du fichier exécutable (autrement dit, le fichier .pdb doit être le fichier d'origine ou une copie du fichier .pdb d'origine). Pour plus d’informations, consultez [pourquoi Visual Studio requièrent des symboles de débogueur fichiers doivent correspondre exactement aux fichiers binaires qui elles ont été générées avec ?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Chaque type de projet peut avoir une façon différente de la définition de ces options.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Générer des fichiers de symboles pour un projet c#, ASP.NET ou Visual Basic

Pour plus d’informations sur les paramètres de projet pour les configurations debug en c# ou Visual Basic, consultez [des paramètres de projet pour c# configuration debug](../debugger/project-settings-for-csharp-debug-configurations.md) ou [des paramètres de projet pour Visual Basic configurationdebug](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Dans l'Explorateur de solutions, sélectionnez le projet.

2. Sélectionnez le **propriétés** icône (ou appuyez sur **Alt + entrée**).

3. Dans le volet latéral, choisissez **Build** (ou **compiler** en Visual Basic).

4. Dans le **Configuration** , choisissez **déboguer** ou **version**.

5. Sélectionnez le **avancé** bouton (ou le **Options avancées de compilation** bouton en Visual Basic).

6. Dans le **informations de débogage** liste (ou le **générer des infos de débogage** liste en Visual Basic), choisissez **complète**, **Pdb-only**, ou **Portable**.

   Le format portable est le format inter-plateformes plus récent pour .NET Core. Pour plus d’informations sur les options, consultez [boîte de dialogue Paramètres de génération avancés (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Générer des fichiers PDB pour les builds en C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Générez votre projet.

   Le compilateur crée les fichiers de symbole dans le même dossier que le fichier exécutable ou fichier de sortie principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Générer des fichiers de symboles pour un projet C++

1. Dans l'Explorateur de solutions, sélectionnez le projet.

2. Sélectionnez le **propriétés** icône (ou appuyez sur **Alt + entrée**).

3. Dans le **Configuration** , choisissez **déboguer** ou **version**.

4. Dans le volet latéral, choisissez **l’éditeur de liens > débogage**, puis sélectionnez options pour **générer des infos de débogage**.

   Pour plus d’informations sur les paramètres de projet pour les configurations de débogage en C++, consultez [des paramètres de projet pour une C++ debug configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Configurer les options de **générer des fichiers de base de données programme**.

   Dans la plupart des projets C++, la valeur par défaut est `$(OutDir)$(TargetName).pdb`, ce qui génère des fichiers .pdb dans le dossier de sortie.

   ![Générer des fichiers PDB pour les builds en C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Générez votre projet.

   Le compilateur crée les fichiers de symbole dans le même dossier que le fichier exécutable ou fichier de sortie principal.

## <a name="see-also"></a>Voir aussi
 
[Spécifier les fichiers de symboles (.pdb) et les fichiers sources dans le débogueur Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)<br/>
[Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[Paramètres de projet pour une configuration debug c#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)
