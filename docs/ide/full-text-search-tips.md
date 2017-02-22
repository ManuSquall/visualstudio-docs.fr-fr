---
title: "Conseils de recherche en texte int&#233;gral | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_search"
helpviewer_keywords: 
  - "Help Viewer 2.0, conseils de recherche en texte intégral"
  - "conseils de recherche en texte intégral [Help Viewer 2.0]"
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Conseils de recherche en texte int&#233;gral
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'une des méthodes les plus utiles pour localiser les informations dans l'Aide consiste à effectuer une recherche de texte intégral.  Pour affiner et personnaliser vos résultats, vous devez comprendre la manière dont la syntaxe affecte votre requête.  Cette rubrique fournit des conseils, des procédures, des informations de syntaxe détaillées pour vous aider à mieux maîtriser vos requêtes.  
  
## Conseils de recherche en texte intégral  
 Créez des recherches plus ciblées qui retournent uniquement les rubriques qui vous intéressent, si vous comprenez comment l'aide interprète la mise en forme que vous utilisez dans les requêtes.  Ces formats incluent des caractères spéciaux, des mots réservés et des filtres.  
  
### Indications générales  
 Le tableau suivant contient les règles de base et les directives de développement des requêtes de recherche dans l'aide.  
  
|Syntaxe|Description|  
|-------------|-----------------|  
|Respect de la casse|Les recherches ne respectent pas la casse.  Développez vos critères de recherche à l'aide de caractères majuscules ou minuscules.  Par exemple, « OLE » et « ole » retournent les mêmes résultats.|  
|Combinaisons de caractères|Vous ne pouvez pas rechercher uniquement des lettres \(a\-z\) ou nombres \(0\-9\) individuels.  Si vous essayez de rechercher certains mots réservés, tels que « et », « de » et « par », ils seront ignorés.  Pour plus d'informations, consultez "Mots ignorés dans les Recherches \(mots vides\)" plus loin dans cette rubrique.|  
|Ordre d'évaluation|Les requêtes de recherche sont évaluées de gauche à droite.|  
  
### Syntaxe de recherche  
 Si vous spécifiez une chaîne de recherche qui comprend plusieurs mots, tels que « mot1 mot2 », cette chaîne est équivalente à « word1 ET word2 », qui retourne uniquement les rubriques qui contiennent tous les mots individuels dans la chaîne de recherche.  
  
> [!IMPORTANT]
>  1.  Les recherches d'expressions ne sont pas prises en charge.  Si vous spécifiez plusieurs mots dans une chaîne de recherche, les rubriques retournées contiendront tous les mots spécifiés mais pas nécessairement l'expression exacte spécifiée.  
> 2.  Utilisez des opérateurs logiques pour spécifier la relation entre les mots dans votre expression de recherche.  Incluez des opérateurs logiques, tels que AND, OR, NOT et NEAR, pour affiner davantage votre recherche.  Par exemple, si vous recherchez « déclaration PRÈS union », les résultats de la recherche afficheront les rubriques contenant les mots « déclaration » et « union » espacés de quelques mots maximum.  Pour plus d'informations, consultez [Opérateurs logiques dans les expressions de recherche](../ide/logical-operators-in-search-expressions.md).  
  
### Filtres  
 Vous pouvez restreindre davantage les résultats de la recherche à l'aide des opérateurs de recherche avancée.  Pour filtrer les résultats d'une recherche en texte intégral, utilisez trois catégories dans l'Aide : Titre, Code, et Mot clé.  Pour plus d'informations, consultez [Opérateurs de recherche avancés dans les expressions de recherche](../ide/advanced-search-operators-in-search-expressions.md).  
  
### Classement des résultats de la recherche  
 L'algorithme de recherche applique certains critères pour aider à classer les résultats de la recherche vers le haut ou le bas de la liste des résultats.  En général :  
  
1.  Le contenu qui inclut des mots de recherche dans le titre est mieux classé que le contenu qui n'en inclut pas.  
  
2.  Le contenu qui inclut des mots de recherche très proches est mieux classé que le contenu dont les mots de recherche ne le sont pas.  
  
3.  Le contenu dont la densité des mots trouvés est plus élevée est mieux classé que le contenu dont la densité des mots trouvés est plus faible.  
  
### Mots ignorés dans les recherches \(mots d'arrêt\)  
 Les mots ou des nombres courants, parfois appelés mots vides, sont automatiquement ignorés pendant une recherche en texte intégral.  Par exemple, si vous recherchez l'expression « passer par », les résultats de la recherche afficheront les rubriques contenant le mot « passer » sans tenir compte du mot « par ».  
  
## Voir aussi  
 [Informations relatives aux paramètres régionaux](../ide/locate-information.md)   
 [Opérateurs logiques dans les expressions de recherche](../ide/logical-operators-in-search-expressions.md)