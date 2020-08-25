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
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800084"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Vue d’ensemble de l’analyse du code managé dans Visual Studio

Visual Studio peut effectuer une analyse du code managé de deux manières :
- Avec l' [analyse héritée](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), également connue sous le nom d’analyse statique FxCop des assemblys managés.
- Avec les analyseurs de code les plus modernes [basés sur le .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Les analyseurs de code basés sur .NET Compiler Platform, qui analysent votre code en temps réel à mesure que vous tapez, remplacent l’analyse de code statique FxCop héritée, qui analyse uniquement le code compilé.