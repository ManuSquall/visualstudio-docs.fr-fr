---
title: PF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07ec6d636ec087386fdc9462ae09db55400957a9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778412"
---
# <a name="pf"></a>PF
*L’option VSPerfCmd.exe* **PF** définit l’événement de profilage qui est échantillonné pour les défauts de page, et il modifie optionnellement le nombre de défauts de page dans un intervalle d’échantillonnage de la valeur par défaut de 10.

> [!NOTE]
> Vous ne pouvez pas utiliser **PF** sur les systèmes 64 bits.

Vous pouvez utiliser **PF** seulement sur une ligne de commande qui contient aussi l’option **Launch** ou **Attach**.

 Par défaut, l’événement d’échantillonnage du profileur est défini sur les cycles d’horloge du processeur hors interruption, et l’intervalle d’échantillonnage est défini sur 10 000 000. Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l’événement d’échantillonnage et l’intervalle d’échantillonnage. L’option **GC** collecte les données de mémoire .NET à chaque événement d’allocation et de garbage collection. Vous ne pouvez spécifier qu'une seule de ces options sur une ligne de commande.

 Vous pouvez définir l’événement d’échantillonnage et l’intervalle d’échantillonnage seulement sur la première ligne de commande qui contient une option **Launch** ou **Attach**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]
```

#### <a name="parameters"></a>Paramètres
 `Events` Valeur entière qui spécifie le nombre d’événements de défaut de page dans un intervalle d’échantillonnage. Si `Events` n’est pas spécifié, l’intervalle est défini sur 10.

## <a name="required-options"></a>Options obligatoires
 Vous pouvez spécifier **PF** seulement sur une ligne de commande qui contient une des options suivantes.

 **Lancement :** `AppName` Démarre le profileur et l’application spécifiée par AppName.

 **Attachez :** `PID` Attache le profileur au processus spécifié par AppName.

## <a name="invalid-options"></a>Options non valides
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **PF**.

 **Timer**[**:**`Cycles`] définit l’événement d’échantillonnage aux `Cycles`cycles d’horloge du processeur et définit l’intervalle d’échantillonnage à . L’intervalle de Timer par défaut est 10,000,000.

 **Sys**[**:**`Events`] définit l’événement d’échantillonnage aux appels de l’application profilée au noyau du `Events`système d’exploitation (syscalls) et définit en option l’intervalle d’échantillonnage à . L'intervalle Sys par défaut est 10.

 **Compteur:** `Name``,Reload`[`,FriendlyName`[ ] Définit l’événement d’échantillonnage `Name` au compteur de `Reload`performance de processeur spécifié par et définit l’intervalle d’échantillonnage à .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Collecte les données de mémoire .NET. Par défaut **(Allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Lorsque le **paramètre à vie** est spécifié, les données sont également recueillies lors de chaque événement de collecte des ordures.

## <a name="example"></a> Exemple
 Cet exemple montre comment définir l’événement d’échantillonnage du profilage sur les défauts de page, et comment définir l’intervalle d’échantillonnage sur 20 défauts de page.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Voir aussi
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET applications Web](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
