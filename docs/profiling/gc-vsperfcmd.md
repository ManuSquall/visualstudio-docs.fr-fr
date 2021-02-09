---
title: GC (VSPerfCmd) | Microsoft Docs
description: Passez en revue l’option GC dans l’outil VSPerfCmd.exe. L’option GC active la collecte des données d’allocation mémoire et de durée de vie des objets de .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bc1c215359f6b891239cd7b39f33d412bbf40dd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907344"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
L’option **GC** active la collecte des données d’allocation mémoire et de durée de vie des objets de .NET Framework. L’option **GC** peut être utilisée seulement avec la méthode de profilage par échantillonnage et seulement avec l’option **Launch**.

 Quand vous utilisez l’option **GC**, la commande VSPerfClrEnv **/sampleon** n’est pas obligatoire.

 Si aucun paramètre n’est spécifié, ou si le paramètre **Allocation** est spécifié, seules les données d’allocation mémoire de .NET Framework sont collectées. Si le paramètre **Lifetime** est spécifié, les données d’allocation mémoire de .NET Framework et de durée de vie des objets de .NET Framework sont collectées.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Paramètres
 **Allocation** Valeur par défaut. Collecte les données d’allocation mémoire de .NET Framework.

 **Lifetime** Collecte les données d’allocation de mémoire du .NET Framework et les données de durée de vie des objets du .NET Framework.

## <a name="required-options"></a>Options obligatoires
 L’option **GC** peut être utilisée seulement avec l’option **Launch**.

 **Lancer :** `AppName` Démarre l’application spécifiée et commence le profilage à l’aide de la méthode d’échantillonnage.

## <a name="example"></a>Exemple
 L’exemple suivant lance une application et collecte les données d’allocation mémoire de .NET Framework.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
