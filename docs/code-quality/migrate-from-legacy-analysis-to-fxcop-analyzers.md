---
title: Migrer de l’analyse héritée (FxCop) vers l’analyse source (FxCop Analyzer)
description: Découvrez comment analyser du code pour la première fois ou comment effectuer une migration à partir de l’analyse binaire (FxCop) vers la nouvelle méthode d’analyse du code managé à l’aide de l’analyse de source (FxCop Analyzer).
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9157d47278f835232308dc497965afebb294f8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78937580"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migrer de l’analyse héritée (FxCop) vers l’analyse source (FxCop Analyzer)

Les analyseurs de la source par .NET Compiler Platform (« Roslyn ») remplacent l' [analyse héritée](../code-quality/code-analysis-for-managed-code-overview.md) du code managé. Pour les modèles de projet plus récents tels que les projets .NET Core et .NET Standard, l’analyse héritée n’est pas disponible.

La plupart des règles d’analyse héritée (FxCop) ont déjà été réécrites pour les analyseurs FxCop, un ensemble d’analyseurs de code Roslyn. Vous [Installez les analyseurs FxCop en tant que package NuGet](install-fxcop-analyzers.md#nuget-package) référencé par le projet ou la solution. Les analyseurs FxCop exécutent une analyse basée sur le code source pendant l’exécution du compilateur. Les résultats des analyseurs sont signalés en même temps que les résultats du compilateur.

Pour plus d’informations sur les différences entre l’analyse héritée et l’analyse de la source, consultez les rubriques suivantes :

- [Analyse du code source et analyse héritée](../code-quality/roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

- [FAQ sur les analyseurs FxCop](../code-quality/fxcop-analyzers-faq.md)

Pour migrer vers l’analyse de la source, [Installez les analyseurs FxCop](../code-quality/install-fxcop-analyzers.md). À l’instar des violations des règles d’analyse héritées, les violations de l’analyse du code source s’affichent dans la fenêtre Liste d’erreurs dans Visual Studio. En outre, les violations de l’analyse du code source s’affichent également dans l’éditeur de code sous forme de *tildes* sous le code incriminé. La couleur de la ligne ondulée dépend du [paramètre de gravité](../code-quality/use-roslyn-analyzers.md#rule-severity) de la règle. Pour afficher l’état des règles portées vers les nouveaux analyseurs FxCop, consultez [règles portées et](../code-quality/fxcop-rule-port-status.md)déplacées.

Pour en savoir plus sur la configuration des analyseurs FxCop :

- Pour configurer les analyseurs FxCop, consultez [configurer les analyseurs FxCop](../code-quality/configure-fxcop-analyzers.md).

- Pour en savoir plus sur la configuration des analyseurs à l’aide de règles prédéfinies avec EditorConfig ou un fichier d’ensemble de règles, consultez [activer une catégorie de règles](../code-quality/analyzer-rule-sets.md).