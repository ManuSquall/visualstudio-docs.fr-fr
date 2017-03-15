---
title: "Moteur de d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage"
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Moteur de d&#233;bogage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un moteur \(DE\) de débogage s'exécute avec l'interpréteur ou le système d'exploitation pour fournir des services de débogage tels que le contrôle, les points d'arrêt, et l'évaluation de l'expression d'exécution.  Le De est chargé de contrôler l'état d'un programme en cours de débogage.  Pour faire pour ce faire, le De utilise toutes les méthodes sont disponibles à lui dans le runtime pris en charge, si de l'UC ou les API fournies par le runtime.  
  
 Par exemple, le common langage \(CLR\) runtime fournit des mécanismes pour surveiller un programme en cours de exécution par le biais de les interfaces d'ICorDebugXXX.  Un De qui prend en charge le CLR utilise les interfaces appropriées d'ICorDebugXXX pour conserver un programme de code managé en cours de débogage.  Il communique toutes les modifications d'état au gestionnaire de débogage de session \(SDM\), qui transmet de telles informations [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE.  
  
> [!NOTE]
>  Un moteur de débogage cible un runtime spécifique, c. autrement dit., le système dans lequel le programme en cours est en cours de exécution.  Le CLR est le runtime pour le code managé, et le runtime Win32 concerne les applications Windows natives.  Si le langage que vous créez peut cibler un de ces deux runtimes, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit déjà les moteurs de débogage nécessaires.  Tout ce que vous devez implémenter est un évaluateur d'expression.  
  
## opération de moteur de débogage  
 Les services de contrôle sont implémentés par le biais DE interfaces et peuvent provoquer le package de débogage à la transition entre les différents modes opérationnels.  Pour plus d'informations, consultez [Modes de fonctionnement](../../extensibility/debugger/operational-modes.md).  Il y a généralement un seul L'implementation par environnement d'exécution.  
  
> [!NOTE]
>  S'il y a DE implementations distinct pour Transact\-SQL et [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)], VBScript et [!INCLUDE[jsprjscript](../../extensibility/debugger/includes/jsprjscript_md.md)] partagent un De unique.  
  
 le débogage de[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]permet aux moteurs de débogage pour exécuter une de deux façons : dans le même processus que le shell de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ou dans le même processus que le programme cible en cours de débogage.  Le dernier formulaire se produit généralement lorsque le processus débogué est en fait un bon fonctionnement de script sous un interpréteur, et le moteur de débogage doit avoir l'intime connaissance de l'interpréteur afin de contrôler le script.  Notez que dans ce cas, l'interpréteur est en réalité un runtime ; les moteurs de débogage sont pour les implémentations du runtime spécifiques.  En outre, l'implémentation d'un De peut être fractionné au delà de les limites de processus et de l'ordinateur \(par exemple, débogage distant\).  
  
 Le expose De [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage des interfaces.  Toutes les communications est via COM.  Si le De est chargé en cours de processus, hors processus, ou sur un autre ordinateur, il n'affecte pas la communication entre les composants.  
  
 Le De fonctionne avec un composant évaluateur d'expression pour activer le De pour que ce moment particulier inclut la syntaxe des expressions.  Le De fonctionne également avec un composant de gestionnaire de symboles pour accéder aux informations de débogage symboliques générées par le compilateur de langage.  Pour plus d'informations, consultez [Évaluateur d'expression](../../extensibility/debugger/expression-evaluator.md) et [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md).  
  
## Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)   
 [Évaluateur d'expression](../../extensibility/debugger/expression-evaluator.md)   
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)