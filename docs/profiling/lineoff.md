---
title: LineOff | Microsoft Docs
description: Découvrez comment l’option LineOff de VSPerfCmd désactive la collecte des données de numéro de ligne lorsque VSPerfCmd est utilisé pour démarrer l’application.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a141e713dd03f99db6ce47224c64236a0219cdd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917901"
---
# <a name="lineoff"></a>LineOff
Par défaut, le profileur collecte le numéro de ligne du code source et le décalage de numéro de ligne quand vous utilisez la méthode de profilage par échantillonnage. L’option **LineOff** de VSPerfCmd désactive la collecte des numéros de ligne quand VSPerfCmd est utilisé pour démarrer l’application. Les données de profilage sont collectées au niveau de la fonction quand **LineOff** est spécifié.

 Vous pouvez utiliser **LineOff** seulement avec l’option **Launch**, et seulement quand le profileur a été initialisé pour l’échantillonnage avec l’option **Start**:**Sample**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Paramètres
 None

## <a name="required-options"></a>Options obligatoires
 L’option **LineOff** peut être utilisée seulement sur une ligne de commande qui contient l’option **Launch**.

 **Lancer :** `AppName` Démarre l’application spécifiée et commence le profilage à l’aide de la méthode d’échantillonnage.

## <a name="example"></a>Exemple
 Cet exemple démarre l’application et le profileur, et désactive l’échantillonnage au niveau des lignes.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
