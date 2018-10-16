---
title: Guide pratique pour profiler du code JavaScript dans des pages web | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
ms.assetid: 37d02aad-ca4d-4eb0-bf66-ca3ecef31fbe
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99e0f201ab1c61999eae1e54efb4eaf4fc475f4d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176473"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Guide pratique pour profiler du code JavaScript dans des pages web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peuvent collecter des données de performances pour le code JavaScript qui s’exécute dans une application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], une page web arbitraire ou une application JavaScript en utilisant la méthode de profilage par instrumentation.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
-   Internet Explorer 8 ou ultérieur  
  
> [!WARNING]
>  Pour profiler JavaScript dans des applications du Windows Store, consultez une des rubriques suivantes :  
>   
>  -   [Minutage de fonction JavaScript](http://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03) [minutage de fonction JavaScript sur un périphérique distant](http://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
> -   [Analyser les données de minutage de fonction JavaScript](http://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
> -  
  
 Vous pouvez utiliser l’Assistant Profilage pour créer une session de performance. Spécifiez la méthode d’instrumentation, puis spécifiez l’option de profilage JavaScript sur la page Instrumentation de la boîte de dialogue des propriétés de la session de performance.  
  
 Quand vous spécifiez le profilage JavaScript, le code JavaScript qui s’exécute dans le navigateur et le code [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] qui s’exécute sur le serveur sont profilés.  
  
-   Pour une application web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], le code JavaScript qui s’exécute dans le navigateur et le code [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] qui s’exécute sur le serveur sont profilés.  
  
-   Pour une page web arbitraire, le code JavaScript qui s’exécute dans le navigateur est profilé.  
  
### <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Pour profiler JavaScript dans un projet d’application web ASP.NET  
  
1.  Dans [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], ouvrez le projet web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
2.  Dans le menu **Analyser** , cliquez sur **Lancer l’Assistant Performance**.  
  
3.  Dans la première page de l’Assistant Performance, spécifiez la méthode de profilage **Instrumentation** , puis cliquez sur **Suivant**.  
  
4.  Dans la deuxième page de l’Assistant, assurez-vous que le projet actuel est sélectionné dans la liste des cibles, puis cliquez sur **Suivant**.  
  
5.  Dans la troisième page de l’Assistant, cochez la case **Profiler JavaScript** , puis cliquez sur **Suivant**.  
  
6.  Dans la quatrième page de l’Assistant, cliquez sur **Terminer** pour démarrer l’application web dans le navigateur.  
  
7.  Testez la fonctionnalité que vous voulez profiler.  
  
8.  Pour terminer la session de profilage, fermez le navigateur.  
  
### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Pour profiler JavaScript dans des pages web individuelles ou une application JavaScript  
  
1.  Ouvrez [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)].  
  
2.  Dans le menu **Analyser** , cliquez sur **Lancer l’Assistant Performance**.  
  
3.  Dans la première page de l’Assistant Performance, spécifiez la méthode de profilage **Instrumentation** , puis cliquez sur **Suivant**.  
  
4.  Dans la deuxième page de l’Assistant, cliquez sur Une application ASP.NET ou JavaScript, puis cliquez sur **Suivant**.  
  
5.  Dans la troisième page de l’Assistant :  
  
    1.  Tapez l’URL de la page dans la zone **Quel URL ou chemin d’accès exécutera votre application** .  
  
    2.  Cochez la case **Profiler JavaScript** , puis cliquez sur **Suivant**.  
  
6.  Dans la quatrième page de l’Assistant, cliquez sur **Terminer** pour démarrer la page web dans le navigateur.  
  
7.  Testez la fonctionnalité que vous voulez profiler.  
  
8.  Pour terminer la session de profilage, fermez le navigateur.



