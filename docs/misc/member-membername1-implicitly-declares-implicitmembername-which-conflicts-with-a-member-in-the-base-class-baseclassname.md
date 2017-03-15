---
title: "Le membre &#39;&lt;nom_membre1&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre_implicite&gt;&#39;, qui est en conflit avec un membre dans la classe de base &#39;&lt;nom_classe_base&gt;&#39; | Microsoft Docs"
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
  - "vbc40022"
  - "bc40022"
helpviewer_keywords: 
  - "BC40022"
ms.assetid: be5bb2ee-2274-42b2-b843-179b14127b34
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_membre1&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre_implicite&gt;&#39;, qui est en conflit avec un membre dans la classe de base &#39;&lt;nom_classe_base&gt;&#39;
Le membre '\<nom\_membre1\>' déclare implicitement '\<nom\_membre\_implicite\>', qui est en conflit avec un membre dans la classe de base '\<nom\_classe\_base\>' ; le membre ne doit donc pas être déclaré 'Overloads'  
  
 Une propriété d’une classe dérivée génère un membre implicite portant le même nom qu’un membre de la classe de base et spécifie le mot clé [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 La surcharge permet de définir plusieurs versions d’une propriété ou d’une procédure dans la même classe. Vous ne pouvez pas définir une version supplémentaire d’un membre de classe de base tant que ce membre ne spécifie pas `Overloads`. Étant donné que le membre de la classe de base ne spécifie pas `Overloads`, le compilateur suppose que cette propriété occulte \([Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\) le membre de classe de base implicite.  
  
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
  
 **ID d’erreur :** BC40022  
  
### Pour corriger cette erreur  
  
-   Si vous envisagez de masquer ou d’occulter le membre de classe de base, remplacez le mot clé [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) par le mot clé [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) dans la déclaration de la propriété.  
  
-   Si vous ne souhaitez pas occulter le membre de classe de base, modifiez le nom de la propriété pour éviter les conflits de noms décrits dans le tableau précédent.  
  
## Voir aussi  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)