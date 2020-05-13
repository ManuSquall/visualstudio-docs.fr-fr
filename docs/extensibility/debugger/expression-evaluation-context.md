---
title: Contexte d’évaluation de l’expression (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738734"
---
# <a name="expression-evaluation-context"></a>Contexte d’évaluation de l’expression
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage, un **contexte d’évaluation d’expression**:

- Représente un contexte d’évaluation de l’expression. En général, un contexte d’évaluation correspond à la portée lexicale dans laquelle évaluer les variables, les paramètres, les fonctions et les méthodes. Par exemple, un contexte d’évaluation d’expression associé à un cadre de pile fournira le contexte pour évaluer les variables locales, les paramètres de la méthode et les membres du groupe (le cas échéant).

- Existe lorsqu’un programme s’arrête à un point d’arrêt. L’expression elle-même est une structure de données représentant une expression analysée qui est prête à lier et à évaluer dans le contexte donné.

     Plus en détail, des expressions sont créées à l’aide de la méthode [ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Lorsqu’une expression est évaluée, elle génère une chaîne imprimable contenant le nom et le type de variable ou d’argumentation et sa valeur. Cette chaîne est affichée dans la fenêtre Watch ou dans la fenêtre locale de l’IDE.

     Compte `BSTR` tenu d’une interface [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) un moteur de débogé (DE) peut créer une interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) en parsingant une expression. Compte `IDebugExpression2` tenu d’une interface, le DE peut obtenir une valeur grâce à l’évaluation de l’expression synchrone ou asynchrone. Cette valeur, ainsi que le nom et le type de la variable ou de l’argumentation, est envoyé à l’IDE pour l’affichage.

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation d’expression](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md)
