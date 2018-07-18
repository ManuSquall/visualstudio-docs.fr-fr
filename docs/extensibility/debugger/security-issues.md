---
title: Problèmes de sécurité | Documents Microsoft
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
ms.openlocfilehash: d45ebd8c4d80b84749838c2034d72159c9e39627
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126895"
---
# <a name="security-issues"></a>Problèmes de sécurité
Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessitées sont les mêmes que ceux un développeur a besoin pour exécuter le programme. Cela inclut le débogage distant pour la plupart des cas (certaines situations impliquant d’autres services, comme Internet Information Services, peuvent nécessiter un niveau supérieur d’autorisations).  
  
 Pendant l’exécution de Visual Studio, le Gestionnaire de processus de débogage (PDM) effectue le suivi des processus de débogage sur l’ordinateur local. À distance, un programme appelé msvsmon.exe est démarré par le développeur pour gérer le débogage distant et de disposition de PDM. (Notez que msvsmon.exe n’est pas un service et doit être démarré manuellement pour activer le débogage à distance sur cet ordinateur.) Lorsque Visual Studio (ou msvsmon.exe) n’est pas en cours d’exécution, aucun processus ne sont suivies pour le débogage.  
  
 Cela signifie qu’un développeur peut déboguer les programmes qu'il ou elle a démarré avec des autorisations spéciales. Le développeur peut même déboguer les processus démarrés par un autre utilisateur si cette personne est membre du même groupe de sécurité. Pour activer le débogage distant, il est nécessaire uniquement nécessaires de copier les fichiers à l’instance distante de l’ordinateur et démarrer msvsmon.exe (consultez [débogage distant](../../debugger/remote-debugging.md) pour plus d’informations).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [Gestionnaire de processus de débogage](../../extensibility/debugger/process-debug-manager.md)   
 [Débogage à distance](../../debugger/remote-debugging.md)