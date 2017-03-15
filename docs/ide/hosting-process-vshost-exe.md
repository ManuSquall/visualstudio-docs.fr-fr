---
title: "Processus d&#39;h&#233;bergement (vshost.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "processus d'hébergement"
  - "vshost.exe"
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Processus d&#39;h&#233;bergement (vshost.exe)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le processus d'hébergement est une fonctionnalité de Visual Studio qui améliore les performances du débogage, Active le débogage de confiance partielle et permet l'évaluation d'expression design time.  Les fichiers du processus de l'hébergement contiennent vshost dans le nom de fichier et sont placés dans le dossier de sortie de votre projet.  Pour plus d'informations, consultez [Débogage et processus d'hébergement](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Fichiers de processus d'hébergement \(. vshost.exe\) sont utilisées par Visual Studio et ne doivent pas être exécutés directement ou déployés avec votre application.  
  
## Amélioration des performances du débogage  
 Le processus d'hébergement crée un domaine d'application et associe le débogueur à l'application.  L'exécution de ces tâches peut introduire un délai significatif entre le démarrage du débogage et le début de l'exécution de l'application.  Le processus d'hébergement contribue à l'amélioration des performances en créant le domaine d'application et en associant le débogueur en arrière\-plan, et en enregistrant le domaine d'application et l'état du débogueur entre les exécutions de l'application.  Pour plus d'informations sur les domaines d'application, consultez [Domaines d'application](../Topic/Application%20Domains.md).  
  
## Débogage en confiance partielle  
 Une application peut être spécifiée comme une application de confiance partielle dans la [page Sécurité](../ide/reference/security-page-project-designer.md) du **Concepteur de projets**.  Le débogage d'une application de confiance partielle nécessite une initialisation spéciale du domaine d'application.  Cette initialisation est assurée par le processus d'hébergement.  
  
## Évaluation de l'expression au moment du design  
 L'évaluation d'une expression au moment du design vous permet de tester le code à partir de la fenêtre **Exécution**, sans devoir exécuter l'application.  Le processus d'hébergement exécute ce code pendant l'évaluation d'une expression au moment du design.  Pour plus d'informations, consultez [Fenêtre Exécution](../ide/reference/immediate-window.md).  
  
## Voir aussi  
 [Débogage et processus d'hébergement](../debugger/debugging-and-the-hosting-process.md)   
 [Comment : désactiver le processus d'hébergement](../ide/how-to-disable-the-hosting-process.md)   
 [Fenêtre Exécution](../ide/reference/immediate-window.md)   
 [Domaines d'application](../Topic/Application%20Domains.md)