---
title: PF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a7911a505494c3af0c047208660671ec3f5a8c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="pf"></a>PF
L’option **PF** de VSPerfCmd.exe définit l’événement de profilage qui est échantillonné lors des défauts de page. Elle peut changer le nombre de défauts de page dans un intervalle d’échantillonnage (la valeur par défaut est 10).  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser PF sur les systèmes 64 bits.  
  
 **Notez que PF** n’est pas pris en charge sur les ordinateurs 64 bits. **PF** peut être utilisé seulement dans une ligne de commande qui contient également l’option **Launch** ou **Attach**.  
  
 Par défaut, l’événement d’échantillonnage du profileur est défini sur les cycles d’horloge du processeur hors interruption, et l’intervalle d’échantillonnage est défini sur 10 000 000. Les options **Timer**, **PF**, **Sys** et **Counter** vous permettent de définir l’événement d’échantillonnage et l’intervalle d’échantillonnage. L’option **GC** collecte les données de mémoire .NET à chaque événement d’allocation et de garbage collection. Vous ne pouvez spécifier qu'une seule de ces options sur une ligne de commande.  
  
 Vous pouvez définir l’événement d’échantillonnage et l’intervalle d’échantillonnage seulement sur la première ligne de commande qui contient une option **Launch** ou **Attach**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Events`  
 Valeur entière qui spécifie le nombre d’événements de défaut de page dans un intervalle d’échantillonnage. Si `Events` n’est pas spécifié, l’intervalle est défini sur 10.  
  
## <a name="required-options"></a>Options obligatoires  
 Vous pouvez spécifier **PF** seulement sur une ligne de commande qui contient une des options suivantes.  
  
 **Launch:** `AppName`  
 Démarre le profileur et l’application spécifiée par AppName.  
  
 **Attach:** `PID`  
 Attache le profileur au processus spécifié par AppName.  
  
## <a name="invalid-options"></a>Options non valides  
 Vous ne pouvez pas spécifier les options suivantes sur la même ligne de commande que **PF**.  
  
 **Timer**[**:**`Cycles`]  
 Définit l’événement d’échantillonnage sur les cycles d’horloge du processeur et définit éventuellement l’intervalle d’échantillonnage sur `Cycles`. L’intervalle de Timer par défaut est 10,000,000.  
  
 **Sys**[**:**`Events`]  
 Définit l’événement d’échantillonnage comme étant des appels de l’application profilée au noyau du système d’exploitation (syscalls), et définit éventuellement l’intervalle d’échantillonnage sur `Events`. L'intervalle Sys par défaut est 10.  
  
 **Counter:** `Name`[`,Reload`[`,FriendlyName`]]  
 Définit l'événement d'échantillonnage sur le compteur de performance d'UC spécifié par `Name` et définit l'intervalle d'échantillonnage sur `Reload`.  
  
 **GC**[**:**{**Allocation**&#124;**Lifetime**}]  
 Recueille des données de mémoire .NET. Par défaut (**Allocation**), les données sont collectées à chaque événement d’allocation mémoire. Quand le paramètre **Lifetime** est spécifié, les données sont aussi collectées à chaque événement de garbage collection.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment définir l’événement d’échantillonnage du profilage sur les défauts de page, et comment définir l’intervalle d’échantillonnage sur 20 défauts de page.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)