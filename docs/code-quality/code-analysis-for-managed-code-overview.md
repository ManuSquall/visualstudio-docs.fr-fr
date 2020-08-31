---
title: Analyse du code pour le code managé
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d13a8afdfcbeb6ae9f91e39779af8b82b2461000
ms.sourcegitcommit: 016bcdc7cd3e3619457beb321800e98544efb6c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "89091397"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Vue d’ensemble de l’analyse du code pour .NET dans Visual Studio

Visual Studio peut effectuer une analyse du code managé de deux manières : avec l' [analyse héritée](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), également appelée analyse statique FxCop des assemblys managés, et avec les [analyseurs de code plus modernes basés sur le .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Les analyseurs de code basés sur .NET Compiler Platform, qui analysent votre code en temps réel à mesure que vous tapez, remplacent l’analyse de code statique FxCop héritée, qui analyse uniquement le code compilé.
