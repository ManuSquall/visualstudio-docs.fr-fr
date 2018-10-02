---
title: Contextes du débogueur | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f24360b29557ef767d1a9a5f91a6f116db9ec12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507422"
---
# <a name="debugger-contexts"></a>Contextes du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [contextes du débogueur](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugger-contexts).  
  
Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogage, le moteur de débogage (dé) opère simultanément dans plusieurs contextes distinctes, comme suit :  
  
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
 [Concepts de débogage](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architectures débogage.  
  
 [Composants de débogage](../../extensibility/debugger/debugger-components.md)  
 Fournit une vue d’ensemble des composants de débogage Visual Studio, qui incluent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (SH).  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.

