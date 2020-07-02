---
title: Référence de l’ensemble de règles d’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e480869d5b13ecc051deaa97b0bfd2532519d18f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535718"
---
# <a name="code-analysis-rule-set-reference"></a>Référence d’ensemble de règles d’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand vous configurez l’analyse du code pour les projets de code managé dans [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] , [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , ou [!INCLUDE[vsPro](../includes/vspro-md.md)] une liste d' *ensembles de règles*intégrés s’affiche. Vous pouvez utiliser l’un des ensembles de règles autonomes, ou vous pouvez personnaliser un ensemble de règles en fonction des exigences de votre projet.

## <a name="available-rule-sets"></a>Ensembles de règles disponibles
 Le tableau suivant répertorie les ensembles de règles par défaut :

|Élément|Valeur|
|-|-|
|[Ensemble de règles de toutes les règles](../code-quality/all-rules-rule-set.md)|Cet ensemble de règles contient toutes les règles. L’exécution de cet ensemble de règles peut entraîner le signalement d’un grand nombre d’avertissements. Utilisez cet ensemble de règles pour obtenir une image complète de tous les problèmes dans votre code. Cela peut vous aider à déterminer quel ensemble de règles plus ciblées est le plus approprié à s’exécuter pour vos projets.|
|[Ensemble de règles de règles de vérification de base pour le code managé](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Ces règles se concentrent sur les erreurs logiques et les erreurs courantes dans l’utilisation des API de Framework. Incluez cet ensemble de règles pour développer la liste des avertissements signalés par les règles minimales recommandées.|
|[Ensemble de règles de règles de conception de base pour le code managé](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Ces règles sont axées sur l’application des meilleures pratiques pour faciliter la compréhension et l’utilisation de votre code. Incluez cet ensemble de règles si votre projet inclut du code de bibliothèque ou si vous souhaitez appliquer les meilleures pratiques pour faciliter la gestion du code.|
|[Ensemble de règles de règles de vérification étendue pour le code managé](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Ces règles s’étendent sur les règles de vérification de base pour optimiser les erreurs d’utilisation de la logique et de l’infrastructure qui sont signalées. Une importance supplémentaire est placée sur des scénarios spécifiques tels que les COM Interop et les applications mobiles. Pensez à inclure cet ensemble de règles si l’un de ces scénarios s’applique à votre projet ou pour rechercher des problèmes supplémentaires dans votre projet.|
|[Ensemble de règles de règles de conception étendue pour le code managé](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Ces règles s’étendent sur les règles de conception de base pour optimiser les problèmes de facilité d’utilisation et de maintenance signalés. Une mise en évidence supplémentaire est placée dans les instructions d’affectation de noms. Pensez à inclure cet ensemble de règles si votre projet inclut du code de bibliothèque ou si vous souhaitez appliquer les normes les plus élevées pour écrire du code gérable.|
|[Ensemble de règles des règles de globalisation pour le code managé](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Ces règles se concentrent sur les problèmes qui empêchent les données de votre application de s’afficher correctement quand elles sont utilisées dans différentes langues, paramètres régionaux et cultures. Incluez cet ensemble de règles si votre application est localisée ou globalisée.|
|[Ensemble de règles des règles minimales managées pour le code managé](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Ces règles se concentrent sur les problèmes les plus critiques de votre code pour lesquels l’analyse du code est la plus précise.  Ces règles sont peu nombreuses et sont destinées uniquement à s’exécuter dans les éditions limitées de Visual Studio.  Utilisez MinimumRecommendedRules. RuleSet avec d’autres éditions de Visual Studio.|
|[Ensemble de règles des règles recommandées managées pour le code managé](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Ces règles se concentrent sur les problèmes les plus critiques de votre code, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs importantes de logique et de conception. Vous devez inclure cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets.|
|[Ensemble de règles des règles minimales mixtes](../code-quality/mixed-minimum-rules-rule-set.md)|Ces règles se concentrent sur les problèmes les plus critiques dans vos projets C++ qui prennent en charge le Common Language Runtime, y compris les failles de sécurité potentielles et les blocages d’application. Vous devez inclure cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.|
|[Ensemble de règles des règles recommandées mixtes](../code-quality/mixed-recommended-rules-rule-set.md)|Ces règles sont axées sur les problèmes les plus courants et critiques dans vos projets C++ qui prennent en charge le Common Language Runtime, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs de conception et logique importantes. Vous devez inclure cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.  Cet ensemble de règles est conçu pour être configuré avec l’édition Visual Studio Professional et versions ultérieures.|
|[Ensemble de règles des règles minimales natives](../code-quality/native-minimum-rules-rule-set.md)|Ces règles se concentrent sur les problèmes les plus critiques dans votre code natif, y compris les failles de sécurité potentielles et les pannes d’application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.|
|[Ensemble de règles des règles recommandées natives](../code-quality/native-recommended-rules-rule-set.md)|Ces règles se concentrent sur les problèmes les plus critiques et les plus courants dans votre code natif, y compris les failles de sécurité potentielles et les pannes d’application.  Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.  Cet ensemble de règles est conçu pour fonctionner avec Visual Studio Professional Edition et versions ultérieures.|
|[Ensemble de règles des règles de sécurité pour le code managé](../code-quality/security-rules-rule-set-for-managed-code.md)|Cet ensemble de règles contient toutes les règles de sécurité Microsoft. Incluez cet ensemble de règles pour maximiser le nombre de problèmes de sécurité potentiels signalés.|
