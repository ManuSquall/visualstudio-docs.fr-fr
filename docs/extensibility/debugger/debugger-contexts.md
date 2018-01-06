---
title: "Contextes de débogueur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f36df39cf29ff298a327ec6e6d4bb02ff53485a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-contexts"></a>Contextes de débogueur
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, le moteur de débogage (DE) fonctionne simultanément dans plusieurs contextes distinctes, comme suit :  
  
-   Le contexte de code, qui décrit l’emplacement actuel dans le flux de l’exécution d’un programme.  
  
-   Le contexte de la documentation ou de la position, qui décrit la position actuelle dans un document source.  
  
-   Le contexte d’évaluation d’expression, qui décrit le contexte dans les expressions évaluation aura lieu.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contexte de code](../../extensibility/debugger/code-context.md)  
 Décrit le contexte du code en tant qu’adresse dans le flux d’instructions d’un programme dans des architectures d’exécution d’aujourd'hui par rapport aux langages non traditionnel, où code ne peut pas être représenté par des instructions, mais d’autres moyens.  
  
 [Position du document](../../extensibility/debugger/document-position.md)  
 Définit la position du document dans le débogage au moyen d’une abstraction d’une position dans un fichier de source connues de l’IDE de Visual Studio.  
  
 [Contexte de document](../../extensibility/debugger/document-context.md)  
 Décrit le contexte de document représente dans le débogage de Visual Studio par rapport à un fichier source. Explique également comment le Gestionnaire de symboles mappe un contexte de code pour le contexte de la documentation.  
  
 [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)  
 Fournit des informations sur un contexte d’évaluation d’expression dans Visual Studio. Par exemple, un contexte d’évaluation d’expression associé à un frame de pile fournit le contexte pour évaluer les variables locales, les paramètres de méthode et les membres de classe.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Débogage des Concepts](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts d’architecture débogage.  
  
 [Composants de débogage](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des composants de débogage Visual Studio, y compris le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (es).  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.