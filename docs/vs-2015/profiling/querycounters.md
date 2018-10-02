---
title: QueryCounters | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: ff5cd703a323c93c479d69bbe956855106d80d80
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494373"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [QueryCounters](https://docs.microsoft.com/visualstudio/profiling/querycounters).  
  
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



