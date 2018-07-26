---
title: Problèmes de sécurité | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cd4d07721f202169ca0689882ac1a41045a4d61
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252321"
---
# <a name="security-issues"></a>Problèmes de sécurité
Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessitées sont les mêmes que ceux un développeur a besoin pour exécuter le programme. Cela inclut le débogage distant pour la plupart des situations. Certaines situations impliquant d’autres services, tels que le Service d’informations Internet, peuvent nécessiter un niveau plus élevé d’autorisations.  
  
 Pendant l’exécution de Visual Studio, le Gestionnaire de débogage de processus (PDM) effectue le suivi de déboguer des processus sur l’ordinateur local. À distance, un programme appelé *msvsmon.exe* est démarré par le développeur pour gérer le débogage à distance et de proposer le PDM. (*msvsmon.exe* n’est pas un service et doit être démarré manuellement pour activer le débogage à distance sur cet ordinateur.) Lorsque Visual Studio (ou *msvsmon.exe*) est ne pas en cours d’exécution, aucun processus sont suivies pour le débogage.  
  
 Un développeur peut déboguer les programmes qu’il a commencé avec aucune autorisation spéciale. Le développeur peut même déboguer des processus démarrés par quelqu'un d’autre si cette autre personne est membre du même groupe de sécurité. Et, pour activer le débogage à distance, il est uniquement nécessaire pour copier les fichiers requis vers l’ordinateur distant et démarrer *msvsmon.exe*. Pour plus d’informations, consultez [le débogage à distance](../../debugger/remote-debugging.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [Gestionnaire de débogage de processus](../../extensibility/debugger/process-debug-manager.md)   
 [Débogage distant](../../debugger/remote-debugging.md)
