---
title: Opérateurs de recherche avancée dans les expressions de recherche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24bf027f2fa480f95c0f223f8a319e7977615454
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505064"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Opérateurs de recherche avancée dans les expressions de recherche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [opérateurs de recherche avancée dans les Expressions de recherche](https://docs.microsoft.com/visualstudio/ide/advanced-search-operators-in-search-expressions).  
  
À l’aide des opérateurs de recherche avancée, vous pouvez affiner votre recherche de contenu en créant des expressions de recherche plus complexes parmi ceux qui sont plus simples. Comme le montre le tableau suivant, ces opérateurs limitent le contexte dans lequel une requête s’exécute.  
  
> [!WARNING]
>  Vous devez entrer les opérateurs de recherche avancée avec un signe deux-points final et sans espace avant ce signe pour que le moteur de recherche les identifie.  
  
|Pour rechercher|Utilisez|Exemple|Résultat|  
|-------------------|---------|-------------|------------|  
|Un terme dans le titre de la rubrique|title:|title:binaryreader|Rubriques qui contiennent « binaryreader » dans leur titre.|  
|Un terme dans un exemple de code|code:|code:readdouble|Rubriques qui contiennent « readdouble » dans un exemple de code.|  
|Un terme dans un exemple de langage de programmation spécifique|code:vb:|code:vb:string|Rubriques qui contiennent « string » dans un exemple Visual Basic.|  
|Une rubrique qui est associée à un mot clé d’index spécifique|keyword:|keyword:readbyte|Rubriques qui sont associés avec le mot clé d’index « readbyte ».|  
  
 Vous pouvez utiliser l’opérateur code: pour rechercher du contenu sur l’un des différents langages de programmation, mais il ne retourne des résultats que pour le contenu marqué avec un langage de programmation spécifique. Le tableau suivant liste les langages de programmation pris en charge par cet opérateur :  
  
|Langage de programmation|Utilisez|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> ou<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> ou<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> ou<br /><br /> code:c++<br /><br /> ou<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> ou<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> ou<br /><br /> code:js|  
|XAML|code:xaml|  
  
## <a name="see-also"></a>Voir aussi  
 [Opérateurs logiques dans les expressions de recherche](../ide/logical-operators-in-search-expressions.md)   
 [Conseils de recherche en texte intégral](../ide/full-text-search-tips.md)



