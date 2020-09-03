---
title: 'Comment : définir des configurations Debug et Release | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703639"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Comment : définir des configurations Debug et Release
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les projets Visual Studio ont des configurations Release et Debug distinctes pour votre programme. Comme le nom l’indique, vous générez la version Debug pour le débogage et la version Release pour la distribution de la version finale.  
  
 La configuration Debug de votre programme est compilée avec des informations de débogage relatives aux symboles et aucune optimisation. L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.  
  
 La configuration Release de votre programme ne contient pas d’informations de débogage relatives aux symboles et est entièrement optimisée. Les informations de débogage peuvent être générées dans des fichiers PDB, selon les options de compilateur utilisées. La création de fichiers PDB peut être très utile si vous devez ultérieurement déboguer votre version Release.  
  
 Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).  
  
 Vous pouvez modifier la configuration de build à partir du menu **générer** , à partir de la barre d’outils ou dans les pages de propriétés du projet. Les pages de propriétés du projet sont spécifiques au langage. La procédure suivante montre comment changer la configuration de build à partir du menu et de la barre d'outils. Pour plus d'informations sur la modification de la configuration de build dans des projets dans différents langages, consultez la section Rubriques connexes ci-dessous.  
  
### <a name="to-change-the-build-configuration"></a>Pour changer la configuration de build  
  
1. Dans le menu Générer, cliquez sur **générer/Configuration Manager**, puis sélectionnez **Debug** ou **Release**.  
  
2. Dans la barre d’outils, choisissez **Debug** ou **Release** dans la zone de liste **configurations de solutions** .  
  
     ![configuration de build de barre d’outils](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Cette barre d'outils n'est pas disponible dans les éditions Express. Vous pouvez utiliser les éléments de menu de la **solution de génération F6** et **Démarrer le débogage F5** pour choisir la configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Paramètres de projet pour les configurations de débogage C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)   
 [Configurations de projet Debug et Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)
