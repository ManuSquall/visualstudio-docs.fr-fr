---
title: Référence d’ensemble de règles d’analyse du code
ms.date: 04/04/2018
description: En savoir plus sur les ensembles de règles intégrés dans l’analyse du code hérité Visual Studio. Consultez ressources sur les ensembles de règles. Découvrez comment utiliser ces jeux dans des ensembles de règles personnalisés.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cead2d51a13ce4ec137edcd55c7db91d84b04f7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867774"
---
# <a name="code-analysis-rule-set-reference"></a>Référence d’ensemble de règles d’analyse du code

Quand vous configurez une analyse héritée pour des projets de code managé dans Visual Studio, vous pouvez choisir parmi une liste d' *ensembles de règles* intégrés. Certaines règles sont incluses dans plusieurs ensembles de règles prédéfinis, par exemple, l’ensemble de règles de règles de vérification de base inclut des règles qui se trouvent dans l’ensemble de règles des règles recommandées managées.

> [!NOTE]
> Les ensembles de règles de cette section se rapportent aux analyses héritées. Pour plus d’informations sur les ensembles de règles disponibles pour les packages de l’analyseur de code, consultez [utiliser des ensembles de règles avec des analyseurs de code](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

Vous pouvez utiliser l’un de ces ensembles de règles intégrés ou [personnaliser un ensemble de règles](../code-quality/how-to-create-a-custom-rule-set.md) en fonction des exigences de votre projet. Si vous incluez plusieurs ensembles de règles qui contiennent la même règle dans un ensemble de règles personnalisé, cette règle apparaît une seule fois dans l’ensemble de règles personnalisé.

Les rubriques de cette section décrivent les ensembles de règles intégrés et les règles (ou avertissements) qu’elles contiennent.

| Ensemble de règles | Règles incluses |
| - | - |
| [Toutes les règles](all-rules-rule-set.md) | Contient toutes les règles managées et C++ disponibles |
| [Règles de vérification de base](basic-correctness-rules-rule-set-for-managed-code.md) | Comprend les règles recommandées gérées, ainsi que les règles pour les erreurs logiques et l’utilisation de l’infrastructure |
| [Règles de vérification étendue](extended-correctness-rules-rule-set-for-managed-code.md) | Comprend des règles de vérification de base (qui incluent les règles recommandées gérées), ainsi que d’autres règles pour les erreurs logiques et l’utilisation de l’infrastructure |
| [Règles de conception de base](basic-design-guideline-rules-rule-set-for-managed-code.md) | Comprend des règles recommandées gérées, ainsi que des règles permettant de s’assurer que le code est facile à lire, à comprendre et à entretenir. |
| [Règles de conception étendue](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Comprend des règles de conception de base (qui incluent les règles recommandées gérées), ainsi que des règles de maintenabilité qui se concentrent sur l’affectation de noms |
| [Règles de globalisation](globalization-rules-rule-set-for-managed-code.md) | Contient des règles pour les problèmes de globalisation |
| [Règles minimales gérées](managed-minimum-rules-rule-set-for-managed-code.md) | Contient quatre règles pour les problèmes critiques de code managé |
| [Règles recommandées gérées](managed-recommended-rules-rule-set-for-managed-code.md) | Comprend des règles minimales gérées, ainsi que d’autres règles pour les problèmes critiques de code managé |
| [Règles minimales mixtes](mixed-minimum-rules-rule-set.md) | Contient des règles pour les problèmes critiques dans le code C++ pour CLR |
| [Règles recommandées mixtes](mixed-recommended-rules-rule-set.md) | Comprend des règles minimales mixtes plus des règles pour les problèmes critiques dans le code C++ pour CLR |
| [Règles minimales natives](native-minimum-rules-rule-set.md) | Contient des règles pour les problèmes critiques en code natif |
| [Règles recommandées natives](native-recommended-rules-rule-set.md) | Comprend des règles minimales natives, ainsi que d’autres règles pour les problèmes critiques en code natif. |
| [Règles de sécurité](security-rules-rule-set-for-managed-code.md) | Contient des règles de détection des failles de sécurité |