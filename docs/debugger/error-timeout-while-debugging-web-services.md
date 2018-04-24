---
title: 'Erreur : Le délai lors du débogage de Services Web | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f7b97aa665062b0d0388764cb0ab75956087924
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="error-timeout-while-debugging-web-services"></a>Erreur : délai d'attente lors du débogage de services Web
Lorsque vous exécutez pas à pas un service web XML à partir du code appelant, l’appel peut parfois dépasser le délai et, par conséquent, vous ne pouvez pas continuer le débogage. Un message d'erreur, tel que celui-ci, peut s'afficher.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Solution  
 Pour éviter ce problème, attribuez une valeur infinie au délai d’attente de l’appel du service web XML, comme dans cet exemple :  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)