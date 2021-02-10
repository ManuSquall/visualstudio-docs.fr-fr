---
title: ThreadOn et ThreadOff | Microsoft Docs
description: Découvrez comment les sous-commandes VSPerfCmd.exe ThreadOff et ThreadOn sont uniquement disponibles dans les sessions de profilage en ligne de commande qui utilisent la méthode d’instrumentation.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 059e7dfc9d7c16be3aa699eea47b1a64882e689e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949309"
---
# <a name="threadon-and-threadoff"></a>ThreadOn et ThreadOff
Les *VSPerfCmd.exe* sous-commandes **ThreadOff** et **ThreadOn** ne sont disponibles que dans les sessions de profilage en ligne de commande qui utilisent la méthode d’instrumentation. **ThreadOff** et **ThreadOn** suspendent et reprennent le profilage du thread spécifié. **ThreadOff** arrête le profilage du thread et **ThreadOn** démarre le profilage du thread.

 Dans la plupart des cas, vous spécifiez **ThreadOn** ou **ThreadOff** comme seule option dans une ligne de commande *VSPerfCmd.exe* , mais elles peuvent également être combinées avec les sous-commandes **GlobalOn**, **globaloff**, **ProcessOn** et **ProcessOff** .

 Les sous-commandes **ThreadOn** et **ThreadOff** interagissent avec les sous-commandes **GlobalOn** et **GlobalOff**, qui contrôlent la collecte de données de tous les processus d’une session de profilage en ligne de commande, et avec les sous-commandes **ProcessOn** et **ProcessOff**, qui contrôlent la collecte de données d’un processus spécifié.

 Les sous-commandes **ThreadOff** et **ThreadOn** affectent également le nombre de Start/Stop du thread qui est manipulé par les fonctions d’API du profileur.

- **ThreadOff** affecte immédiatement la valeur 0 au nombre de Start/Stop global et suspend ainsi le profilage.

- **ThreadOn** affecte immédiatement la valeur 1 au nombre de Start/Stop du thread et reprend ainsi le profilage.

  Pour plus d’informations, consultez [API des outils de profilage](../profiling/profiling-tools-apis.md).

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]

```

#### <a name="parameters"></a>Paramètres
 `TID` Identificateur sous forme d’entier du thread à démarrer ou à arrêter.

## <a name="valid-options"></a>Options valides
 Vous pouvez spécifier **ThreadOn** et **ThreadOff** sur des lignes de commande qui contiennent également les sous-commandes suivantes.

 **Démarrer :** `Method` Initialise la session de profilage en ligne de commande et définit la méthode de profilage spécifiée.

 **GlobalOff**&#124;**GlobalOn** Arrête ou démarre le profilage de tous les processus d’une session de profilage en ligne de commande.

 {**ProcessOff**&#124;**ProcessOn**} **:**`TID` Arrête ou démarre le profilage pour le processus spécifié.

## <a name="example"></a>Exemple
 Dans cet exemple, la sous-commande **ThreadOff** est utilisée pour arrêter la collecte de données de profilage et collecter seulement les données de démarrage de l’application.

```cmd
; Initialize the profiler.
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp
; Start the instrumented application.
; Stop profiling the thread after startup.
VSPerfCmd.exe /ThreadOff:12345
; Shut down the target application.
; Close the profiler.
VSPerfCmd /Shutdown

```

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
