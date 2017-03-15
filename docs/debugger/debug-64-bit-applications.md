---
title: "D&#233;boguer des applications 64&#160;bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogage [Visual Studio], 64 bits"
  - "débogage 64 bits"
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# D&#233;boguer des applications 64&#160;bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez déboguer une application 64 bits qui s'exécute sur l'ordinateur local ou sur un ordinateur distant.  
  
 Pour déboguer une application 64 bits qui s’exécute sur un ordinateur distant, consultez [Débogage distant](../debugger/remote-debugging.md).  
  
 Pour déboguer des applications 64 bits localement, Visual Studio utilise un processus de travail 64 bits \(msvsmon.exe\) pour effectuer les opérations de bas niveau qui ne peuvent pas être réalisées à l’intérieur du processus Visual Studio 32 bits.  
  
 Le débogage en mode mixte n’est pas pris en charge pour les processus 64 bits qui utilisent .NET Framework version 3.5 ou antérieure.  
  
## Déboguer une application 64 bits  
 Pour essayer de déboguer une application 64 bits :  
  
1.  Créez une solution Visual Studio, par exemple une application console C\#.  
  
2.  Définissez une configuration 64 bits à l’aide du Gestionnaire de configurations. Pour plus d'informations, consultez [Comment : configurer des projets pour des plateformes cibles](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  À ce stade, la version 64 bits du débogueur distant \(msvsmon.exe\) démarre. Le débogueur s’exécute tant que la solution avec la configuration 64 bits est ouverte.  
  
4.  Démarrez le débogage. Vous devez avoir la même expérience qu’avec une configuration 32 bits. Si vous obtenez des erreurs, consultez la section de résolution des problèmes ci\-dessous.  
  
## Résolution des problèmes de débogage 64 bits  
 L’erreur suivante peut s’afficher : « Une opération de débogage 64 bits prend plus de temps que prévu ». Dans ce cas, Visual Studio a envoyé une demande à la version 64 bits de msvsmon.exe et l’obtention du résultat de cette demande a pris beaucoup de temps.  
  
 Deux causes principales peuvent provoquer cette erreur :  
  
-   Un logiciel de sécurité réseau installé sur votre ordinateur altère la fiabilité de la pile de mise en réseau, et il a ignoré des paquets qui passent sur localhost. Essayez de désactiver tous les logiciels de sécurité réseau et voyez si le problème est résolu. Si tel est le cas, signalez à votre fournisseur de logiciels de sécurité réseau que le logiciel interfère avec le trafic de localhost.  
  
-   Vous rencontrez un problème de blocage ou de performances avec Visual Studio. Si le problème se produit régulièrement, vous pouvez collecter les dumps de Visual Studio \(devenv.exe\) et le processus de travail \(msvsmon.exe\), puis les envoyer à Microsoft. Pour plus d’informations sur le signalement d’un problème, consultez [Comment signaler un problème avec Visual Studio](../Topic/How%20to%20Report%20a%20Problem%20with%20Visual%20Studio.md).  
  
## Voir aussi  
 [Applications 64 bits](../Topic/64-bit%20Applications.md)   
 [Configuration des programmes pour les processeurs 64 bits](/visual-cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Prise en charge de l'IDE de Visual Studio 64 bits](../ide/visual-studio-ide-64-bit-support.md)   
 [Utiliser les fichiers de dump pour déboguer les pannes et blocages d'application](../debugger/using-dump-files.md)   
 [Débogage distant](../debugger/remote-debugging.md)