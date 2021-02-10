---
title: Problèmes de sécurité | Microsoft Docs
description: Découvrez les autorisations nécessaires pour déboguer un programme à l’aide de Visual Studio, notamment le débogage à distance et les situations qui impliquent d’autres services.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e7b834dc41fb019e70aa40bca995770985d4c05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960921"
---
# <a name="security-issues"></a>Problèmes de sécurité
Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessaires sont les mêmes que celles requises par un développeur pour exécuter le programme. Cela comprend le débogage à distance pour la plupart des situations. Certaines situations, impliquant d’autres services, tels que Internet Information Service, peuvent nécessiter un niveau d’autorisations plus élevé.

 Pendant que Visual Studio est en cours d’exécution, le gestionnaire de débogage de processus (PDM) effectue le suivi des processus de débogage sur l’ordinateur local. À distance, un programme appelé *msvsmon.exe* est démarré par le développeur pour gérer le débogage distant et rendre le PDM disponible. (*msvsmon.exe* n’est pas un service et doit être démarré manuellement pour activer le débogage à distance sur cet ordinateur.) Lorsque Visual Studio (ou *msvsmon.exe*) n’est pas en cours d’exécution, aucun processus n’est suivi pour le débogage.

 Un développeur peut déboguer les programmes qu’il a démarrés sans autorisations spéciales. Le développeur peut même déboguer les processus démarrés par quelqu’un d’autre si cette personne est membre du même groupe de sécurité. Et, pour activer le débogage distant, il est nécessaire uniquement de copier les fichiers requis sur l’ordinateur distant et de démarrer *msvsmon.exe*. Pour plus d’informations, consultez [débogage distant](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [Gestionnaire de débogage de processus](../../extensibility/debugger/process-debug-manager.md)
- [Débogage distant](../../debugger/remote-debugging.md)
