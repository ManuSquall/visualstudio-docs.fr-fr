---
title: "Contextes de d&#233;bogueur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], contextes"
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Contextes de d&#233;bogueur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, le moteur de \(DE\) débogage s'exécute simultanément dans plusieurs contextes distincts, comme suit :  
  
-   le contexte de code, qui décrit la position actuelle dans un flux de données de l'exécution du programme.  
  
-   Le contexte ou la position de documentation, qui décrivent la position actuelle dans un document source.  
  
-   Le contexte d'évaluation de l'expression, qui décrit le contexte dans lequel l'évaluation de l'expression est effectué.  
  
## Dans cette section  
 [contexte de code](../../extensibility/debugger/code-context.md)  
 Décrit le contexte de code comme adresse dans le flux d'instructions d'un programme dans des architectures à l'exécution du jour par rapport à les langages mais pas, où le code ne peut être représenté par l'instruction, mais les inconvénients d'autres moyens.  
  
 [position de document](../../extensibility/debugger/document-position.md)  
 Définit la position du débogage de Visual Studio via une abstraction d'une position dans un fichier source comme connu à l'IDE.  
  
 [contexte de document](../../extensibility/debugger/document-context.md)  
 Décrit ce que représente le contexte du débogage Visual Studio par rapport à un fichier source.  Explique également comment le gestionnaire de symboles mappe un contexte de code au contexte de documentation.  
  
 [contexte d'évaluation de l'expression](../../extensibility/debugger/expression-evaluation-context.md)  
 fournit des informations sur un contexte d'évaluation de l'expression dans Visual Studio.  Par exemple, un contexte d'évaluation de l'expression associé à un frame de pile fournit le contexte pour évaluer les variables locales, des paramètres de méthode, et les membres de classe.  
  
## Rubriques connexes  
 [concepts de débogage](../../extensibility/debugger/debugger-concepts.md)  
 décrit les concepts architecturaux de débogage principal.  
  
 [composants de débogage](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d'ensemble des composants de débogage de Visual Studio, notamment le moteur de \(DE\) débogage, l'évaluateur \(EE\) d'expression, et le gestionnaire de symboles \(SH\).  
  
 [tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers différentes tâches de débogage, telles que exécuter un programme et évaluer des expressions.