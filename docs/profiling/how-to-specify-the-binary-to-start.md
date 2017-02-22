---
title: "Comment&#160;: sp&#233;cifier le binaire &#224; d&#233;marrer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.itemlaunch"
helpviewer_keywords: 
  - "outils de profilage, lancer"
  - "outils d’analyse des performances, lancer"
  - "sessions de performance, lancer"
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment&#160;: sp&#233;cifier le binaire &#224; d&#233;marrer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour profiler des binaires, tels que les DLL, vous devez entrer des informations dans la boîte de dialogue **Pages de propriétés de\<Cible\>** .  Ces informations indiquent où le projet de DLL peut trouver l'application appelante.  
  
 **Conditions requises**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Pour spécifier l'exécutable à démarrer  
  
1.  Dans l'**Explorateur de performances**, cliquez avec le bouton droit sur le fichier binaire cible, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Pages de propriétés**, cliquez sur les propriétés de **Lancer**.  
  
3.  Activez la case à cocher **Remplacer les paramètres du projet**.  
  
4.  Dans la zone de texte **Exécutable à lancer**, spécifiez l'emplacement du fichier.  
  
5.  Dans la zone de texte **Arguments**, spécifiez les arguments requis pour démarrer l'application.  
  
6.  Dans la zone de texte **Répertoire de travail**, spécifiez l'emplacement du répertoire.  
  
7.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)