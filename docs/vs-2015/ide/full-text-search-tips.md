---
title: Conseils de recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e05c7aa16d689dd037546fe9a199f43a80b0401
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303431"
---
# <a name="full-text-search-tips"></a>Conseils de recherche en texte intégral
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’une des approches les plus utiles pour trouver des informations dans l’Aide consiste à effectuer une recherche en texte intégral. Pour affiner et personnaliser vos résultats, vous devez comprendre comment la syntaxe affecte votre requête. Cette rubrique fournit des conseils, des procédures et des informations détaillées sur la syntaxe pour vous aider à mieux écrire vos requêtes.  
  
## <a name="full-text-search-tips"></a>Conseils de recherche en texte intégral  
 Pour créer des recherches ciblées qui retournent uniquement les rubriques qui vous intéressent, vous devez comprendre comment l’Aide interprète la mise en forme que vous utilisez dans les requêtes. Ces mises en forme comprennent les caractères spéciaux, les mots réservés et les filtres.  
  
### <a name="general-guidelines"></a>Indications générales  
 Le tableau suivant présente quelques règles de base et des instructions pour le développement de requêtes de recherche dans l’Aide.  
  
|Syntaxe|Description|  
|------------|-----------------|  
|Respect de la casse|Les recherches ne respectent pas la casse. Développez vos critères de recherche à l’aide de caractères majuscules ou minuscules. Par exemple, « OLE » et « ole » retournent les mêmes résultats.|  
|Combinaisons de caractères|Vous ne pouvez pas rechercher uniquement des lettres (a-z) ou des nombres (0-9). Si vous tentez de rechercher certains mots réservés, tels que « et », « de » et « avec », ils sont ignorés. Pour plus d’informations, consultez « Mots ignorés dans les recherches (mots vides) » plus loin dans cette rubrique.|  
|Ordre d’évaluation|Les requêtes de recherche sont évaluées de gauche à droite.|  
  
### <a name="search-syntax"></a>Syntaxe de recherche  
 Si vous spécifiez une chaîne de recherche qui comprend plusieurs mots, tels que « mot1 mot2 » cette chaîne revient à taper « mot1 AND mot2 », qui retourne uniquement les rubriques qui contiennent tous les mots de la chaîne de recherche.  
  
> [!IMPORTANT]
>  1.  Les recherches d’expressions ne sont pas prises en charge. Si vous spécifiez plusieurs mots dans une chaîne de recherche, les rubriques retournées contiennent tous les mots que vous avez spécifiés, mais pas nécessairement l’expression exacte que vous avez spécifiée.  
> 2.  Utilisez des opérateurs logiques pour spécifier la relation entre les mots dans votre expression de recherche. Vous pouvez inclure des opérateurs logiques, tels que AND, OR, NOT et NEAR, pour affiner votre recherche. Par exemple, si vous recherchez « déclarer NEAR union », les résultats de recherche incluent les rubriques dans lesquelles les mots « déclarer » et « union » ne sont séparés que de quelques mots. Pour plus d’informations, consultez [Opérateurs logiques dans les expressions de recherche](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>Filtres  
 Vous pouvez restreindre davantage les résultats de la recherche en utilisant des opérateurs de recherche avancée. L’Aide inclut trois catégories que vous pouvez utiliser pour filtrer les résultats d’une recherche en texte intégral : titre, code et mot clé. Pour plus d’informations, consultez [Opérateurs de recherche avancée dans les expressions de recherche](../ide/advanced-search-operators-in-search-expressions.md).  
  
### <a name="ranking-of-search-results"></a>Classement des résultats de recherche  
 L’algorithme de recherche applique certains critères pour aider à classer les résultats de la recherche dans la liste des résultats. En général :  
  
1.  Le contenu qui comprend les mots à rechercher dans le titre a un classement plus élevé.  
  
2.  Le contenu dans lequel les mots à rechercher sont situés à proximité les uns des autres a un classement plus élevé.  
  
3.  Le contenu où la densité de mots à rechercher est supérieure a un classement plus élevé.  
  
### <a name="words-ignored-in-searches-stop-words"></a>Mots ignorés dans les recherches (mots vides)  
 Les mots ou les nombres courants, parfois appelés mots vides, sont automatiquement ignorés lors d’une recherche en texte intégral. Par exemple, si vous recherchez l’expression « pass through », les résultats de la recherche affichent les rubriques qui contiennent le mot « pass », mais pas « through ».  
  
## <a name="see-also"></a>Voir aussi  
 [Rechercher des informations](../ide/locate-information.md)   
 [Opérateurs logiques dans les expressions de recherche](../ide/logical-operators-in-search-expressions.md)



