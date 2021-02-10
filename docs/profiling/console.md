---
title: Console | Microsoft Docs
description: Utilisez l’option de console de VSPerfCmd.exe pour démarrer l’application spécifiée dans une nouvelle fenêtre d’invite de commandes. Vous devez l’utiliser avec l’option Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a5234c2b7368a992676e12ecbdcd5ea36219f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955409"
---
# <a name="console"></a>Console
L’option **Console** de VSPerfCmd.exe démarre l’application spécifiée dans une nouvelle fenêtre d’invite de commandes. L’option **Console** peut être utilisée seulement avec l’option **Launch** de VSPerfCmd. Si l’application n’est pas une application en ligne de commande, **Console** n’a aucun effet.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>Paramètres
 None

## <a name="required-options"></a>Options obligatoires
 Vous pouvez spécifier **Console** seulement sur une ligne de commande qui contient aussi l’option **Launch**.

 **Lancer :** `AppName` Démarre le profileur et l’application spécifiée par `AppName` .

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
