---
title: Timer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1bed2715421948385a5b7eb1ddbbac064f3288b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778113"
---
# <a name="timer"></a>Minuterie
*L’option VSPerfCmd.exe* **Timer** définit l’événement de profilage qui est échantillonné aux cycles d’horloge du processeur et modifie d’option le nombre de cycles dans un intervalle d’échantillonnage par défaut de 10 000 000. Sur un processeur d'1 GHz (un gigahertz), 10 000 000 de cycles d'horloge correspondent environ à 100 échantillons par seconde. Vous pouvez spécifier au minimum 50 000 cycles.

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

 **Lancement:** `AppName` Démarre le profileur et `AppName`l’application spécifiée par .

 **Attacher :** `PID` Attache le profileur au processus spécifié`PID`par l’ID du processus ().

## <a name="invalid-options"></a>Options non valides
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **Timer**.

 **PF**[**:**`Events`] Définit l’événement d’échantillonnage aux `Events`défauts de page et définit l’intervalle d’échantillonnage à . L'intervalle de défaut de page par défaut est 10.

 **Sys**[**:**`Events`] définit l’événement d’échantillonnage aux `Events`appels du système d’exploitation et définit l’intervalle d’échantillonnage à . L'intervalle Sys par défaut est 10.

 **Compteur**[**:**`Name,Reload,FriendlyName`] définit l’événement d’échantillonnage au compteur de performance de processeur spécifié par `Name` et définit l’intervalle d’échantillonnage à `Reload`.

 **GC**[**:**{**Allocation**&#124;**Lifetime**}] Collecte les données de mémoire .NET. Par défaut **(Allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Lorsque le **paramètre à vie** est spécifié, les données sont également recueillies lors de chaque événement de collecte des ordures.

## <a name="example"></a> Exemple
 Cet exemple illustre comment définir l'intervalle d'échantillonnage du profileur sur 1 000 000 de cycles du processeur.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000
```

## <a name="see-also"></a>Voir aussi
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET applications Web](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
