---
title: Définir les configurations Debug et Release | Microsoft Docs
description: Définissez les configurations Debug et Release dans Visual Studio. Vous générez la version Debug pour le débogage et la version Release pour la distribution de la version finale.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f96570f517d24492ecdacb4e45450fa7b7ba1cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908397"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Définir des configurations Debug et Release dans Visual Studio

Les projets Visual Studio ont des configurations Release et Debug distinctes pour votre programme. Vous générez la version Debug pour le débogage et la version Release pour la distribution de la version finale.

Dans la configuration de débogage, votre programme est compilé avec des informations de débogage symboliques complètes et aucune optimisation. L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.

La configuration Release de votre programme n’a pas d’informations de débogage symboliques et est entièrement optimisée. Pour le code managé et le code C++, les informations de débogage peuvent être générées dans des fichiers. pdb, [selon les options du compilateur](#BKMK_symbols_release) utilisées. La création de fichiers. pdb peut être utile si vous devez ultérieurement déboguer votre version Release.

Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).

Vous pouvez modifier la configuration de build à partir du menu **Générer**, à partir de la barre d’outils ou dans les pages de propriétés du projet. Les pages de propriétés du projet sont spécifiques au langage. La procédure suivante montre comment changer la configuration de build à partir du menu et de la barre d'outils. Pour plus d’informations sur la modification de la configuration de build dans des projets dans différents langages, consultez la section [Voir aussi](#see-also) ci-dessous.

## <a name="change-the-build-configuration"></a>Modifier la configuration de build

Pour modifier la configuration de build, effectuez l’une des opérations suivantes :

* Dans le menu **générer** , sélectionnez **Configuration Manager**, puis sélectionnez **Debug** ou **Release**.

or

* Dans la barre d’outils, choisissez **Debug** ou **Release** dans la liste **Configurations de solutions**.

  ![configuration de build des barres d’outils](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Générer des fichiers de symboles (. pdb) pour une génération (C#, C++, Visual Basic, F #)

Vous pouvez choisir de générer des fichiers de symboles (. pdb) et les informations de débogage à inclure. Pour la plupart des types de projets, le compilateur génère des fichiers de symboles par défaut pour les versions Debug et Release, tandis que les autres paramètres par défaut diffèrent selon le type de projet et la version de Visual Studio.

> [!IMPORTANT]
> Le débogueur chargera uniquement un fichier .pdb pour un fichier exécutable qui correspond exactement au fichier .pdb créé lors de la génération du fichier exécutable (autrement dit, le fichier .pdb doit être le fichier d'origine ou une copie du fichier .pdb d'origine). Pour plus d’informations, consultez [raisons pour lesquelles Visual Studio requiert que les fichiers de symboles du débogueur correspondent exactement aux fichiers binaires avec lesquels ils ont été générés](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with).

Chaque type de projet peut avoir une façon différente de définir ces options.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Générer des fichiers de symboles pour un projet C#, ASP.NET ou Visual Basic

Pour plus d’informations sur les paramètres de projet pour les configurations de débogage en C# ou Visual Basic, consultez [paramètres de projet pour une configuration de débogage c#](../debugger/project-settings-for-csharp-debug-configurations.md) ou [paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Dans l’Explorateur de solutions, sélectionnez le projet.

2. Sélectionnez l’icône **Propriétés** (ou appuyez sur **Alt + Entrée**).

3. Dans le volet latéral, choisissez **générer** (ou **compilez** dans Visual Basic).

4. Dans la liste **configuration** , choisissez **Déboguer** ou **version finale**.

5. Sélectionnez le bouton **avancé** (ou le bouton **Options avancées de compilation** dans Visual Basic).

6. Dans la **liste informations de débogage** (ou générer la liste d’informations de **débogage** dans Visual Basic), choisissez **Full**, **PDB uniquement** ou **portable**.

   Le format portable est le format multiplateforme le plus récent pour .NET Core. Pour plus d’informations sur les options, consultez [paramètres de build avancés, boîte de dialogue (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Générer des fichiers PDB pour les builds en C #](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Générez votre projet.

   Le compilateur crée le ou les fichiers de symboles dans le même dossier que le fichier exécutable ou le fichier de sortie principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Générer des fichiers de symboles pour un projet C++

1. Dans l’Explorateur de solutions, sélectionnez le projet.

2. Sélectionnez l’icône **Propriétés** (ou appuyez sur **Alt + Entrée**).

3. Dans la liste **configuration** , choisissez **Déboguer** ou **version finale**.

4. Dans le volet latéral, choisissez **éditeur de liens > débogage**, puis sélectionnez les options pour **générer des informations de débogage**.

   Pour plus d’informations sur les paramètres de projet pour les configurations de débogage en C++, consultez [paramètres de projet pour une configuration de débogage c++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Configurez les options de **génération des fichiers de base de données du programme**.

   Dans la plupart des projets C++, la valeur par défaut est `$(OutDir)$(TargetName).pdb` , qui génère des fichiers. pdb dans le dossier de sortie.

   ![Générer des fichiers PDB pour les builds en C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Générez votre projet.

   Le compilateur crée le ou les fichiers de symboles dans le même dossier que le fichier exécutable ou le fichier de sortie principal.

## <a name="see-also"></a><a name="see-also"></a>Voir aussi

- [Spécifier les fichiers de symboles (. pdb) et les fichiers sources dans le débogueur Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)<br/>
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Paramètres de projet pour une configuration Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)