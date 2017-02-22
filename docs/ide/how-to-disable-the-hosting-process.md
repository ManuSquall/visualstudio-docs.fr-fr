---
title: "Comment&#160;: d&#233;sactiver le processus d&#39;h&#233;bergement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "processus d'hébergement, désactiver"
  - "vshost.exe, désactiver le processus d'hébergement"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;sactiver le processus d&#39;h&#233;bergement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les appels à certaines API peuvent être affectés lorsque le processus hôte est activé.  Dans ces situations, il est nécessaire de désactiver le processus d'hébergement pour retourner les résultats corrects.  
  
### Pour désactiver le processus d'hébergement.  
  
1.  Ouvrez un projet exécutable dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Les projets qui ne produisent pas de fichiers exécutables \(par exemple, les bibliothèque de classes ou les projets de service\) n'ont pas cette option.  
  
2.  Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
3.  Cliquez sur l'onglet **Débogage**.  
  
4.  Désactivez la case à cocher **Activer le processus d'hébergement Visual Studio**.  
  
 Lorsque le processus d'hébergement est désactivé, plusieurs fonctionnalités de débogage sont indisponibles ou subissent une baisse de performance.  Pour plus d'informations, consultez [Débogage et processus d'hébergement](../debugger/debugging-and-the-hosting-process.md).  
  
 En général, lorsque le processus d'hébergement est désactivé :  
  
-   Le temps nécessaire au débogage des applications [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] augmente.  
  
-   L'évaluation d'une expression au moment du design n'est pas disponible.  
  
-   Le débogage de confiance partielle n'est pas disponible.  
  
## Voir aussi  
 [Débogage et processus d'hébergement](../debugger/debugging-and-the-hosting-process.md)   
 [Processus d'hébergement \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/fr-fr/c9497d62-3b7b-4449-88e8-cf27acc9efe6)