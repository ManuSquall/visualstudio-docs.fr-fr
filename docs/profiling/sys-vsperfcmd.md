---
title: Sys (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 435393ac536eb70f2f3f6d38b16eaab645848704
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778178"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
*L’option VSPerfCmd.exe* **Sys** définit l’événement de profilage qui est échantillonné aux événements d’appels système (appels de fonction de l’application profilée au système d’exploitation), et modifie d’option le nombre d’appels système dans un intervalle d’échantillonnage par défaut de 10.

 Vous pouvez utiliser **Sys** seulement sur une ligne de commande qui contient aussi l’option **Launch** ou **Attach**.

 Par défaut, l'événement d'échantillonnage du profileur est défini sur les cycles d'horloge du processeur et l'intervalle d'échantillonnage est défini sur 10 000 000. Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l’événement d’échantillonnage et l’intervalle d’échantillonnage. L’option **GC** collecte les données de mémoire .NET à chaque événement d’allocation et de garbage collection. Vous ne pouvez spécifier qu'une seule de ces options sur une ligne de commande.

 Vous pouvez définir l’événement d’échantillonnage et l’intervalle d’échantillonnage seulement sur la première ligne de commande qui contient une option **Launch** ou **Attach**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]
```

#### <a name="parameters"></a>Paramètres
 `Events` Valeur entière qui spécifie le nombre d’événements d’appel système dans un intervalle d’échantillonnage. Si `Events` n’est pas spécifié, l’intervalle est défini sur 10.

## <a name="required-options"></a>Options obligatoires
 **Sys** nécessite une des options suivantes.

 **Lancement:** `AppName` Démarre le profileur et `AppName`l’application spécifiée par .

 **Attacher:** `PID` Attache le profileur au `PID`processus spécifié par .

## <a name="invalid-options"></a>Options non valides
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **Sys**.

 **PF**[**:**`Events`] Définit l’événement d’échantillonnage aux `Events`défauts de page et définit l’intervalle d’échantillonnage à . L'intervalle de défaut de page par défaut est 10.

 **Timer**[**:**`Cycles`] définit l’événement d’échantillonnage aux `Cycles`cycles d’horloge du processeur et définit l’intervalle d’échantillonnage à . L’intervalle de Timer par défaut est 10,000,000.

 **Compteur:** `Name``,Reload`[`,FriendlyName`[ ] Définit l’événement d’échantillonnage `Name` au compteur de `Reload`performance de processeur spécifié par et définit l’intervalle d’échantillonnage à .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Collecte les données de mémoire .NET. Par défaut **(Allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Lorsque le **paramètre à vie** est spécifié, les données sont également recueillies lors de chaque événement de collecte des ordures.

## <a name="example"></a> Exemple
 Cet exemple montre comment définir le l’événement d’échantillonnage du profileur comme étant les appels système, et comment définir l’intervalle d’échantillonnage sur 20 appels par échantillon.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Voir aussi
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET applications Web](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
