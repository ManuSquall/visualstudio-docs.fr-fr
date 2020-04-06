---
title: Évaluation du temps de course et de l’expression des langues courantes (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739109"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Évaluation de l’heure d’exécution et de l’expression des langues courantes
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Les compilateurs, tels que Visual Basic et CMD (prononcé C-sharp), qui ciblent le Common Language Runtime (CLR), produisent Microsoft Intermediate Language (MSIL), qui est plus tard compilé au code natif. Le CLR fournit un moteur de débogé (DE) pour déboiffer le code résultant. Si vous envisagez d’intégrer votre langage de programmation propriétaire dans l’IDE Visual Studio, vous pouvez choisir de compiler à MSIL et donc ne pas avoir à écrire votre propre DE. Cependant, vous devrez écrire un évaluateur d’expression (EE) qui est capable d’évaluer les expressions dans le contexte de votre langage de programmation.

## <a name="discussion"></a>Discussions
 Les expressions en langage informatique sont généralement analysées pour produire un ensemble d’objets de données et un ensemble d’opérateurs utilisés pour les manipuler. Par exemple, l’expression « A-B » peut être analysée pour appliquer l’opérateur d’addition (MD) aux objets de données « A » et « B », ce qui peut entraîner un autre objet de données. L’ensemble total des objets de données, des opérateurs et de leurs associations sont le plus souvent représentés dans un programme comme arbre, avec les opérateurs aux nœuds de l’arbre et les objets de données dans les branches. Une expression qui a été décomposée sous forme d’arbre est souvent appelée arbre analysé.

 Une fois qu’une expression a été analysée, un fournisseur de symboles (SP) est appelé à évaluer chaque objet de données. Par exemple, si « A » est défini à la fois dans plus d’une méthode, la question « Which A? » doit être répondu avant que la valeur de A puisse être vérifiée. La réponse retournée par le SP est quelque chose comme "Le troisième élément sur le cadre de la cinquième pile" ou "Le A qui est de 50 octets au-delà du début de la mémoire statique allouée à cette méthode."

 En plus de produire MSIL pour le programme lui-même, compilateurs CLR peut également produire des informations de débogage très descriptive qui est écrit dans un programme DataBase (*.pdb*) fichier. Tant qu’un compilateur en langue propriétaire produit des informations de débaillement dans le même format que les compilateurs CLR, le SP du CLR est en mesure d’identifier les objets de données nommés par cette langue. Une fois qu’un objet de données nommé a été identifié, l’EE utilise un objet de liant pour associer (ou lier) l’objet de données à la zone de mémoire qui détient la valeur de cet objet. Le DE peut alors obtenir ou définir une nouvelle valeur pour l’objet de données.

 Un compilateur propriétaire peut fournir des informations `ISymbolWriter` de débogage CLR en appelant l’interface (qui est définie dans le cadre .NET dans l’espace de `System.Diagnostics.SymbolStore`nom ). En compilant à MSIL et en écrivant des informations de débagé à travers ces interfaces, un compilateur propriétaire peut utiliser le CLR DE et SP. Cela simplifie grandement l’intégration d’une langue propriétaire dans l’IDE Visual Studio.

 Lorsque le CLR DE appelle l’EE propriétaire pour évaluer une expression, le DE fournit l’EE avec des interfaces à un SP et un objet de liant. Ainsi, l’écriture d’un moteur de débogé à base de CLR signifie qu’il est nécessaire seulement de mettre en œuvre les interfaces d’évaluateur d’expression appropriées; le CLR s’occupe de la reliure et de la manipulation du symbole pour vous.

## <a name="see-also"></a>Voir aussi
- [Écrire un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
