---
title: Guide pratique pour collecter les données des compteurs Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9743fa7defbbf3321636d2ba4799454713a647db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432785"
---
# <a name="how-to-collect-windows-counter-data"></a>Guide pratique pour collecter les données des compteurs Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les compteurs Windows sont des compteurs de performances système dont les données peuvent être collectées à intervalles réguliers pendant le profilage. Dans la vue Marques du rapport Outils de profilage, une ligne est étiquetée **AutoMark** pour chaque intervalle de collecte. Cette ligne contient des colonnes qui décrivent les valeurs de compteur de performances avec cet intervalle. Pour limiter l’analyse à une période située entre deux marques, sélectionnez les marques, cliquez avec le bouton droit, puis sélectionnez **Filtrer par** ->  **Marques** dans le menu contextuel.  
  
 **Spécifications**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications Windows Store demandent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Pour collecter les données des compteurs Windows  
  
1. Dans l’Explorateur de performances, cliquez avec le bouton droit sur la session pour laquelle vous voulez configurer des compteurs Windows, puis sélectionnez **Propriétés**.  
  
2. Dans les **Pages de propriétés**, cliquez sur **Compteurs Windows**.  
  
3. Cochez la case **Collecter les compteurs Windows**.  
  
4. Dans la zone de texte **Intervalle de collecte (ms)**, tapez un intervalle.  
  
5. Sélectionnez une catégorie dans la liste déroulante **Catégorie de compteurs**.  
  
6. Sélectionnez une instance dans la liste déroulante **Instance**.  
  
7. Sélectionnez les compteurs que vous voulez utiliser pour profiler votre application.  
  
8. Cliquez sur **Appliquer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Propriétés d’une session de performance](../profiling/performance-session-properties.md)   
 [Compteurs UC et Windows](../profiling/cpu-and-windows-counters.md)
