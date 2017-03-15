---
title: "Le membre &lt;nom_membre &gt;&#39; d&#233;finit implicitement un membre &#39;&lt;nom_membre_implicite&gt;&#39; qui porte le m&#234;me nom qu’un param&#232;tre de type | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC32070"
  - "vbc32070"
helpviewer_keywords: 
  - "BC32070"
ms.assetid: cc0b3fcf-c141-47e2-9b33-d2b91c8bf2d6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &lt;nom_membre &gt;&#39; d&#233;finit implicitement un membre &#39;&lt;nom_membre_implicite&gt;&#39; qui porte le m&#234;me nom qu’un param&#232;tre de type
Un membre d’une classe générique génère un membre implicite portant le même nom qu’un paramètre de type pour la classe.  
  
 Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] crée des membres implicites correspondant à certains éléments de programmation que vous déclarez. Le tableau suivant récapitule ces membres implicites ou *synthétiques*.  
  
|Élément déclaré|Membres créés implicitement|  
|---------------------|---------------------------------|  
|Énumération|Membre `value__`|  
|Événement|Procédure `add_<eventname>`<br /><br /> Procédure `remove_<eventname>`<br /><br /> Champ `<eventname>Event`<br /><br /> Délégué `<eventname>EventHandler`|  
|Propriété|Procédure `get_<propertyname>`<br /><br /> Procédure `set_<propertyname>`|  
|Variable de collection `My.`|Variable `m_<variablename>` `Static`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
|Variable `WithEvents`|Variable `_<variablename>`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
  
 En raison du risque de conflits de noms, vous devez éviter de nommer un élément de programmation déclaré en utilisant la même forme que l’un de ces membres implicites. Par exemple, vous devez éviter tout nom d’élément qui commence par `get_` ou `set_`.  
  
 **ID d’erreur :** BC32070  
  
### Pour corriger cette erreur  
  
-   Si le nom du paramètre de type est flexible, modifiez\-le pour éviter les conflits avec les noms répertoriés dans le tableau précédent.  
  
-   Si le paramètre de type doit conserver son nom, modifiez le nom du membre de classe pour éviter les conflits avec les noms répertoriés dans le tableau précédent.  
  
## Voir aussi  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)