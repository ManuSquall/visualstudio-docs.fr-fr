---
title: Contextes du débogueur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a9f75167f45b364757326ddb50ef93edfc37104
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004368"
---
# <a name="debugger-contexts"></a>Contextes du débogueur
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, le moteur de débogage (dé) opère simultanément dans plusieurs contextes distinctes, comme suit :  
  
-   Le contexte de code, qui décrit l’emplacement actuel dans le flux de l’exécution d’un programme.  
  
-   Le contexte de la documentation ou de la position, qui décrit la position actuelle dans un document source.  
  
-   Le contexte d’évaluation expression, qui décrit le contexte dans les expressions évaluation aura lieu.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contexte de code](../../extensibility/debugger/code-context.md)  
 Décrit le contexte de code en tant qu’adresse dans le flux d’instructions d’un programme dans les architectures d’exécution d’aujourd'hui par rapport aux langages non traditionnel, où code ne peut pas être représenté par des instructions, mais d’autres moyens.  
  
 [Position du document](../../extensibility/debugger/document-position.md)  
 Définit la position du document dans le débogage de Visual Studio au moyen d’une abstraction d’une position dans un fichier source connues de l’IDE.  
  
 [Contexte de document](../../extensibility/debugger/document-context.md)  
 Décrit le contexte de document représente lors du débogage de Visual Studio par rapport à un fichier source. Explique également comment le Gestionnaire de symboles mappe un contexte de code au contexte de la documentation.  
  
 [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)  
 Fournit des informations sur un contexte d’évaluation d’expression dans Visual Studio. Par exemple, un contexte d’évaluation d’expression associé à un frame de pile fournit le contexte pour évaluer les variables locales, les paramètres de méthode et les membres de classe.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Déboguer des concepts](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architectures débogage.  
  
 [Déboguer des composants](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des composants de débogage Visual Studio, qui incluent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (SH).  
  
 [Déboguer des tâches](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.