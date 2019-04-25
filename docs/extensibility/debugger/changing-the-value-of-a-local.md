---
title: Modification de la valeur d’une variable locale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf90a2c03112cb2d3a935a9721f455ec976803c7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041741"
---
# <a name="change-the-value-of-a-local"></a>Modifiez la valeur d’une variable locale
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quand une nouvelle valeur est tapée dans le champ de valeur de la **variables locales** fenêtre, le package de débogage transmet la chaîne, comme de type, l’évaluateur d’expression (EE). Le EE évalue cette chaîne, ce qui peut contenir une valeur simple ou une expression et stocke la valeur résultante dans local associé.

 Il s’agit d’une vue d’ensemble du processus de modification de la valeur d’une variable locale :

1. Une fois que l’utilisateur entre la nouvelle valeur, Visual Studio appelle [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sur le [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet associé à l’ordinateur local.

2. `IDebugProperty2::SetValueAsString` effectue les tâches suivantes :

   1. Évalue la chaîne pour produire une valeur.

   2. Lie associé [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet pour obtenir un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet.

   3. Convertit la valeur à une série d’octets.

   4. Appels [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) à placer les octets de la valeur dans la mémoire pour le programme en cours de débogage pour y accéder.

3. Visual Studio actualise le **variables locales** afficher (consultez [variables locales affichage](../../extensibility/debugger/displaying-locals.md) pour plus d’informations).

   Cette procédure est également utilisée pour modifier la valeur d’une variable dans le **espion** fenêtre, sauf si elle est la `IDebugProperty2` objet associé à la valeur de la variable locale qui est utilisée au lieu du `IDebugProperty2` objet associé à l’ordinateur local lui-même.

## <a name="in-this-section"></a>Dans cette section
 [Exemple d’implémentation de la modification des valeurs](../../extensibility/debugger/sample-implementation-of-changing-values.md) utilise l’exemple MyCEE pour parcourir le processus de modification des valeurs.

## <a name="see-also"></a>Voir aussi
- [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)