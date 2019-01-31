---
title: GlobalOn et GlobalOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fc5a353b87d8dbe945e73d828269c38b18274a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961648"
---
# <a name="globalon-and-globaloff"></a>GlobalOn et GlobalOff
Les options **GlobalOff** et **GlobalOn** de *VSPerfCmd.exe* suspendent et reprennent le profilage pour tous les processus et threads dans une session de profilage en ligne de commande.  
  
 Vous pouvez spécifier **GlobalOn** et **GlobalOff** comme uniques options sur une ligne de commande *VSPerfCmd.exe*, ou vous pouvez les inclure sur des lignes de commande qui contiennent aussi les options **Start**, **Launch** ou **Attach**.  
  
 Vous pouvez aussi combiner **GlobalOn** et **GlobalOff** avec les options **ProcessOn**, **ProcessOff**, **ThreadOn** et **ThreadOff**.  
  
 Les options **GlobalOn** et **GlobalOff** interagissent avec les options **ProcessOn** et **ProcessOff** qui contrôlent la collecte de données pour un processus spécifié, et avec les options **ThreadOn** et **ThreadOff** qui contrôlent la collecte de données pour un thread spécifié.  
  
 Les options **GlobalOff** et **GlobalOn** affectent également le nombre Start/Stop global manipulé par les fonctions d’API du profileur.  
  
- **GlobalOff** affecte immédiatement la valeur 0 au Nombre Start/Stop global et suspend ainsi le profilage.  
  
- **GlobalOff** affecte immédiatement la valeur 1 au Nombre Start/Stop global et reprend ainsi le profilage.  
  
  Pour plus d’informations, consultez [API des outils de profilage](../profiling/profiling-tools-apis.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn}[Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="valid-options"></a>Options valides  
 Vous pouvez spécifier **GlobalOn** et **GlobalOff** sur des lignes de commande qui contiennent également les options suivantes.  
  
 **Start :** `Method`  
 Initialise la session de profileur en ligne de commande et définit la méthode de profilage spécifiée.  
  
 **Launch :** `AppName`  
 Démarre l’application spécifiée et commence le profilage avec la méthode d’échantillonnage.  
  
 **Attach :** `PID`  
 Démarre le profilage du processus spécifié.  
  
 {**ProcessOff**&#124;**ProcessOn**}  **:**`PID`  
 Arrête ou démarre le profilage du processus spécifié.  
  
 {**ThreadOff**&#124;**ThreadOn**}  **:**`TID`  
 Arrête ou démarre le profilage du processus spécifié (méthode d’instrumentation uniquement).  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, les options **GlobalOff** et **GlobalOn** permettent d’éviter la collecte de données de profilage pour le démarrage et l’arrêt de l’application.  
  
```cmd  
; Initialize the profiler with profiling stopped.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff  
; Start an instrumented application and wait for it to warm up.  
; Start profiling.  
VSPerfCmd.exe /GlobalOn  
; Exercise the application functionality that you want to profile.  
; Stop profiling.  
VSPerfCmd.exe /GlobalOff  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)