---
title: Problèmes de sécurité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dc31022611d7148d2cb52182b2a10336215afdc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345615"
---
# <a name="security-issues"></a>Problèmes de sécurité
Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessitées sont les mêmes que ceux un développeur a besoin pour exécuter le programme. Cela inclut le débogage distant pour la plupart des situations. Certaines situations impliquant d’autres services, tels que le Service d’informations Internet, peuvent nécessiter un niveau plus élevé d’autorisations.

 Pendant l’exécution de Visual Studio, le Gestionnaire de débogage de processus (PDM) effectue le suivi de déboguer des processus sur l’ordinateur local. À distance, un programme appelé *msvsmon.exe* est démarré par le développeur pour gérer le débogage à distance et de proposer le PDM. (*msvsmon.exe* n’est pas un service et doit être démarré manuellement pour activer le débogage à distance sur cet ordinateur.) Lorsque Visual Studio (ou *msvsmon.exe*) est ne pas en cours d’exécution, aucun processus sont suivies pour le débogage.

 Un développeur peut déboguer les programmes qu’il a commencé avec aucune autorisation spéciale. Le développeur peut même déboguer des processus démarrés par quelqu'un d’autre si cette autre personne est membre du même groupe de sécurité. Et, pour activer le débogage à distance, il est uniquement nécessaire pour copier les fichiers requis vers l’ordinateur distant et démarrer *msvsmon.exe*. Pour plus d’informations, consultez [le débogage à distance](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Voir aussi
- [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
- [Gestionnaire de débogage de processus](../../extensibility/debugger/process-debug-manager.md)
- [Débogage distant](../../debugger/remote-debugging.md)
