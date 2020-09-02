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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74778178"
---
# <a name="sys-vsperfcmd"></a>Sys (VSPerfCmd)
L’option *VSPerfCmd.exe* **sys** définit l’événement de profilage qui est échantillonné aux événements d’appel système (appels de fonction de l’application profilée au système d’exploitation) et modifie éventuellement le nombre d’appels système dans un intervalle d’échantillonnage à partir de la valeur par défaut de 10.

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

 **Lancer :** `AppName` Démarre le profileur et l’application spécifiée par `AppName` .

 **Attacher :** `PID` Attache le profileur au processus spécifié par `PID` .

## <a name="invalid-options"></a>Options non valides
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **Sys**.

 **PF**[**:** `Events` ] définit l’événement d’échantillonnage sur les défauts de page et définit éventuellement l’intervalle d’échantillonnage sur `Events` . L'intervalle de défaut de page par défaut est 10.

 **Timer**[**:** `Cycles` ] définit l’événement d’échantillonnage sur les cycles d’horloge du processeur et définit éventuellement l’intervalle d’échantillonnage sur `Cycles` . L’intervalle de Timer par défaut est 10,000,000.

 **Compteur :** `Name` [ `,Reload` [ `,FriendlyName` ]] Définit l’événement d’échantillonnage sur le compteur de performance de l’UC spécifié par `Name` et définit l’intervalle d’échantillonnage sur `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Collecte les données de mémoire .NET. Par défaut (**allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Quand le paramètre **Lifetime** est spécifié, les données sont également collectées à chaque événement garbage collection.

## <a name="example"></a>Exemple
 Cet exemple montre comment définir le l’événement d’échantillonnage du profileur comme étant les appels système, et comment définir l’intervalle d’échantillonnage sur 20 appels par échantillon.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
