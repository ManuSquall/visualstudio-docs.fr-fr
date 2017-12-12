---
title: "Guide pratique pour collecter les données de suivi d’événements pour Windows (ETW) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ad7c937ba6c3845e905abea31f4525198f8389
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Guide pratique pour collecter les données de suivi d’événements pour Windows (ETW)
Le suivi d’événements pour Windows (ETW) est une fonctionnalité de traçage efficace de niveau noyau qui permet de journaliser les événements de noyau et les événements définis par l’application du profileur. Les données collectées à partir du fournisseur d’événements ne peuvent être affichées qu’à l’aide de l’option /**Summary:ETW** de l’outil en ligne de commande [VSPerfReport](../profiling/vsperfreport.md). Vous pouvez utiliser ce rapport pour déterminer où se situent les problèmes de performances au sein de l’application.  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Pour activer les fournisseurs de suivi d’événements  
  
1.  Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Dans les **Pages de propriétés**, cliquez sur les propriétés **Événements Windows**.  
  
3.  Dans la liste **Sélectionner les fournisseurs de suivi d’événements desquels collecter des données**, sélectionnez les fournisseurs d’événements que vous voulez utiliser pour profiler votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performances](../profiling/configuring-performance-sessions.md)