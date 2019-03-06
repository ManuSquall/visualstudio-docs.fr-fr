---
title: Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c5c734d4d0b12bea1e13ac216700be5f85ed088
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627335"
---
# <a name="attach"></a>Attach
L’option **Attach** de *VSPerfCmd.exe* démarre le profilage par échantillonnage du processus en cours d’exécution spécifié par le PID (ID de processus).

 Pour utiliser l’option **Attach**, vous devez spécifier la méthode **Sample** dans l’option Start.

> [!NOTE]
>  Si l’option **Start** a été spécifiée avec l’option **Crosssession**, les appels à **VSPerfCmd /Attach** ou **VSPerfCmd /Detach** doivent également spécifier **Crosssession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Paramètres
 `ProcessID` PID (ID de processus) du processus en cours d’exécution. Le PID d’un processus en cours d’exécution est répertorié sous l’onglet Processus du Gestionnaire des tâches de Windows.

## <a name="valid-options"></a>Options valides
 Les options suivantes de **VSPerfCmd** peuvent être combinées avec l’option **Attach** sur une même ligne de commande.

 **Crosssession** Active le profilage d’applications dans d’autres sessions que l’ouverture de session. Obligatoire si l’option **Start** a été spécifiée avec l’option **Crosssession**.

 **Start :** `Method` Initialise la session de profilage en ligne de commande, et définit la méthode de profilage spécifiée.

 **TargetCLR** Spécifie la version du CLR (Common Language Runtime) du .NET Framework à profiler quand plusieurs versions sont chargées dans une session de profilage. Par défaut, la première version chargée est profilée.

 **GlobalOn GlobalOff** Reprend (**GlobalOn**) ou interrompt (**GlobalOff**) le profilage, mais ne met pas fin à la session de profilage.

 **ProcessOn :** `PID` **ProcessOff:** `PID` Reprend (**ProcessOn**) ou interrompt (**ProcessOff**) le profilage pour le processus spécifié.

## <a name="interval-options"></a>Options pour l’intervalle
 Une des options d’intervalle d’échantillonnage suivantes peut être spécifiée sur la ligne de commande d’Attach. L’intervalle d’échantillonnage par défaut est de 10 000 000 de cycles d’horloge du processeur.

 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[<strong>:</strong>Events]**Counter**[**:**`Name`,`Reload`,`FriendlyName`] Spécifie le nombre et le type de l’intervalle d’échantillonnage.

-   **Timer** : échantillonne tous les `Cycles` cycles d’horloge du processeur. Si `Cycles` n’est pas spécifié, la valeur utilisée est de 10 000 000 cycles.

-   **PF** : échantillonne tous les `Events` défauts de page. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 défauts de page.

-   **Sys** : échantillonne tous les `Events` appels au système d’exploitation. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 appels système.

-   **Counter** : échantillonne tous les nombres de `Reload` du compteur de performance de l’UC spécifié par `Name`. En option, `FriendlyName` peut spécifier une chaîne à utiliser comme en-tête de colonne dans les rapports du profileur.

## <a name="example"></a>Exemple
 Cet exemple montre comment s’attacher à une instance en cours d’exécution d’une application avec l’ID de processus 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)