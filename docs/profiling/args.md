---
title: Args | Microsoft Docs
description: Utilisez l’option ARGS de VSPerfCmd.exe pour passer une liste d’arguments à l’application cible de la sous-commande Launch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44e68822ebd444b8683b85b2df0c49b14d78bcaa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901068"
---
# <a name="args"></a>Args
L’option **Args** de VSPerfCmd.exe spécifie la liste des arguments qui sont passés à l’application cible de la sous-commande **Launch**.

 **Args** ne peut être utilisé que si **Launch** est également spécifié sur la ligne de commande. **Args** est facultatif lorsque **Launch** est spécifié.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Paramètres
 `Arguments` Liste d’arguments pour l’application cible de la commande **Launch** .

## <a name="required-options"></a>Options obligatoires
 **Lancer :** `AppName` Démarre l’application spécifiée et commence le profilage à l’aide de la méthode d’échantillonnage.

## <a name="example"></a>Exemple
 L’exemple suivant utilise l’option **Args** pour passer des arguments à TestApp.exe.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilage d’applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilage de services](../profiling/command-line-profiling-of-services.md)
