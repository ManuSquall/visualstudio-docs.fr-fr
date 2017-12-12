---
title: QueryCounters | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b8dbbf2539980f775fb6385303a3fcfe7ae7e07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="querycounters"></a>QueryCounters
L’option **/QueryCounters** répertorie les compteurs de performances (matériels) de l’UC qui sont disponibles sur l’ordinateur.  
  
 **QueryCounters** doit être la seule option sur la ligne de commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucune  
  
## <a name="remarks"></a>Remarques  
 Quand vous utilisez la méthode d’instrumentation, le profileur peut collecter les valeurs d’un ou plusieurs compteurs de performances de l’UC à chaque événement de collecte de données. Quand vous utilisez la méthode de profilage par échantillonnage, vous pouvez spécifier un événement de compteur et le nombre d’occurrences de l’événement à utiliser comme intervalle d’échantillonnage.  
  
 Les différents processeurs exposent des compteurs de performances d’UC différents. Le profileur définit un ensemble de compteurs génériques qui peuvent être utilisés sur presque tous les processeurs. L’option **QueryCounters** répertorie les noms des compteurs génériques et les noms des compteurs qui sont spécifiques au processeur.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)