---
title: Analyse du code pour le code managé
ms.date: 08/27/2020
description: En savoir plus sur les analyseurs de code basés sur .NET Compiler Platform dans Visual Studio. Comprenez pourquoi ces analyseurs remplacent l’analyse statique FxCop des assemblys managés.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348526"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Vue d’ensemble de l’analyse du code pour .NET dans Visual Studio

Visual Studio peut effectuer une analyse du code managé de deux manières : avec l' [analyse héritée](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md), également appelée analyse statique FxCop des assemblys managés, et avec les [analyseurs de code plus modernes basés sur le .NET Compiler Platform](../code-quality/roslyn-analyzers-overview.md). Les analyseurs de code basés sur .NET Compiler Platform, qui analysent votre code en temps réel à mesure que vous tapez, remplacent l’analyse de code statique FxCop héritée, qui analyse uniquement le code compilé.
