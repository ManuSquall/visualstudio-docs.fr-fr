---
title: Launch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcd6a5d9008a53e1ae6cd25954d047b68e3168de
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033217"
---
# <a name="launch"></a>Lancer
L’option **Launch** démarre le profileur avec la méthode d’échantillonnage et démarre également l’application spécifiée.  
  
 Pour utiliser l’option **Launch**, vous devez spécifier la méthode **Sample** dans l’option **Start**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AppName`  
 Nom de l’application à lancer. Les chemins complets et partiels depuis le répertoire actif sont pris en charge.  
  
## <a name="valid-options"></a>Options valides  
 Les options de VSPerfCmd peuvent être combinées avec l’option **Launch** sur une même ligne de commande.  
  
 **Start:** `Method`  
 Initialise la session de profileur en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **GlobalOn** et **GlobalOff**  
 Reprend (**GlobalOn**) ou interrompt (**GlobalOff**) le profilage, mais ne met pas fin à la session de profilage.  
  
 **ProcessOn:** `PID` et **ProcessOff** :`PID`  
 Reprend (**ProcessOn**) ou interrompt (**ProcessOff**) le profilage pour le processus spécifié.  
  
 **TargetCLR**  
 Spécifie la version du CLR de .NET Framework à profiler quand plusieurs versions sont chargées dans une session de profilage. Par défaut, la première version chargée est profilée.  
  
## <a name="exclusive-options"></a>Options exclusives  
 Les options suivantes peut être utilisée seulement avec l’option **Launch**.  
  
 **Console**  
 Lance l’application en ligne de commande spécifiée dans une nouvelle fenêtre.  
  
 **Args:** `ArgList`  
 Spécifie la liste des arguments à passer à l’application.  
  
 **LineOff**  
 Désactive la collecte des données de profilage au niveau des lignes.  
  
## <a name="sampling-options"></a>Options d’échantillonnage  
 Une des options d’intervalle d’échantillonnage suivantes peut être spécifiée sur la ligne de commande **Launch**. L’intervalle d’échantillonnage par défaut est de 10 000 000 de cycles d’horloge du processeur.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**allocation**&#124;**lifetime**]  
 Spécifie la valeur et le type de l’intervalle d’échantillonnage.  
  
-   **Timer** : échantillonne tous les `Cycles` cycles d’horloge du processeur sans interruption. Si `Cycles` n’est pas spécifié, la valeur utilisée est de 10 000 000 cycles.  
  
-   **PF** : échantillonne tous les `Events` défauts de page. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 défauts de page.  
  
-   **Sys** : échantillonne tous les `Events` appels au système d’exploitation. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 appels système.  
  
-   **Counter** : échantillonne tous les nombres de `Reload` du compteur de performance de l’UC spécifié par `Name`. En option, `FriendlyName` peut spécifier une chaîne à utiliser comme en-tête de colonne dans les rapports du profileur.  
  
-   **GC** : collecte les données de mémoire .NET. Par défaut (**allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Quand le paramètre **lifetime** est spécifié, les données sont également collectées à chaque événement de garbage collection.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre l’utilisation de **Launch** pour démarrer une application.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)