---
title: Console | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e1870870301b4f9812ea9a16fe6089fd72028b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987425"
---
# <a name="console"></a>Console
L’option **Console** de VSPerfCmd.exe démarre l’application spécifiée dans une nouvelle fenêtre d’invite de commandes. L’option **Console** peut être utilisée seulement avec l’option **Launch** de VSPerfCmd. Si l’application n’est pas une application en ligne de commande, **Console** n’a aucun effet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="required-options"></a>Options obligatoires  
 Vous pouvez spécifier **Console** seulement sur une ligne de commande qui contient aussi l’option **Launch**.  
  
 **Launch :** `AppName`  
 Démarre le profileur et l'application spécifiée par `AppName`.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)