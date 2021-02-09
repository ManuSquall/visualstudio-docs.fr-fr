---
title: Délai d’expiration lors du débogage de services Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 87a2d79fc24bdb433fbb5eb1480dbf5d15520a8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871102"
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
- [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
