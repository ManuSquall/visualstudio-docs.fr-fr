---
title: 'Comment : déboguer des Exceptions ASP.NET | Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a08e382ed9d97aa659012934d3edef45151e10ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178527"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Comment : déboguer des exceptions ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Débogage d’exceptions est une partie importante du développement d’une solide [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] application. Des informations générales sur le débogage d’exceptions sont à [la gestion des Exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Débogage non prise en charge [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] exceptions, vous devez vous assurer que le débogueur s’arrête pour elles. Le runtime [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a un gestionnaire d'exceptions de niveau supérieur. Par conséquent, le débogueur ne s'arrête jamais par défaut sur les exceptions non gérées. Pour arrêter le débogueur lorsqu’une exception est levée, vous devez sélectionner **arrêter lorsqu’une exception est : levé** pour cette exception spécifique dans le **Exceptions** boîte de dialogue.  
  
 Si vous avez activé uniquement mon Code, **arrêter lorsqu’une exception est : levé** n’entraîne pas le débogueur s’arrête immédiatement si une exception est levée dans une méthode .NET Framework ou un autre code système. En revanche, l'exécution continue jusqu'à ce que le débogueur atteigne du code du non-système, puisse elle s'arrête. Résultat : vous n'avez pas à parcourir le code de système lorsqu'une exception se produit.  
  
 Uniquement mon Code offre une autre option qui peut être encore plus utile : **arrêter lorsqu’une exception est : User-unhandled**. Si vous affectez ce paramètre à une exception, le débogueur arrêtera l'exécution du code utilisateur, mais uniquement si l'exception n'est pas interceptée et gérée par le code utilisateur. Ce paramètre annule l'effet du gestionnaire d'exceptions [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] de niveau supérieur, parce que ce gestionnaire se trouve dans du code non-utilisateur.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Activer le débogage des exceptions ASP.NET avec Uniquement mon code  
  
1.  Sur le **déboguer** menu, cliquez sur **Exceptions**.  
  
     Le **Exceptions** boîte de dialogue s’affiche.  
  
2.  Sur le **Exceptions Common Language Runtime** ligne, sélectionnez **levé** ou **User-unhandled**.  
  
     Pour utiliser le **User-unhandled** définition, **uniquement mon Code** doit être activée...  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Pour utiliser les meilleures pratiques pour la gestion des exceptions ASP.NET  
  
-   Placez des blocs `try … catch` autour du code qui peut lever des exceptions que vous pouvez anticiper et que vous savez gérer. Par exemple, si l’application effectue des appels à un Service Web XML ou directement à un serveur SQL Server, ce code doit être dans **try... catch** bloque, car de nombreuses exceptions qui peuvent se produire.



