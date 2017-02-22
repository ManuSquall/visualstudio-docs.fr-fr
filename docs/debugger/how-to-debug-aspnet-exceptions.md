---
title: "Comment&#160;: d&#233;boguer des exceptions ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, exceptions"
  - "déboguer (Visual Studio), exceptions ASP.NET"
  - "exceptions, ASP.NET"
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: d&#233;boguer des exceptions ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogage d'exceptions est une part importante du développement d'une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fiable.  Les informations générales à propos du débogage d'exceptions figurent dans [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Pour déboguer des exceptions [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non gérées, vous devez vous assurer que le débogueur s'arrête pour elles.  Le runtime [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a un gestionnaire d'exceptions de niveau supérieur.  Par conséquent, le débogueur ne s'arrête jamais par défaut sur les exceptions non gérées.  Pour arrêter le débogueur lorsqu'une exception est levée, vous devez sélectionner le paramètre **Arrêter lorsqu'une exception est : Levé** pour cette exception spécifique dans la boîte de dialogue **Exceptions**.  
  
 Si vous avez activé Uniquement mon code, **Arrêter lorsqu'une exception est : Levé** n'arrête pas le débogueur immédiatement si une exception est levée dans une méthode .NET Framework ou un autre code système.  En revanche, l'exécution continue jusqu'à ce que le débogueur atteigne du code du non\-système, puisse elle s'arrête.  Résultat : vous n'avez pas à parcourir le code de système lorsqu'une exception se produit.  
  
 Uniquement mon code offre une autre option qui peut vous être encore plus utile : **Arrêter lorsqu'une exception est : Non géré par l'utilisateur**.  Si vous affectez ce paramètre à une exception, le débogueur arrêtera l'exécution du code utilisateur, mais uniquement si l'exception n'est pas interceptée et gérée par le code utilisateur.  Ce paramètre annule l'effet du gestionnaire d'exceptions [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] de niveau supérieur, parce que ce gestionnaire se trouve dans du code non\-utilisateur.  
  
### Activer le débogage des exceptions ASP.NET avec Uniquement mon code  
  
1.  Dans le menu **Déboguer**, cliquez sur **Exceptions**.  
  
     La boîte de dialogue **Exceptions** s'affiche.  
  
2.  Sur la ligne **Exceptions du Common language runtime**, sélectionnez **Levé** ou **Non géré par l'utilisateur**.  
  
     Pour utiliser le paramètre **Non géré par l'utilisateur**, **Uniquement mon code** doit être activé.  
  
### Pour utiliser les meilleures pratiques pour la gestion des exceptions ASP.NET  
  
-   Placez des blocs `try … catch` autour du code qui peut lever des exceptions que vous pouvez anticiper et que vous savez gérer.  Par exemple, si l'application effectue des appels à un service Web XML ou directement à un SQL Server, ce code doit se trouver dans des blocs **try ... catch**, parce que de nombreuses exceptions risquent de se produire.