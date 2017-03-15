---
title: "&#39;&lt;nom_membre&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;nom_interface&gt;.&lt;nom_membre_interface&gt;&#39;, car leurs contraintes de param&#232;tre de type diff&#232;rent | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32078"
  - "BC32078"
helpviewer_keywords: 
  - "BC32078"
ms.assetid: 2c971345-edb4-491e-9202-8eb8286b66f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_membre&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;nom_interface&gt;.&lt;nom_membre_interface&gt;&#39;, car leurs contraintes de param&#232;tre de type diff&#232;rent
Une propriété, une procédure ou un événement générique tente d’implémenter un membre semblable défini dans une interface, mais les listes de contraintes sur leurs paramètres de type diffèrent.  
  
 Pour implémenter un membre d’interface, le membre d’implémentation doit non seulement avoir la même signature complète que le membre d’interface, mais aussi le même mécanisme de passage que chaque paramètre.  
  
 Pour implémenter un membre d’interface générique, le membre d’implémentation doit également avoir le même nombre de paramètres de type et la même liste de contraintes que chacun d’eux.  
  
 Pour plus d’informations sur l’implémentation d’une interface, consultez [NOT IN BUILD : Implements \(mot clé\) et Implements \(instruction\)](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be).  
  
 **ID d’erreur :** BC32078  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez implémenter le membre d’interface, modifiez les contraintes de paramètre de type pour qu’elles correspondent exactement à celles du membre d’interface.  
  
-   Si les contraintes de paramètre de type doivent rester telles que vous les avez définies, vous ne pouvez pas implémenter le membre d’interface dans cette déclaration. Supprimez le mot clé [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) de la déclaration.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NOT IN BUILD : Exemples d’implémentation d’interface dans Visual Basic](http://msdn.microsoft.com/fr-fr/50bf2a30-73b6-4126-a921-075fd6eec278)