---
title: Args | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b6d01a95b7e0872d6bb36c6d9f3917bc6a05b3b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779816"
---
# <a name="args"></a>Args
L’option **Args** de VSPerfCmd.exe spécifie la liste des arguments qui sont passés à l’application cible de la sous-commande **Launch**.

 **Args** ne peut être utilisé que si **Launch** est également spécifié sur la ligne de commande. **Args** est facultatif lorsque **Launch** est spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Paramètres
 `Arguments`Une liste d’arguments à l’application cible de la commande **de lancement.**

## <a name="required-options"></a>Options obligatoires
 **Lancement :** `AppName` Démarre l’application spécifiée et commence à profiler avec la méthode d’échantillonnage.

## <a name="example"></a> Exemple
 L’exemple suivant utilise l’option **Args** pour passer des arguments à TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Voir aussi
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Services de profilage](../profiling/command-line-profiling-of-services.md)
