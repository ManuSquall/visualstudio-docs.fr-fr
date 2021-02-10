---
title: CrossSession | Microsoft Docs
description: Découvrez comment utiliser l’option VSPerfCmd.exe CrossSession pour permettre au profileur de collecter des données à partir d’une session de console. Vous devez également spécifier l’option Start.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a52acb80bac511706086c56074eb5bfe450b7674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955903"
---
# <a name="crosssession"></a>CrossSession
L’option *VSPerfCmd.exe* **CrossSession** permet au profileur de collecter des données de n’importe quelle session console. L’option **CrossSession** doit être utilisée avec l’option **Start**.

 Vous pouvez utiliser l’abréviation **CS** à la place de **CrossSession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Paramètres
 None

## <a name="valid-options"></a>Options valides
 Pour activer le profilage dans une autre session, l’option **CrossSession** doit être spécifiée avec l’option **Start**. L’option **CrossSession** doit également être spécifiée dans toutes les commandes **VSPerfCmd Attach** et **Detach** suivantes.

 **Démarrer :** `Method` L’option **Start** Initialise le profileur avec la méthode de profilage spécifiée.

 **Attach :** _PID_[**,**_PID_] commence le profilage des processus spécifiés.

 **Detach**[**:**_PID_[,_PID_]] Arrête le profilage des processus spécifiés.

## <a name="example"></a>Exemple
 Dans cet exemple, l’option **CrossSession** est utilisée pour attacher à une application qui a été démarrée dans une autre session de console.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
