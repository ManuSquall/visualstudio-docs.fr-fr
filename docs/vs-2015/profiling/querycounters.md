---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ee9028f3fe4d72d70b2d9b6acab2c70705bfe40
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175251"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **/QueryCounters** répertorie les compteurs de performances (matériels) de l’UC qui sont disponibles sur l’ordinateur.  
  
 **QueryCounters** doit être la seule option sur la ligne de commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Quand vous utilisez la méthode d’instrumentation, le profileur peut collecter les valeurs d’un ou plusieurs compteurs de performances de l’UC à chaque événement de collecte de données. Quand vous utilisez la méthode de profilage par échantillonnage, vous pouvez spécifier un événement de compteur et le nombre d’occurrences de l’événement à utiliser comme intervalle d’échantillonnage.  
  
 Les différents processeurs exposent des compteurs de performances d’UC différents. Le profileur définit un ensemble de compteurs génériques qui peuvent être utilisés sur presque tous les processeurs. L’option **QueryCounters** répertorie les noms des compteurs génériques et les noms des compteurs qui sont spécifiques au processeur.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)



