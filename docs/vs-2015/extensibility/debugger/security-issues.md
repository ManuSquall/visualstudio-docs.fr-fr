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
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704425"
---
# <a name="security-issues"></a>Problèmes de sécurité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour déboguer un programme à l’aide de Visual Studio, les seules autorisations nécessaires sont les mêmes que celles dont un développeur a besoin pour exécuter le programme. Cela comprend le débogage à distance pour la plupart des situations (certaines situations impliquant d’autres services, tels que Internet Information Service, peuvent nécessiter un niveau d’autorisations plus élevé).  
  
 Pendant que Visual Studio est en cours d’exécution, le gestionnaire de débogage de processus (PDM) effectue le suivi des processus de débogage sur l’ordinateur local. À distance, un programme appelé msvsmon.exe est démarré par le développeur pour gérer le débogage distant et rendre le PDM disponible. (Notez que msvsmon.exe n’est pas un service et doit être démarré manuellement pour activer le débogage à distance sur cet ordinateur.) Lorsque Visual Studio (ou msvsmon.exe) n’est pas en cours d’exécution, aucun processus n’est suivi pour le débogage.  
  
 Cela signifie qu’un développeur peut déboguer des programmes qu’il a démarrés sans autorisations spéciales. Le développeur peut même déboguer les processus démarrés par quelqu’un d’autre si cette personne est membre du même groupe de sécurité. Et pour activer le débogage à distance, il est nécessaire uniquement de copier les fichiers nécessaires sur l’ordinateur distant et de démarrer msvsmon.exe (pour plus d’informations, consultez [configurer la outils de contrôle à distance sur l’appareil](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) ).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [Gestionnaire de débogage de processus](../../extensibility/debugger/process-debug-manager.md)   
 [Configurer les outils de contrôle à distance sur le périphérique](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
