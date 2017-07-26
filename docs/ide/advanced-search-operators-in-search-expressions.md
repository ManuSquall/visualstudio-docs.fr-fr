---
title: "Opérateurs de recherche avancée dans les expressions de recherche | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 07ff2413503209d6ade252ac89dbfbe2589e7e85
ms.openlocfilehash: 7ad9c78134c337445a3e9180ad27234b7bcb07cc
ms.contentlocale: fr-fr
ms.lasthandoff: 06/02/2017

---
# <a name="advanced-search-operators-in-search-expressions"></a>Opérateurs de recherche avancée dans les expressions de recherche
En utilisant des opérateurs de recherche avancée dans la visionneuse d’aide, vous pouvez affiner votre recherche de contenu en créant des expressions de recherche plus complexes. Comme le montre le tableau suivant, ces opérateurs limitent le contexte dans lequel une requête s’exécute.  

> [!WARNING]
>  Vous devez entrer les opérateurs de recherche avancée avec un signe deux-points final et sans espace avant ce signe pour que le moteur de recherche les identifie.  

|Pour rechercher|Utilisez|Exemple|Résultat|  
|-------------------|---------|-------------|------------|  
|Un terme dans le titre de la rubrique|title:|title:binaryreader|Rubriques qui contiennent « binaryreader » dans leur titre.|  
|Un terme dans un exemple de code|code:|code:readdouble|Rubriques qui contiennent « readdouble » dans un exemple de code.|  
|Un terme dans un exemple de langage de programmation spécifique|code:vb:|code:vb:string|Rubriques qui contiennent « string » dans un exemple Visual Basic.|  
|Une rubrique qui est associée à un mot clé d’index spécifique|keyword:|keyword:readbyte|Rubriques associées au mot clé d’index « readbyte ».|  

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

