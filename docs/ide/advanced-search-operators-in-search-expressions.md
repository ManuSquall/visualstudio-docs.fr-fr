---
title: "Op&#233;rateurs de recherche avanc&#233;s dans les expressions de recherche | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, recherche de code"
  - "Help Viewer 2.0, recherche du code en fonction du langage de programmation"
  - "Help Viewer 2.0, recherche des mots clés"
  - "Help Viewer 2.0, recherche des titres"
  - "recherche du code (Help Viewer 2.0)"
  - "recherche des titres (Help Viewer 2.0)"
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Op&#233;rateurs de recherche avanc&#233;s dans les expressions de recherche
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En utilisant des opérateurs de recherche avancée, vous pouvez affiner votre recherche de contenu en créant des expressions de recherche plus complexes à partir d'expressions de recherche simples.  Comme le montre le tableau suivant, ces opérateurs limitent le contexte dans lequel une requête s'exécute.  
  
> [!WARNING]
>  Vous devez entrer les opérateurs de recherche avancée avec le signe final deux\-points et sans espace avant ce signe pour que le moteur de recherche les identifie.  
  
|Pour rechercher|Utilisation|Exemple|Résultat|  
|---------------------|-----------------|-------------|--------------|  
|Un terme dans le titre de la rubrique|titre :|title:binaryreader|Rubriques qui contiennent « binaryreader » dans leurs titres.|  
|Un terme dans un exemple de code|code :|code:readdouble|Rubriques qui contiennent « readdouble » dans un exemple de code.|  
|Un terme dans un exemple de langage de programmation spécifique|code:vb:|code:vb:string|Rubriques qui contiennent « string » dans un exemple Visual Basic.|  
|Une rubrique qui est associée à un mot clé d'index spécifique|Mot clé :|keyword:readbyte|Rubriques associées au mot clé d'index « readbyte ».|  
  
 Vous pouvez utiliser le code : l'opérateur pour rechercher le contenu sur l'un des différents langages de programmation, mais il ne retourne des résultats que pour le contenu marqué avec un langage de programmation spécifique.  Le tableau suivant répertorie les langages de programmation que cet opérateur prend en charge :  
  
|Langage de programmation|Utilisation|  
|------------------------------|-----------------|  
|Visual Basic|code:vb<br /><br /> ou<br /><br /> code:visualbasic|  
|C\#|code:c\#<br /><br /> ou<br /><br /> code:csharp|  
|C\+\+|code:cpp<br /><br /> ou<br /><br /> code:C\+\+<br /><br /> ou<br /><br /> code:cplusplus|  
|F\#|code:f\#<br /><br /> ou<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> ou<br /><br /> code:js|  
|XAML|code:xaml|  
  
## Voir aussi  
 [Opérateurs logiques dans les expressions de recherche](../ide/logical-operators-in-search-expressions.md)   
 [Conseils de recherche en texte intégral](../ide/full-text-search-tips.md)