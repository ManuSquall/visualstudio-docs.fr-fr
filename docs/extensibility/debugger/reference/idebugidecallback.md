---
title: "IDebugIDECallback | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugIDECallback"
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugIDECallback
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Permet à un évaluateur d’expression \(EE\) afficher un message dans la fenêtre de sortie du débogueur.  
  
## Syntaxe  
  
```  
IDebugIDECallback : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Ce rappel est implémenté par le moteur de débogage managé.  
  
## Remarques pour les appelants  
 Il peut être consommé par un évaluateur d’expression pour envoyer la sortie à la fenêtre de sortie du débogueur.  
  
## Méthodes  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[DisplayMessage](../Topic/IDebugIDECallback::DisplayMessage.md)|Envoie la chaîne du message spécifié à la fenêtre de sortie du débogueur.|  
  
## Configuration requise  
 En\-tête : Ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll