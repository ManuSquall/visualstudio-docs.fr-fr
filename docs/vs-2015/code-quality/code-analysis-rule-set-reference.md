---
title: Référence d’ensemble de règles d’analyse de code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a1f91b352da5a41ec2ef81fb6067976073c787ef
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951790"
---
# <a name="code-analysis-rule-set-reference"></a>Référence d’ensemble de règles d’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous configurez l’analyse du code pour des projets de code dans managé [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], ou [!INCLUDE[vsPro](../includes/vspro-md.md)]vous sont présentées avec une liste des intégré *ensembles de règles*. Vous pouvez utiliser un des ensembles de règles standard, ou vous pouvez personnaliser un ensemble de règles à adapter à vos besoins de projet.  
  
## <a name="available-rule-sets"></a>Ensembles de règles disponibles  
 Le tableau suivant répertorie les ensembles de règles par défaut :  
  
|||  
|-|-|  
|[Ensemble de règles de toutes les règles](../code-quality/all-rules-rule-set.md)|Cet ensemble de règles contient toutes les règles. Cet ensemble de règles en cours d’exécution peut entraîner un grand nombre d’avertissements. Utilisez ce jeu de règles pour obtenir une image complète de tous les problèmes dans votre code. Cela peut vous aider à décider de la règle plus ciblée jeux sont plus appropriés pour vos projets.|  
|[Ensemble de règles de règles de vérification de base pour le code managé](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les erreurs de logique et les erreurs communes liées à l’utilisation des API framework. Inclure cet ensemble de règles pour développer la liste des avertissements générés par les règles minimales recommandées.|  
|[Ensemble de règles de règles de conception de base pour le code managé](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur l’application des meilleures pratiques pour rendre votre code facile à comprendre et utiliser. Inclure cet ensemble de règles si votre projet inclut le code de bibliothèque ou si vous souhaitez appliquer les meilleures pratiques pour le code facile à entretenir.|  
|[Ensemble de règles de règles de vérification étendue pour le code managé](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Ces règles développent les règles de vérification de base afin d’optimiser les erreurs de l’utilisation de logique et framework qui sont signalés. Accentuation supplémentaire est placée sur les scénarios spécifiques tels que les applications COM interop et les appareils mobiles. Envisagez d’inclure cet ensemble de règles si un de ces scénarios s’applique à votre projet ou pour trouver d’autres problèmes dans votre projet.|  
|[Ensemble de règles de règles de conception étendue pour le code managé](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Ces règles développent les règles de conception de base pour optimiser les problèmes de facilité d’utilisation et la facilité de gestion qui sont signalés. Accentuation supplémentaire est placée sur les règles de dénomination. Envisagez d’inclure cet ensemble de règles si votre projet inclut le code de bibliothèque ou si vous souhaitez appliquer les normes la plus élevées pour l’écriture de code plus facile à gérer.|  
|[Ensemble de règles des règles de globalisation pour le code managé](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes qui empêchent les données de votre application de s’afficher correctement lorsqu’il est utilisé dans différentes langues, paramètres régionaux et cultures. Inclure cet ensemble de règles si votre application est localisée ou globalisée.|  
|[Ensemble de règles des règles minimales managées pour le code managé](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes les plus critiques présents dans votre code pour laquelle l’analyse du Code est le plus précis.  Ces règles sont petits nombreuses et ils sont destinés uniquement à exécuter dans les éditions de Visual Studio limitées.  Utilisez MinimumRecommendedRules.ruleset avec d’autres éditions de Visual Studio.|  
|[Ensemble de règles des règles recommandées managées pour le code managé](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes les plus critiques dans votre code, notamment les failles de sécurité potentielles, les blocages d’application et les autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets.|  
|[Ensemble de règles des règles minimales mixtes](../code-quality/mixed-minimum-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes les plus critiques présents dans vos projets C++ qui prennent en charge le Common Language Runtime, y compris les failles de sécurité potentielles et les blocages d’application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.|  
|[Ensemble de règles des règles recommandées mixtes](../code-quality/mixed-recommended-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes plus courants et critiques dans vos projets C++ qui prennent en charge le Common Language Runtime, y compris les failles de sécurité potentielles, les blocages d’application et les autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.  Ce groupe de règles est conçu pour être configuré avec l’édition de Visual Studio Professional et versions ultérieures.|  
|[Ensemble de règles des règles minimales natives](../code-quality/native-minimum-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes les plus critiques présents dans votre code natif, notamment les failles de sécurité potentielles et les blocages d’application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.|  
|[Ensemble de règles des règles recommandées natives](../code-quality/native-recommended-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes plus fréquents et critiques dans votre code natif, notamment les failles de sécurité potentielles et les blocages d’application.  Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.  Ce groupe de règles est conçu pour fonctionner avec l’édition de Visual Studio Professional et versions ultérieures.|  
|[Ensemble de règles des règles de sécurité pour le code managé](../code-quality/security-rules-rule-set-for-managed-code.md)|Cet ensemble de règles contient toutes les règles de sécurité de Microsoft. Inclure cet ensemble de règles à maximiser le nombre de problèmes potentiels de sécurité qui sont signalés.|
