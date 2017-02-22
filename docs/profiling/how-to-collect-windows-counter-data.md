---
title: "Comment&#160;: collecter les donn&#233;es des compteurs Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.syscounter"
  - "vs.performance.property.wincounter"
helpviewer_keywords: 
  - "compteurs Windows"
  - "outils d’analyse des performances, utiliser les compteurs Windows"
  - "outils de profilage, utiliser les compteurs Windows"
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment&#160;: collecter les donn&#233;es des compteurs Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les compteurs Windows sont des compteurs de performance système qui peuvent être collectés à des intervalles définis pendant le profilage.  L'affichage Marques du rapport Outils de profilage comprend une ligne intitulée **AutoMark** pour chaque intervalle de collection.  La ligne contient des colonnes qui décrivent les valeurs des compteurs de performance à cet intervalle.  Pour restreindre l'analyse à une période comprise entre deux marques particulières, sélectionnez les marques, cliquez avec le bouton droit, puis sélectionnez **Filtrer par**\-\>  **Marques** dans le menu contextuel.  
  
 **Conditions requises**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### Pour collecter les données des compteurs Windows  
  
1.  Dans l'Explorateur de performances, cliquez avec le bouton droit sur la session pour laquelle vous souhaitez configurer des compteurs Windows, puis sélectionnez **Propriétés**.  
  
2.  Dans les **pages de propriétés**, cliquez sur **Compteurs Windows**.  
  
3.  Activez la case à cocher **Collecter les compteurs Windows**.  
  
4.  Dans la zone de texte **Intervalle de collecte \(ms\)**, tapez un intervalle de temps.  
  
5.  Sélectionnez une catégorie dans la liste déroulante **Catégorie de compteurs**.  
  
6.  Sélectionnez une instance dans la liste déroulante **Instance**.  
  
7.  Sélectionnez les compteurs à utiliser lorsque vous profilez votre application.  
  
8.  Cliquez sur **Appliquer**.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Propriétés d’une session de performance](../profiling/performance-session-properties.md)   
 [Compteurs UC et Windows](../profiling/cpu-and-windows-counters.md)