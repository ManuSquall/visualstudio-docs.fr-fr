---
title: Shutdown | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29f6ab4b750370467fa75c2341e20264db756a7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979885"
---
# <a name="shutdown"></a>Éteindre
L’option **Shutdown** attend que les processus en cours de profilage se terminent ou se détachent, puis désactive le profileur et ferme le fichier de données de profilage. L’option **Shutdown** doit être la dernière commande d’une exécution de profilage.

 Si aucun paramètre de délai d’expiration n’est spécifié, l’option **Shutdown** attend indéfiniment. Si un paramètre de délai d’expiration est spécifié, l’option retourne après le nombre de secondes spécifié sans désactiver le profileur ni fermer le fichier de données.

 L’option **Shutdown** doit être la seule option spécifiée sur la ligne de commande.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>Paramètres
`Timeout`
- (Facultatif) Si elle est spécifiée, l’option retourne après le nombre de secondes spécifié sans désactiver le profileur ni fermer le fichier de données de profilage.

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)