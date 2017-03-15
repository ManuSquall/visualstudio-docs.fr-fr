---
title: "Prise en charge du Service de langage pour le d&#233;bogage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogueur, prise en charge linguistique"
  - "prise en charge des services de langage de débogage"
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Prise en charge du Service de langage pour le d&#233;bogage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un service de langage peut fournir des fonctionnalités qui prennent en charge un débogueur via le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Ces fonctionnalités incluent la validation des points d'arrêt et en fournissant une liste d'expressions pour les **automatique** fenêtre.  
  
 Toutefois, vous devez avoir un évaluateur d'expression pour déboguer votre langue. L'évaluateur d'expression est responsable de l'évaluation des expressions pour produire des valeurs pendant le débogage. Pour plus d'informations sur l'implémentation des évaluateurs d'expression CLR, consultez :  
  
-   [Évaluateurs d'Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Exemple d'évaluateur d'Expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## Résultats de la compilation  
 Le type de compilateur détermine ce que vous devez faire pour implémenter le débogage de votre langage. Si votre compilateur cible le système d'exploitation Windows et écrit un fichier .pdb, vous pouvez déboguer des programmes avec le moteur est intégré à Visual Studio de débogage du code natif. Si votre compilateur produit Microsoft intermediate language \(MSIL\), vous pouvez déboguer des programmes avec du code managé, débogage de moteur, qui est également intégrée à Visual Studio. Si votre compilateur cible un système d'exploitation propriétaire ou un environnement d'exécution différent, vous devez écrire votre propre moteur de débogage.  
  
 Pour plus d'informations sur l'implémentation de débogage pour votre langage, consultez [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) dans le SDK de débogage de Visual Studio.