---
title: Timer | Microsoft Docs
description: Découvrez comment l’option de minuterie VSPerfCmd.exe définit l’événement de profilage qui est échantillonné aux cycles d’horloge du processeur.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3aeffc3be3fee5d3460ddea340d8c4a216829e08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963157"
---
# <a name="timer"></a>Minuteur
L’option de **minuterie** *VSPerfCmd.exe* définit l’événement de profilage qui est échantillonné aux cycles d’horloge du processeur et modifie éventuellement le nombre de cycles dans un intervalle d’échantillonnage à partir de la valeur par défaut 10 millions. Sur un processeur d'1 GHz (un gigahertz), 10 000 000 de cycles d'horloge correspondent environ à 100 échantillons par seconde. Vous pouvez spécifier au minimum 50 000 cycles.

 **Timer** peut être utilisé seulement quand vous utilisez la méthode de profilage par échantillonnage, et seulement sur une ligne de commande qui contient aussi l’option **Launch** ou **Attach**.

 Par défaut, l'événement d'échantillonnage du profileur est défini sur les cycles d'horloge du processeur et l'intervalle d'échantillonnage est défini sur 10 000 000. Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l’événement d’échantillonnage et l’intervalle d’échantillonnage. L’option **GC** collecte les données de mémoire .NET à chaque événement d’allocation et de garbage collection. Vous ne pouvez spécifier qu'une seule de ces options sur une ligne de commande.

 Vous pouvez définir l’événement d’échantillonnage et l’intervalle d’échantillonnage seulement sur la première ligne de commande qui contient une option **Launch** ou **Attach**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]
```

#### <a name="parameters"></a>Paramètres
 `Cycles` Valeur entière qui spécifie le nombre de cycles d’horloge du processeur dans un intervalle d’échantillonnage. Si `Cycles` n'est pas spécifié, l'intervalle prend la valeur 10 000 000. Spécifiez la valeur sans espace.

## <a name="required-options"></a>Options obligatoires
 Vous pouvez spécifier **Timer** seulement sur une ligne de commande qui contient une des options suivantes.

 **Lancer :** `AppName` Démarre le profileur et l’application spécifiée par `AppName` .

 **Attacher :** `PID` Attache le profileur au processus spécifié par l’ID de processus ( `PID` ).

## <a name="invalid-options"></a>Options non valides
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **Timer**.

 **PF**[**:** `Events` ] définit l’événement d’échantillonnage sur les défauts de page et définit éventuellement l’intervalle d’échantillonnage sur `Events` . L'intervalle de défaut de page par défaut est 10.

 **Sys**[**:** `Events` ] définit l’événement d’échantillonnage sur les appels du système d’exploitation et définit éventuellement l’intervalle d’échantillonnage sur `Events` . L'intervalle Sys par défaut est 10.

 **Counter**[**:** `Name,Reload,FriendlyName` ] définit l’événement d’échantillonnage sur le compteur de performance de l’UC spécifié par `Name` et définit l’intervalle d’échantillonnage sur `Reload` .

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Collecte les données de mémoire .NET. Par défaut (**allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Quand le paramètre **Lifetime** est spécifié, les données sont également collectées à chaque événement garbage collection.

## <a name="example"></a>Exemple
 Cet exemple illustre comment définir l'intervalle d'échantillonnage du profileur sur 1 000 000 de cycles du processeur.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
