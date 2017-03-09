---
title: "Le membre &#39;&lt;nom_membre1&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre_implicite&gt;&#39;, qui est en conflit avec un membre implicitement d&#233;clar&#233; pour le membre &#39;&lt;nom_membre2&gt;&#39; dans la classe de base &#39;&lt;nom_classe_de_base&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40018"
  - "bc40018"
helpviewer_keywords: 
  - "BC40018"
ms.assetid: 43844e55-9ce1-4b88-9aa8-839b37f30e5a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_membre1&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre_implicite&gt;&#39;, qui est en conflit avec un membre implicitement d&#233;clar&#233; pour le membre &#39;&lt;nom_membre2&gt;&#39; dans la classe de base &#39;&lt;nom_classe_de_base&gt;&#39;
Le membre '\<nom\_membre1\>' déclare implicitement '\<nom\_membre\_implicite\>', qui est en conflit avec un membre implicitement déclaré pour le membre '\<nom\_membre2\>' dans la classe de base '\<nom\_classe\_de\_base\>'. Le membre doit être déclaré 'Shadows'.  
  
 Un membre d’une classe dérivée génère un membre implicite portant le même nom qu’un membre implicite de la classe de base. Étant donné que les membres implicites ne spécifient pas [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads), le compilateur suppose que ce membre occulte \([Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\) le membre de classe de base implicite. Votre code est plus lisible, et moins sujet à erreur, si vous spécifiez explicitement le mot clé `Shadows` pour ce membre.  
  
 Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] crée des membres implicites correspondant à certains éléments de programmation que vous déclarez. Le tableau suivant récapitule ces membres implicites ou *synthétiques*.  
  
|Élément déclaré|Membres créés implicitement|  
|---------------------|---------------------------------|  
|Énumération|Membre `value__`|  
|Événement|Procédure `add_<eventname>`<br /><br /> Procédure `remove_<eventname>`<br /><br /> Champ `<eventname>Event`<br /><br /> Délégué `<eventname>EventHandler`|  
|Propriété|Procédure `get_<propertyname>`<br /><br /> Procédure `set_<propertyname>`|  
|Membre `My.Form`, membre `My.WebService` ou membre d’une classe marquée avec l’attribut <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute>|Variable `m_<variablename>``Static`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
|Variable `WithEvents`|Variable `_<variablename>`<br /><br /> Propriété `<variablename>`<br /><br /> Procédure `get_<variablename>`<br /><br /> Procédure `set_<variablename>`|  
  
 En raison du risque de conflits de noms, vous devez éviter de nommer un élément de programmation déclaré en utilisant la même forme que l’un de ces membres implicites. Par exemple, vous devez éviter tout nom d’élément qui commence par `get_` ou `set_`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40018  
  
### Pour corriger cette erreur  
  
-   Si vous envisagez de masquer ou d’occulter le membre de classe de base implicite, incluez le mot clé [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) dans la déclaration du membre de classe dérivée.  
  
-   Si vous ne souhaitez pas occulter le membre de classe de base implicite, modifiez le nom du membre de classe dérivée pour éviter les conflits avec les noms répertoriés dans le tableau précédent.  
  
## Voir aussi  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)