---
title: Problèmes de sécurité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874231333c87020c126eac4c066d53512ba0bbc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938078"
---
# <a name="security-issues"></a>Problèmes de sécurité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessitées sont les mêmes que ceux un développeur a besoin pour exécuter le programme. Cela inclut le débogage distant pour la plupart des cas (certaines situations impliquant d’autres services, tels que le Service d’informations Internet, peuvent nécessiter un niveau plus élevé d’autorisations).  
  
 Pendant l’exécution de Visual Studio, le Gestionnaire de débogage de processus (PDM) effectue le suivi de déboguer des processus sur l’ordinateur local. Un programme appelé msvsmon.exe est démarré à distance, par le développeur pour gérer le débogage à distance et de proposer le PDM. (Notez que msvsmon.exe n’est pas un service et doit être démarré manuellement pour activer le débogage à distance sur cet ordinateur.) Lorsque Visual Studio (ou msvsmon.exe) ne fonctionne pas, aucun processus ne sont suivies pour le débogage.  
  
 Cela signifie qu’un développeur peut déboguer des programmes commencé avec aucune autorisation spéciale. Le développeur peut même déboguer des processus démarrés par quelqu'un d’autre si cette autre personne est membre du même groupe de sécurité. Et pour activer le débogage à distance, il est nécessaire uniquement pour copier les nécessaires fichiers à l’instance distante de l’ordinateur et démarrer msvsmon.exe (consultez [définir Up the Remote Tools sur l’appareil](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) pour plus d’informations).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [Gestionnaire de débogage de processus](../../extensibility/debugger/process-debug-manager.md)   
 [Configurer les outils de contrôle à distance sur le périphérique](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
