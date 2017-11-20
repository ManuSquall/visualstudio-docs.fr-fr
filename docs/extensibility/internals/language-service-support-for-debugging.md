---
title: "Prise en charge du Service de langage pour le débogage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb57f7efa13a31ee4c68340936955624189e285d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="language-service-support-for-debugging"></a>Prise en charge du Service de langage pour le débogage
Un service de langage peut fournir des fonctionnalités qui prennent en charge un débogueur via le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Ces fonctionnalités incluent la validation des points d’arrêt et en fournissant une liste d’expressions à la **automatique** fenêtre.  
  
 Toutefois, vous devez avoir l’évaluateur d’expression pour déboguer votre langage de. L’évaluateur d’expression est responsable de l’évaluation des expressions pour produire des valeurs pendant le débogage. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez :  
  
-   [Évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Exemple d’évaluateur d’Expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Résultats de la compilation  
 Le type de compilateur détermine ce que vous devez faire pour implémenter le débogage de votre langage. Si votre compilateur cible le système d’exploitation Windows et les écrit dans un fichier .pdb, vous pouvez déboguer des programmes avec le moteur est intégré à Visual Studio de débogage du code natif. Si votre compilateur produit Microsoft intermediate language (MSIL), vous pouvez déboguer des programmes avec le moteur, qui est également intégré à Visual Studio de débogage du code managé. Si votre compilateur cible un système d’exploitation propriétaire ou un environnement d’exécution différents, vous devez écrire votre propre moteur de débogage.  
  
 Pour plus d’informations sur l’implémentation de débogage pour votre langue, consultez [mise en route](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) dans le SDK de débogage de Visual Studio.