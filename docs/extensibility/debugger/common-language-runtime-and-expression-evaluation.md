---
title: Common Language Runtime et évaluation des expressions | Microsoft Docs
description: Découvrez comment le Common Language Runtime interagit avec le moteur de débogage et comment intégrer un langage de programmation propriétaire dans l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ddc218d0e9499253269a12687fa89122cfe007
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055009"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime et évaluation des expressions
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Les compilateurs, tels que Visual Basic et C# (prononcé C-Sharp), qui ciblent le Common Language Runtime (CLR), produisent le langage MSIL (Microsoft Intermediate Language), qui est ensuite compilé en code natif. Le CLR fournit un moteur de débogage (DE) pour déboguer le code résultant. Si vous envisagez d’intégrer votre langage de programmation propriétaire dans l’IDE de Visual Studio, vous pouvez choisir de compiler en MSIL et, par conséquent, vous n’aurez pas à écrire votre propre. Toutefois, vous devrez écrire un évaluateur d’expression (EE) qui est capable d’évaluer des expressions dans le contexte de votre langage de programmation.

## <a name="discussion"></a>Discussions
 Les expressions de langage informatique sont généralement analysées pour produire un ensemble d’objets de données et un ensemble d’opérateurs utilisés pour les manipuler. Par exemple, l’expression « A + B » peut être analysée pour appliquer l’opérateur d’addition (+) aux objets de données « A » et « B », ce qui peut entraîner un autre objet de données. Le jeu total d’objets de données, d’opérateurs et de leurs associations est le plus souvent représenté dans un programme sous la forme d’une arborescence, avec les opérateurs situés aux nœuds de l’arborescence et les objets de données au niveau des branches. Une expression qui a été décomposée sous forme d’arborescence est souvent appelée arborescence analysée.

 Une fois qu’une expression a été analysée, un fournisseur de symboles (SP) est appelé pour évaluer chaque objet de données. Par exemple, si « A » est défini à la fois dans plusieurs méthodes, la question « quel ? » la réponse doit être résolue avant que la valeur d’un puisse être vérifiée. La réponse retournée par le SP est semblable à la suivante : « le troisième élément du cinquième frame de pile » ou « A 50 octets au-delà du début de la mémoire statique allouée à cette méthode ».

 Outre la production de code MSIL pour le programme lui-même, les compilateurs CLR peuvent également produire des informations de débogage très descriptives écrites dans un fichier de base de données du programme (*. pdb*). Tant qu’un compilateur de langage propriétaire génère des informations de débogage dans le même format que les compilateurs CLR, le SP du CLR est en mesure d’identifier les objets de données nommées de cette langue. Une fois qu’un objet de données nommé a été identifié, le EE utilise un objet Binder pour associer (ou lier) l’objet de données à la zone mémoire qui contient la valeur de cet objet. La valeur DE peut ensuite obtenir ou définir une nouvelle valeur pour l’objet de données.

 Un compilateur propriétaire peut fournir des informations de débogage du CLR en appelant l' `ISymbolWriter` interface (qui est définie dans le .NET Framework de l’espace de noms `System.Diagnostics.SymbolStore` ). En compilant en MSIL et en écrivant des informations de débogage par le biais de ces interfaces, un compilateur propriétaire peut utiliser le CLR DE et SP. Cela simplifie grandement l’intégration d’un langage propriétaire dans l’IDE de Visual Studio.

 Quand le CLR DE appelle l’EE propriétaire pour évaluer une expression, le service DE fournit à EE des interfaces à un SP et à un objet Binder. Par conséquent, l’écriture d’un moteur de débogage basé sur CLR signifie qu’il est nécessaire d’implémenter uniquement les interfaces d’évaluateur d’expression appropriées. le CLR s’occupe de la liaison et de la gestion des symboles pour vous.

## <a name="see-also"></a>Voir aussi
- [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
