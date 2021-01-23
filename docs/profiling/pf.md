---
title: PF | Microsoft Docs
description: Découvrez comment l’option VSPerfCmd.exe PF définit l’événement de profilage qui est échantillonné sur les défauts de page et modifie le nombre de défauts de page dans un intervalle d’échantillonnage.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b920b641a7bfc4583af7b0ec5a9692a25c19adb5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719550"
---
# <a name="pf"></a>PF
L’option *VSPerfCmd.exe* **PF** définit l’événement de profilage qui est échantillonné sur les défauts de page et, éventuellement, modifie le nombre de défauts de page dans un intervalle d’échantillonnage à partir de la valeur par défaut de 10.

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

 **Lancer :** `AppName` Démarre le profileur et l’application spécifiée par AppName.

 **Attacher :** `PID` Attache le profileur au processus spécifié par AppName.

## <a name="invalid-options"></a>Options non valides
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **PF**.

 **Timer**[**:** `Cycles` ] définit l’événement d’échantillonnage sur les cycles d’horloge du processeur et définit éventuellement l’intervalle d’échantillonnage sur `Cycles` . L’intervalle de Timer par défaut est 10,000,000.

 **Sys**[**:** `Events` ] définit l’événement d’échantillonnage sur les appels de l’application profilée au noyau du système d’exploitation (syscalls) et définit éventuellement l’intervalle d’échantillonnage sur `Events` . L'intervalle Sys par défaut est 10.

 **Compteur :** `Name` [ `,Reload` [ `,FriendlyName` ]] Définit l’événement d’échantillonnage sur le compteur de performance de l’UC spécifié par `Name` et définit l’intervalle d’échantillonnage sur `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Collecte les données de mémoire .NET. Par défaut (**allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Quand le paramètre **Lifetime** est spécifié, les données sont également collectées à chaque événement garbage collection.

## <a name="example"></a>Exemples
 Cet exemple montre comment définir l’événement d’échantillonnage du profilage sur les défauts de page, et comment définir l’intervalle d’échantillonnage sur 20 défauts de page.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /PF:20
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
