---
title: Questions de sécurité (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713048"
---
# <a name="security-issues"></a>Problèmes de sécurité
Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessaires sont les mêmes qu’un développeur a besoin pour exécuter le programme. Cela comprend le débogage à distance pour la plupart des situations. Certaines situations, impliquant d’autres services, comme le Service d’information Sur Internet, peuvent nécessiter un niveau plus élevé d’autorisations.

 Pendant que Visual Studio est en cours d’exécution, le gestionnaire de déboguer le processus (PDM) suit les processus de déboguer sur la machine locale. À distance, un programme appelé *msvsmon.exe* est lancé par le développeur pour gérer le débogage à distance et rendre le PDM disponible. (*msvsmon.exe* n’est pas un service et doit être commencé manuellement pour permettre le débogage à distance sur cette machine.) Lorsque Visual Studio (ou *msvsmon.exe*) n’est pas en cours d’exécution, aucun processus n’est suivi pour débogage.

 Un développeur peut déboiffer les programmes qu’ils ont commencé sans autorisations spéciales. Le développeur peut même déboiffer les processus lancés par quelqu’un d’autre si cette autre personne est membre du même groupe de sécurité. Et, pour permettre le débogage à distance, il est nécessaire seulement de copier les fichiers requis à la machine à distance et de démarrer *msvsmon.exe*. Pour plus d’informations, voir [Débugging à distance](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [Gestionnaire de débogé de processus](../../extensibility/debugger/process-debug-manager.md)
- [Débogage à distance](../../debugger/remote-debugging.md)
