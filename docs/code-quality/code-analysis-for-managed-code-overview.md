---
title: Analyse du code pour le code managé
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f32cf357cadafd6d5dd8166c23de15a16a8e502c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587757"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Vue d’ensemble de l’analyse du code managé dans Visual Studio

Visual Studio peut effectuer une analyse du code managé de deux manières : avec l' [analyse héritée](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), également appelée analyse statique FxCop des assemblys managés, et avec les [analyseurs de code](../code-quality/roslyn-analyzers-overview.md)plus modernes basés sur le .NET Compiler Platform. Les analyseurs de code basés sur .NET Compiler Platform, qui analysent votre code en temps réel à mesure que vous tapez, remplacent l’analyse de code statique FxCop héritée, qui analyse uniquement le code compilé.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs basés sur .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md)
