---
title: "Guide pratique pour profiler du code JavaScript dans des pages web | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 737ead7c9745fc7cb173d542379f3c0d8ba39e89
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Guide pratique pour profiler du code JavaScript dans des pages web

Les Outils de profilage de Visual Studio peuvent collecter des données de performances pour le code JavaScript qui s’exécute dans une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], une page web arbitraire ou une application JavaScript en utilisant la méthode de profilage par instrumentation. La version 8 d’Internet Explorer ou une version ultérieure est requise.

> [!WARNING]
> Pour profiler JavaScript dans des applications UWP, consultez [Mémoire JavaScript](../profiling/javascript-memory.md). 

Vous pouvez utiliser l’Assistant Profilage pour créer une session de performance. Spécifiez la méthode d’instrumentation, puis spécifiez l’option de profilage JavaScript sur la page Instrumentation de la boîte de dialogue des propriétés de la session de performance.

Quand vous spécifiez le profilage JavaScript, le code JavaScript qui s’exécute dans le navigateur et le code [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui s’exécute sur le serveur sont profilés.

- Pour une application web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , le code JavaScript qui s’exécute dans le navigateur et le code [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] qui s’exécute sur le serveur sont profilés.

- Pour une page web arbitraire, le code JavaScript qui s’exécute dans le navigateur est profilé.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Pour profiler JavaScript dans un projet d’application web ASP.NET

1. Ouvrez le projet web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dans Visual Studio.

2. Dans le menu **Analyser** , cliquez sur **Lancer l’Assistant Performance**.

3. Dans la première page de l’Assistant Performance, spécifiez la méthode de profilage **Instrumentation** , puis cliquez sur **Suivant**.

4. Dans la deuxième page de l’Assistant, assurez-vous que le projet actuel est sélectionné dans la liste des cibles, puis cliquez sur **Suivant**.

5. Dans la troisième page de l’Assistant, cochez la case **Profiler JavaScript** , puis cliquez sur **Suivant**.

6. Dans la quatrième page de l’Assistant, cliquez sur **Terminer** pour démarrer l’application web dans le navigateur.

7. Testez la fonctionnalité que vous voulez profiler.

8. Pour terminer la session de profilage, fermez le navigateur.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Pour profiler JavaScript dans des pages web individuelles ou une application JavaScript

1. Ouvrez Visual Studio.

2. Dans le menu **Analyser** , cliquez sur **Lancer l’Assistant Performance**.

3. Dans la première page de l’Assistant Performance, spécifiez la méthode de profilage **Instrumentation** , puis cliquez sur **Suivant**.

4. Dans la deuxième page de l’Assistant, cliquez sur Une application ASP.NET ou JavaScript, puis cliquez sur **Suivant**.

5. Dans la troisième page de l’Assistant :

    1. Tapez l’URL de la page dans la zone **Quel URL ou chemin d’accès exécutera votre application** .

    2. Cochez la case **Profiler JavaScript** , puis cliquez sur **Suivant**.

6. Dans la quatrième page de l’Assistant, cliquez sur **Terminer** pour démarrer la page web dans le navigateur.

7. Testez la fonctionnalité que vous voulez profiler.

8. Pour terminer la session de profilage, fermez le navigateur.