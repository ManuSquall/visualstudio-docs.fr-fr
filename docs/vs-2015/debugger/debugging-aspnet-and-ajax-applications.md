---
title: Débogage des Applications ASP.NET et AJAX | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5943b75513394b44d88dfcfa496e56dad267171
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205203"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Débogage d’applications ASP.NET et AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogage d'applications Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ressemble au débogage d'un Windows Form ou d'une application Windows quelconque, ces applications impliquant dans l'un et l'autre cas des contrôles et des événements. Il existe néanmoins aussi des différences fondamentales entre elles :  
  
-   Assurer le suivi de l'état est plus complexe dans une application Web.  
  
-   Dans une application Windows, le code à déboguer se trouve essentiellement rassemblé au même endroit ; dans une application Web, le code peut se trouver sur le client et sur le serveur. Alors que le code [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se trouve entièrement sur le serveur, il peut y avoir également du code JavaScript ou [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] sur le client.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Préparation du débogage ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Décrit les étapes nécessaires pour activer le débogage d'applications [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 [Débogage d’applications web](../debugger/debugging-web-applications.md)  
 Explique comment déboguer une application [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], y compris des applications de script compatibles AJAX.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)  
 Explique pourquoi Uniquement mon code doit être activé pour le débogage d'exceptions [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Présente quelques techniques et outils qui peuvent vous aider à déboguer votre code AJAX plus facilement.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Déboguez votre code plus rapidement à l’aide de IntelliTrace pour enregistrer et tester un historique de l’état de votre application sans redémarrer l’application fréquemment. Vous pouvez consulter les informations sur les événements et les appels qui surviennent pendant l'exécution de votre application et commencer le débogage à temps. Requiert Visual Studio Ultimate.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage d’applications et de scripts web](../debugger/debugging-web-applications-and-script.md)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)



