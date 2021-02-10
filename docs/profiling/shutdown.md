---
title: Shutdown | Microsoft Docs
description: Découvrez comment l’option Shutdown attend la fin ou le détachement d’un processus actuellement profilé, puis désactive le profileur et ferme le fichier de données de profilage.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 455278f7fccbc9e4f80ce4f11a167e5b433ca8ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950037"
---
# <a name="shutdown"></a>Arrêter
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
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
