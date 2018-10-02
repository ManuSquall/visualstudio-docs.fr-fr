---
title: Modification de la valeur d’une variable locale | Microsoft Docs
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
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b24bf833336245ff36384e3f34d83b27ed44a62c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503778"
---
# <a name="changing-the-value-of-a-local"></a>Modification de la valeur d’une variable locale
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [modification de la valeur d’une variable locale](https://docs.microsoft.com/visualstudio/extensibility/debugger/changing-the-value-of-a-local).  
  
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quand une nouvelle valeur est tapée dans le champ de valeur de la **variables locales** fenêtre, le package de débogage transmet la chaîne, comme de type, l’évaluateur d’expression (EE). Le EE évalue cette chaîne, ce qui peut contenir une valeur simple ou une expression et stocke la valeur résultante dans local associé.  
  
 Il s’agit d’une vue d’ensemble du processus de modification de la valeur d’une variable locale :  
  
1.  Une fois que l’utilisateur entre la nouvelle valeur, Visual Studio appelle [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sur le [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet associé à l’ordinateur local.  
  
2.  `IDebugProperty2::SetValueAsString` effectue les tâches suivantes :  
  
    1.  Évalue la chaîne pour produire une valeur.  
  
    2.  Lie associé [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet pour obtenir un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet.  
  
    3.  Convertit la valeur à une série d’octets.  
  
    4.  Appels [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) à placer les octets de la valeur dans la mémoire pour le programme en cours de débogage pour y accéder.  
  
3.  Visual Studio actualise le **variables locales** afficher (consultez [affichant les variables locales](../../extensibility/debugger/displaying-locals.md) pour plus d’informations).  
  
 Cette procédure est également utilisée pour modifier la valeur d’une variable dans le **espion** fenêtre, sauf qu’elle est la `IDebugProperty2` objet associé à la valeur de la variable locale qui est utilisée au lieu du `IDebugProperty2` objet associé à l’ordinateur local lui-même.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemple d’implémentation de la modification de valeurs](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Utilise l’exemple MyCEE pour parcourir le processus de modification des valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’Expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)

