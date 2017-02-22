---
title: "Comment&#160;: d&#233;finir des configurations Debug et Release | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.builds"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "configurations de build, déboguer"
  - "configurations de build, version"
  - "configurations, version"
  - "versions debug"
  - "versions debug, modifier les paramètres de la configuration"
  - "versions debug, basculer en version release"
  - "configurations de débogage"
  - "déboguer (Visual Studio), configurations de débogage"
  - "déboguer (Visual Studio), configurations Release"
  - "projets (Visual Studio), configurations de débogage"
  - "projets (Visual Studio), configurations Release"
  - "versions release, modifier les paramètres"
  - "versions release, basculer en version debug"
  - "projets Visual Basic, versions debug et release"
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Comment&#160;: d&#233;finir des configurations Debug et Release
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les projets Visual Studio ont des configurations Release et Debug distinctes pour votre programme.  Comme le nom l'indique, vous générez la version Debug pour le débogage et la version Release pour la distribution de la version finale.  
  
 La configuration Debug de votre programme est compilée avec des informations de débogage relatives aux symboles et aucune optimisation.  L'optimisation complique le débogage, étant donné que la relation entre le code source et les instructions générées est plus complexe.  
  
 La configuration Release de votre programme ne contient pas d'informations de débogage relatives aux symboles et est entièrement optimisée.  Les informations de débogage peuvent être générées dans des fichiers PDB, selon les options de compilateur utilisées.  La création de fichiers PDB peut être très utile si vous devez ultérieurement déboguer votre version Release.  
  
 Pour plus d'informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).  
  
 Vous pouvez modifier la configuration de build à partir du menu **Générer**, à partir de la barre d'outils ou dans les pages de propriétés du projet.  Les pages de propriétés du projet sont spécifiques au langage.  La procédure suivante montre comment changer la configuration de build à partir du menu et de la barre d'outils.  Pour plus d'informations sur la modification de la configuration de build dans des projets dans différents langages, consultez la section Rubriques connexes ci\-dessous.  
  
### Pour changer la configuration de build  
  
1.  À partir du menu Générer : cliquez sur **Générer\/Gestionnaire de configurations**, puis sélectionnez **Debug** ou **Release**.  
  
2.  Dans la barre d'outils, choisissez **Debug**  ou **Release** dans la zone de liste **Configurations de solutions**.  
  
     ![configuration de build de barre d’outils](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Cette barre d'outils n'est pas disponible dans les éditions Express.  Vous pouvez utiliser les commandes de menu **Générer la solution \(F6\)** et **Démarrer le débogage \(F5\)** pour choisir la configuration.  
  
## Voir aussi  
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)   
 [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Paramètres de projet pour des configurations Debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e)