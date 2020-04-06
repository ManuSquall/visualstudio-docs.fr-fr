---
title: Changer la valeur d’une section locale Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739139"
---
# <a name="change-the-value-of-a-local"></a>Modifier la valeur d’un
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Lorsqu’une nouvelle valeur est tapée dans le champ de valeur de la fenêtre **Locals,** le paquet de débaillement passe la chaîne, comme tapé, à l’évaluateur d’expression (EE). L’EE évalue cette chaîne, qui peut contenir une valeur simple ou une expression, et stocke la valeur résultante dans le local associé.

 Il s’agit d’un aperçu du processus de modification de la valeur d’un local :

1. Une fois que l’utilisateur entre dans la nouvelle valeur, Visual Studio appelle [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sur [l’objet IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) associé au local.

2. `IDebugProperty2::SetValueAsString` effectue les tâches suivantes :

   1. Évalue la chaîne pour produire une valeur.

   2. Lie l’objet [IDebugField](../../extensibility/debugger/reference/idebugfield.md) associé pour obtenir un objet [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md)

   3. Convertit la valeur en une série d’octets.

   4. Appels [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) pour mettre les octets de la valeur dans la mémoire afin que le programme étant débogé peut y accéder.

3. Visual Studio rafraîchit l’affichage **local** (voir [Afficher les habitants](../../extensibility/debugger/displaying-locals.md) pour plus de détails).

   Cette procédure est également utilisée pour modifier la valeur d’une `IDebugProperty2` variable dans la fenêtre **Watch,** sauf que c’est l’objet associé à la valeur du local qui est utilisé au lieu de l’objet `IDebugProperty2` associé au local lui-même.

## <a name="in-this-section"></a>Contenu de cette section
 [Exemple de mise en œuvre de valeurs changeantes](../../extensibility/debugger/sample-implementation-of-changing-values.md) Utilise l’échantillon MyCEE pour passer à travers le processus de changement de valeurs.

## <a name="see-also"></a>Voir aussi
- [Rédaction d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Affichage des habitants](../../extensibility/debugger/displaying-locals.md)
