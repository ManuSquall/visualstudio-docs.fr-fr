---
title: "Modification de la valeur des variables locales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation de l’expression [Debugging SDK], le débogage"
  - "évaluation d’expression, modification des valeurs par programme"
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Modification de la valeur des variables locales
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quand une nouvelle valeur est tapée dans le champ de valeur de la **variables locales** fenêtre, le package de débogage transmet la chaîne, comme le type, l’évaluateur d’expression \(EE\). Le EE évalue cette chaîne, qui peut contenir une valeur simple ou une expression et stocke la valeur résultante dans local associé.  
  
 Il s’agit d’une vue d’ensemble du processus de modification de la valeur d’une variable locale :  
  
1.  Une fois que l’utilisateur entre la nouvelle valeur, Visual Studio appelle [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sur la [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet associé à l’ordinateur local.  
  
2.  `IDebugProperty2::SetValueAsString` effectue les tâches suivantes :  
  
    1.  Évalue la chaîne pour produire une valeur.  
  
    2.  Lie associé [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet afin d’obtenir un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet.  
  
    3.  Convertit la valeur en une série d’octets.  
  
    4.  Appels [SetValue](../Topic/IDebugObject::SetValue.md) pour placer les octets de la valeur dans la mémoire pour le programme débogué peut y accéder.  
  
3.  Visual Studio actualise le **variables locales** afficher \(voir [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md) Pour plus d’informations\).  
  
 Cette procédure est également utilisée pour modifier la valeur d’une variable dans le **Espion** fenêtre, sauf qu’il est le `IDebugProperty2` objet associé à la valeur de la variable locale qui est utilisée à la place de la `IDebugProperty2` objet associé à l’ordinateur local lui\-même.  
  
## Dans cette section  
 [Exemple d’implémentation de la modification des valeurs](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Utilise l’exemple MyCEE pour parcourir le processus de modification des valeurs.  
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md)