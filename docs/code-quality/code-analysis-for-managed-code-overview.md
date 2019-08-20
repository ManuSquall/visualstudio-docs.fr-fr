---
title: Analyse du code pour le code managé
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a44465b5f3daf89e915a5f6f5e7abe6c856598e5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546921"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Vue d’ensemble de l’analyse du code managé dans Visual Studio

Visual Studio peut effectuer une analyse du code managé de deux manières: avec l' [analyse héritée](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), également appelée analyse statique FxCop des assemblys managés, et avec les analyseurs de [code](../code-quality/roslyn-analyzers-overview.md)plus modernes basés sur le .NET Compiler Platform. Les analyseurs de code basés sur .NET Compiler Platform, qui analysent votre code en temps réel à mesure que vous tapez, remplacent l’analyse de code statique FxCop héritée, qui analyse uniquement le code compilé.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs basés sur .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
