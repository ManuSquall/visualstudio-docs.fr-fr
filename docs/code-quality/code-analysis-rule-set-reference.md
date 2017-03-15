---
title: "R&#233;f&#233;rence d’ensemble de r&#232;gles d’analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyse du code, ensemble de règles"
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 43
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 43
---
# R&#233;f&#233;rence d’ensemble de r&#232;gles d’analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lorsque vous configurez l'analyse du code pour les projets de code managé dans [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], ou [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], une liste d'*ensembles de règles* intégrés vous est présentée.  Utilisez soit l'un des ensembles de règles standard, ou personnalisez un ensemble de règles pour répondre à vos conditions de projet.  
  
## Ensembles de règles disponibles  
 Le tableau suivant répertorie les ensembles de règles par défaut :  
  
|||  
|-|-|  
|[Ensemble de règles de toutes les règles](../code-quality/all-rules-rule-set.md)|Cet ensemble de règles contient toutes les règles.  Son exécution peut avoir pour résultat l'affichage d'un grand nombre d'avertissements.  Utilisez\-le pour obtenir une vue d'ensemble de tous les problèmes présents dans votre code.  Cela peut vous aider à choisir les ensembles de règles les plus appropriés pour vos projets.|  
|[Ensemble de règles de règles de vérification de base pour le code managé](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les erreurs de logique et les erreurs communes liées à l'utilisation des API Framework.  Ajoutez cet ensemble de règles pour allonger la liste des avertissements générés par les règles minimales recommandées.|  
|[Ensemble de règles de règles de conception de base pour le code managé](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur l'application des meilleures pratiques pour rendre votre code facile à comprendre et à utiliser.  Ajoutez cet ensemble de règles si votre projet utilise un code de bibliothèque ou si vous souhaitez appliquer les meilleures pratiques pour faciliter la gestion de votre code.|  
|[Ensemble de règles de règles de vérification étendue pour le code managé](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Ces règles s'ajoutent aux règles de vérification de base et optimisent les rapports d'erreurs de logique et d'utilisation du Framework qui sont stockées.  L'accentuation supplémentaire est placée sur les scénarios spécifiques tels que l'interopérabilité COM et les applications mobiles.  Envisagez d'ajouter cet ensemble de règles si l'un de ces scénarios s'applique à votre projet ou pour trouver d'autres problèmes dans votre projet.|  
|[Ensemble de règles de règles de conception étendue pour le code managé](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Ces règles s'ajoutent aux règles de conception de base et optimisent les rapports d'erreurs d'utilisation et de gestion.  en mettant l'accent sur l'aide liée à l'affectation de noms.  Envisagez d'inclure cet ensemble de règles si votre projet contient un code de bibliothèque ou si vous souhaitez appliquer les normes optimales en matière d'écriture et de gestion du code.|  
|[Ensemble de règles des règles de globalisation pour le code managé](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur des problèmes qui empêchent les données de votre application de s'afficher correctement lors de l'utilisation de langues, paramètres régionaux et cultures différents.  Ajoutez cet ensemble de règles si votre application est localisée ou globalisée.|  
|[Ensemble de règles des règles minimales managées pour le code managé](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes les plus critiques présents dans votre code, pour lesquels l'analyse du code est la plus précise.  Ces règles sont peu nombreuses et destinées à être exécutées seulement dans les éditions limitées de Visual Studio.  Utilisez MinimumRecommendedRules.ruleset avec les autres éditions de Visual Studio.|  
|[Ensemble de règles des règles recommandées managées pour le code managé](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Ces règles sont focalisées sur les problèmes les plus critiques présents dans votre code, comme les failles de sécurité éventuelles, les arrêts brutaux des applications et autres erreurs de logique ou de conception importantes.  Incluez cet ensemble de règles dans tous les ensembles de règles personnalisés que vous créez pour vos projets.|  
|[Ensemble de règles des règles minimales mixtes](../code-quality/mixed-minimum-rules-rule-set.md)|Ces règles couvrent les problèmes les plus critiques rencontrés dans vos projets C\+\+ qui prennent en charge le Common Language Runtime, notamment les failles de sécurité potentielles et les blocages d'applications.  Vous devez inclure cet ensemble de règles dans tout  ensemble de règles personnalisé que vous créez pour vos projets C\+\+ qui prennent en charge le Commun Language Runtime.|  
|[Ensemble de règles des règles recommandées mixtes](../code-quality/mixed-recommended-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes les plus fréquents et critiques rencontrés dans vos projets C\+\+ qui prennent en charge le Common Language Runtime, comme les failles de sécurité éventuelles, les arrêts brutaux des applications et autres erreurs de logique ou de conception importantes.  Vous devez inclure cet ensemble de règles dans tout  ensemble de règles personnalisé que vous créez pour vos projets C\+\+ qui prennent en charge le Commun Language Runtime.  Cet ensemble de règles est conçu pour être configuré avec l'édition Visual Studio Professional et ultérieure.|  
|[Ensemble de règles des règles minimales natives](../code-quality/native-minimum-rules-rule-set.md)|Ces règles couvrent les problèmes les plus critiques rencontrés dans votre code natif, notamment les failles de sécurité potentielles et les blocages d'applications.  Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.|  
|[Ensemble de règles des règles recommandées natives](../code-quality/native-recommended-rules-rule-set.md)|Ces règles sont focalisées sur les problèmes les plus fréquents et critiques rencontrés dans votre code natif, notamment les failles de sécurité potentielles et les blocages d'applications.  Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.  Cet ensemble de règles est conçu pour être configuré avec l'édition Visual Studio Professional et ultérieure.|  
|[Ensemble de règles des règles de sécurité pour le code managé](../code-quality/security-rules-rule-set-for-managed-code.md)|Cet ensemble de règles contient toutes les règles de sécurité Microsoft.  Ajoutez\-le pour optimiser le nombre de problèmes éventuels liés à la sécurité qui sont détectés.|