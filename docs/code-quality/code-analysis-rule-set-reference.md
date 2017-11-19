---
title: "Règle d’analyse du code définie référence | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a0f290fa42a04ddf60a49282d2f350111076ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="code-analysis-rule-set-reference"></a>Référence d’ensemble de règles d’analyse du code
Lorsque vous configurez pour l’analyse du code managé dans les projets de code [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]vous sont présentées avec une liste des intégré *ensembles de règles*. Vous pouvez utiliser l’un des ensembles de règles standard, ou vous pouvez personnaliser une règle définie pour l’adapter à vos besoins de projet.  
  
## <a name="available-rule-sets"></a>Ensembles de règles disponibles  
 Le tableau suivant répertorie les ensembles de règles par défaut :  
  
|||  
|-|-|  
|[Ensemble de règles de toutes les règles](../code-quality/all-rules-rule-set.md)|Cet ensemble de règles contient toutes les règles. Cet ensemble de règles en cours d’exécution peut entraîner un grand nombre d’avertissements. Utilisez cette règle pour obtenir une image complète de tous les problèmes dans votre code. Cela peut vous aider à décider quels jeux sont plus appropriés pour vos projets de la règle plus ciblée.|  
|[Ensemble de règles de règles de vérification de base pour le code managé](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les erreurs de logique et les erreurs communes liées à l’utilisation des API framework. Inclure cet ensemble de règles pour développer la liste des avertissements générés par les règles minimales recommandées.|  
|[Ensemble de règles de règles de conception de base pour le code managé](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur l’application des meilleures pratiques pour rendre votre code facile à comprendre et à utiliser. Inclure cet ensemble de règles si votre projet contient du code de bibliothèque ou si vous souhaitez appliquer les meilleures pratiques pour le code facile à entretenir.|  
|[Ensemble de règles de règles de vérification étendue pour le code managé](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Ces règles développent les règles de vérification de base pour optimiser les logique et l’infrastructure d’utilisation d’erreurs. L’accent sur les scénarios spécifiques tels que les applications COM interop et mobiles. Pensez à inclure cet ensemble de règles si un de ces scénarios s’applique à votre projet ou pour trouver d’autres problèmes dans votre projet.|  
|[Ensemble de règles de règles de conception étendue pour le code managé](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Ces règles développent les règles de conception de base pour optimiser les facilité d’utilisation et de facilité de maintenance les problèmes signalés. L’accent sur l’affectation de noms. Pensez à inclure cet ensemble de règles si votre projet contient du code de bibliothèque ou si vous souhaitez appliquer les normes optimales pour l’écriture de code facile à maintenir.|  
|[Ensemble de règles des règles de globalisation pour le code managé](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes qui empêchent les données dans votre application de s’afficher correctement lorsqu’il est utilisé dans différentes langues, paramètres régionaux et cultures. Inclure cet ensemble de règles si votre application est localisée ou globalisée.|  
|[Règles de règles minimales managées défini pour le code managé](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes les plus critiques dans votre code pour lequel l’analyse du Code est le plus précis.  Ces règles sont petits nombreuses et destinées uniquement à exécuter dans les éditions de Visual Studio limitées.  Utilisez MinimumRecommendedRules.ruleset avec d’autres éditions de Visual Studio.|  
|[Ensemble de règles des règles recommandées managées pour le code managé](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes les plus critiques dans votre code, notamment les failles de sécurité potentielles, application tombe en panne et d’autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets.|  
|[Ensemble de règles des règles minimales mixtes](../code-quality/mixed-minimum-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes les plus critiques dans vos projets C++ qui prennent en charge le Common Language Runtime, notamment les failles de sécurité potentielles et les blocages d’application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.|  
|[Ensemble de règles des règles recommandées mixtes](../code-quality/mixed-recommended-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes plus courants et critiques dans vos projets C++ qui prennent en charge le Common Language Runtime, notamment les failles de sécurité potentielles, application tombe en panne et autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.  Ce groupe de règles est conçu pour être configuré avec l’édition de Visual Studio Professional et versions ultérieures.|  
|[Ensemble de règles des règles minimales natives](../code-quality/native-minimum-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes les plus critiques dans votre code natif, notamment les failles de sécurité potentielles et les blocages d’application. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.|  
|[Ensemble de règles des règles recommandées natives](../code-quality/native-recommended-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes plus fréquents et critiques dans votre code natif, notamment les failles de sécurité potentielles et les blocages d’application.  Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.  Ce groupe de règles est conçu pour fonctionner avec l’édition de Visual Studio Professional et versions ultérieures.|  
|[Ensemble de règles des règles de sécurité pour le code managé](../code-quality/security-rules-rule-set-for-managed-code.md)|Cet ensemble de règles contient toutes les règles de sécurité de Microsoft. Inclure cet ensemble de règles à maximiser le nombre de problèmes potentiels de sécurité qui sont signalés.|
