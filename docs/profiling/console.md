---
title: Console | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7fb90261453caab8dbe54fce79605c1d891d537
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2018
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
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)