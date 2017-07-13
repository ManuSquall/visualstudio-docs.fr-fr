---
title: "Processus d’hébergement (vshost.exe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 96cd56eaeea20b2b0defcb60a188c9e13c19ec6a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# Processus d'hébergement (vshost.exe)
<a id="hosting-process-vshostexe" class="xliff"></a>
Le processus d’hébergement est une fonctionnalité de Visual Studio qui améliore les performances de débogage et permet le débogage de confiance partielle et l’évaluation d’une expression au moment du design. Les fichiers du processus d’hébergement contiennent vshost dans leur nom et sont placés dans le dossier de sortie de votre projet. Pour plus d’informations, consultez [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Les fichiers du processus d’hébergement (.vshost.exe) sont utilisés par Visual Studio et ne doivent pas être exécutés directement ou déployés avec votre application.  
  
## Amélioration des performances de débogage
<a id="improved-debugging-performance" class="xliff"></a>  
 Le processus d’hébergement crée un domaine d’application et associe le débogueur à l’application. La réalisation de ces tâches peut introduire un délai notable entre le démarrage du débogage et le début de l’exécution de l’application. Le processus d’hébergement permet d’améliorer les performances en créant le domaine d’application et en associant le débogueur en arrière-plan, ainsi qu’en enregistrant le domaine d’application et l’état du débogueur entre les exécutions de l’application. Pour plus d’informations sur les domaines d’application, consultez [Domaines d’application](/dotnet/framework/app-domains/application-domains).  
  
## Débogage de confiance partielle
<a id="partial-trust-debugging" class="xliff"></a>  
 Vous pouvez spécifier une application en tant qu’application de confiance partielle dans la [page Sécurité](../ide/reference/security-page-project-designer.md) du **Concepteur de projets**. Le débogage d’une application de confiance partielle nécessite une initialisation spéciale du domaine d’application. Cette initialisation est assurée par le processus d’hébergement.  
  
## Évaluation de l’expression au moment du design
<a id="design-time-expression-evaluation" class="xliff"></a>  
 L’évaluation de l’expression au moment du design vous permet de tester le code à partir de la fenêtre **Exécution** sans devoir exécuter l’application. Le processus d’hébergement exécute ce code pendant l’évaluation de l’expression au moment du design. Pour plus d’informations, consultez [Fenêtre Exécution](../ide/reference/immediate-window.md).  
  
## Voir aussi
<a id="see-also" class="xliff"></a>  
 [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md)   
 [Guide pratique pour désactiver le processus d’hébergement](../ide/how-to-disable-the-hosting-process.md)   
 [Fenêtre Exécution](../ide/reference/immediate-window.md)   
 [Domaines d’application](/dotnet/framework/app-domains/application-domains)
