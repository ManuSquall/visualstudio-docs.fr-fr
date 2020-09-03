---
title: Launch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c910ef1519181f1402cbec1d31686492e30f343d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154755"
---
# <a name="launch"></a>Lancer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **Launch** démarre le profileur avec la méthode d’échantillonnage et démarre également l’application spécifiée.  
  
 Pour utiliser l’option **Launch**, vous devez spécifier la méthode **Sample** dans l’option **Start**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AppName`  
 Nom de l’application à lancer. Les chemins complets et partiels depuis le répertoire actif sont pris en charge.  
  
## <a name="valid-options"></a>Options valides  
 Les options de VSPerfCmd peuvent être combinées avec l’option **Launch** sur une même ligne de commande.  
  
 **Démarrer :**`Method`  
 Initialise la session de profileur en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **GlobalOn** et **globaloff**  
 Reprend (**GlobalOn**) ou interrompt (**GlobalOff**) le profilage, mais ne met pas fin à la session de profilage.  
  
 **ProcessOn :** `PID` et **ProcessOff**:`PID`  
 Reprend (**ProcessOn**) ou interrompt (**ProcessOff**) le profilage pour le processus spécifié.  
  
 **TargetCLR**  
 Spécifie la version du CLR de .NET Framework à profiler quand plusieurs versions sont chargées dans une session de profilage. Par défaut, la première version chargée est profilée.  
  
## <a name="exclusive-options"></a>Options exclusives  
 Les options suivantes peut être utilisée seulement avec l’option **Launch**.  
  
 **Console**  
 Lance l’application en ligne de commande spécifiée dans une nouvelle fenêtre.  
  
 **Arguments :**`ArgList`  
 Spécifie la liste des arguments à passer à l’application.  
  
 **LineOff**  
 Désactive la collecte des données de profilage au niveau des lignes.  
  
## <a name="sampling-options"></a>Options d’échantillonnage  
 Une des options d’intervalle d’échantillonnage suivantes peut être spécifiée sur la ligne de commande **Launch**. L’intervalle d’échantillonnage par défaut est de 10 000 000 de cycles d’horloge du processeur.  
  
 **Timer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[**:** `Events` ]**Counter**[**:** `Name` , `Reload` , `FriendlyName` ]**GC**[ :**allocation**&#124;**durée de vie**]  
 Spécifie la valeur et le type de l’intervalle d’échantillonnage.  
  
- **Timer** : échantillonne tous les `Cycles` cycles d’horloge du processeur sans interruption. Si `Cycles` n’est pas spécifié, la valeur utilisée est de 10 000 000 cycles.  
  
- **PF** : échantillonne tous les `Events` défauts de page. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 défauts de page.  
  
- **Sys** : échantillonne tous les `Events` appels au système d’exploitation. Si `Events` n’est pas spécifié, la valeur utilisée est de 10 appels système.  
  
- **Counter** : échantillonne tous les nombres de `Reload` du compteur de performance de l’UC spécifié par `Name`. En option, `FriendlyName` peut spécifier une chaîne à utiliser comme en-tête de colonne dans les rapports du profileur.  
  
- **GC** : collecte les données de mémoire .NET. Par défaut (**allocation**), les données sont collectées à chaque événement d’allocation de mémoire. Quand le paramètre **lifetime** est spécifié, les données sont également collectées à chaque événement de garbage collection.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre l’utilisation de **Launch** pour démarrer une application.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Option](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage des services](../profiling/command-line-profiling-of-services.md)
