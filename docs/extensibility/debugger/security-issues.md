---
title: "Problèmes de sécurité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>Problèmes de sécurité
Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessitées sont les mêmes que ceux un développeur a besoin pour exécuter le programme. Cela inclut le débogage distant pour la plupart des cas (certaines situations impliquant d’autres services, tels que Internet Information Services, peuvent nécessiter un niveau plus élevé d’autorisations).  
  
 Tandis que Visual Studio est en cours d’exécution, le Gestionnaire de processus de débogage (PDM) effectue le suivi des processus de débogage sur l’ordinateur local. À distance, un programme appelé msvsmon.exe est démarré par le développeur pour gérer le débogage distant et disposition PDM. (Notez que msvsmon.exe n’est pas un service et doit être démarré manuellement pour activer le débogage à distance sur cet ordinateur). Lorsque Visual Studio (ou msvsmon.exe) n’est pas en cours d’exécution, aucun processus ne sont suivis pour le débogage.  
  
 Cela signifie qu’un développeur peut déboguer des programmes commencé avec aucune autorisation particulière. Le développeur peut également déboguer les processus démarrés par un autre utilisateur si cette autre personne est membre du groupe de sécurité même. Pour activer le débogage distant, il est nécessaire uniquement pour copier le nécessaire au serveur distant, les fichiers de l’ordinateur et démarrer msvsmon.exe (voir [débogage distant](../../debugger/remote-debugging.md) pour plus de détails).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [Gestionnaire de processus de débogage](../../extensibility/debugger/process-debug-manager.md)   
 [Débogage à distance](../../debugger/remote-debugging.md)
