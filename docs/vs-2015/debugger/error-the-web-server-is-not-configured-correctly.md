---
title: 'Erreur : le serveur Web n’est pas correctement configuré | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cfbcf127b9951ddfce1d3db8fe1177087b0350a
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918500"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Erreur : le serveur Web n'est pas configuré correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur peut avoir plusieurs causes :  
  
- Une tentative de débogage d’une application Web .NET qui a été copiée sur un ordinateur différent, renommée manuellement ou déplacée.  
  
- Insuffisance des connexions IIS. Pour plus d’informations sur le déploiement d’un site web vers IIS, consultez [Créer un site web](/iis/get-started/getting-started-with-iis/create-a-web-site).  
  
- Si vous essayez de déboguer une application ASP.NET, consultez soit [Publication dans IIS](https://docs.asp.net/en/latest/publishing/iis.html) pour obtenir des instructions sur le déploiement vers un ordinateur distant exécutant IIS 8 ou version ultérieure, soit [Remote Debugging ASP.NET on a Remote IIS 7.5 Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) pour obtenir des instructions sur le déploiement vers un ordinateur distant exécutant IIS 7.5.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
