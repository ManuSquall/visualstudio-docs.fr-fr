---
title: Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 634169607a7d581de1b1332d78e8d5abde1a722e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773737"
---
# <a name="attach"></a>Joindre
*L’option VSPerfCmd.exe* **Attach** commence le profilage de l’échantillon du processus d’exécution spécifié par l’ID processus (PID).

 Pour utiliser l’option **Attach**, vous devez spécifier la méthode **Sample** dans l’option Start.

> [!NOTE]
> Si l’option **Start** a été spécifiée avec l’option **Crosssession**, les appels à **VSPerfCmd /Attach** ou **VSPerfCmd /Detach** doivent également spécifier **Crosssession**.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Paramètres
 `ProcessID` PID (ID de processus) du processus en cours d’exécution. Le PID d’un processus en cours d’exécution est répertorié sous l’onglet Processus du Gestionnaire des tâches de Windows.

## <a name="valid-options"></a>Options valides
 Les options suivantes de **VSPerfCmd** peuvent être combinées avec l’option **Attach** sur une même ligne de commande.

 **Crosssession** Active le profilage d’applications dans d’autres sessions que l’ouverture de session. Obligatoire si l’option **Start** a été spécifiée avec l’option **Crosssession**.

 **Démarrage :** `Method` Initialise la session de profileur de ligne de commande et définit la méthode de profilage spécifiée.

 **TargetCLR** Spécifie la version du CLR (Common Language Runtime) du .NET Framework à profiler quand plusieurs versions sont chargées dans une session de profilage. Par défaut, la première version chargée est profilée.

 **GlobalOn GlobalOff** Reprend (**GlobalOn**) ou interrompt (**GlobalOff**) le profilage, mais ne met pas fin à la session de profilage.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Resumes (**ProcessOn**) ou pauses (**ProcessOff**) profilage pour le processus spécifié.

## <a name="interval-options"></a>Options pour l’intervalle
 Une des options d’intervalle d’échantillonnage suivantes peut être spécifiée sur la ligne de commande d’Attach. L’intervalle d’échantillonnage par défaut est de 10 000 000 de cycles d’horloge du processeur.

 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**`FriendlyName`[<strong>:</strong>Events]**Counter****[:**`Name`,`Reload`, ] Specifie le nombre et le type de l’intervalle d’échantillonnage.

- **Timer** : échantillonne tous les `Cycles` cycles d’horloge du processeur. Si `Cycles` n’est pas spécifié, la valeur utilisée est de 10 000 000 cycles.

- **PF** : échantillonne tous les `Events` défauts de page. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 défauts de page.

- **Sys** : échantillonne tous les `Events` appels au système d’exploitation. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 appels système.

- **Counter** : échantillonne tous les nombres de `Reload` du compteur de performance de l’UC spécifié par `Name`. En option, `FriendlyName` peut spécifier une chaîne à utiliser comme en-tête de colonne dans les rapports du profileur.

## <a name="example"></a> Exemple
 Cet exemple montre comment s’attacher à une instance en cours d’exécution d’une application avec l’ID de processus 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Voir aussi
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET applications Web](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
