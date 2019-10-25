---
title: 'Erreur : délai d’attente lors du débogage de services Web | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aba4fef3e1c787651eb961f80b3507090f250a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736888"
---
# <a name="error-timeout-while-debugging-web-services"></a>Erreur : délai d'attente lors du débogage de services Web
Lorsque vous exécutez pas à pas un service web XML à partir du code appelant, l’appel peut parfois dépasser le délai et, par conséquent, vous ne pouvez pas continuer le débogage. Un message d'erreur, tel que celui-ci, peut s'afficher.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>Solution
 Pour éviter ce problème, attribuez une valeur infinie au délai d’attente de l’appel du service web XML, comme dans cet exemple :

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>Voir aussi
- [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
