---
title: Console | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce6e9ca93d9cdca191db7db8f2eb3d144b74e40d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="console"></a>Console
L’option **Console** de VSPerfCmd.exe démarre l’application spécifiée dans une nouvelle fenêtre d’invite de commandes. L’option **Console** peut être utilisée seulement avec l’option **Launch** de VSPerfCmd. Si l’application n’est pas une application en ligne de commande, **Console** n’a aucun effet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucune  
  
## <a name="required-options"></a>Options obligatoires  
 Vous pouvez spécifier **Console** seulement sur une ligne de commande qui contient aussi l’option **Launch**.  
  
 **Launch:** `AppName`  
 Démarre le profileur et l'application spécifiée par `AppName`.  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)