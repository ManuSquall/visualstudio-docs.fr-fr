---
title: 'Erreur : Le délai pendant le débogage de Services Web | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dee3017114c645c5bc3c2001e0cb2cafda48ef53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504458"
---
# <a name="error-timeout-while-debugging-web-services"></a>Erreur : délai d'attente lors du débogage de services Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [erreur : délai d’attente lors du débogage de Services Web](https://docs.microsoft.com/visualstudio/debugger/error-timeout-while-debugging-web-services).  
  
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



