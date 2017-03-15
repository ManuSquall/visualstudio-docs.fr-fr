---
title: "CA1019&#160;: D&#233;finir des accesseurs pour les arguments d&#39;attribut | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019&#160;: D&#233;finir des accesseurs pour les arguments d&#39;attribut
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Dans son constructeur, un attribut définit des arguments qui n'ont pas de propriétés correspondantes.  
  
## Description de la règle  
 Les attributs peuvent définir des arguments obligatoires qui doivent être spécifiés lorsque vous appliquez l'attribut à une cible.  Ceux\-ci sont également appelés arguments positionnels parce qu'ils sont fournis aux constructeurs d'attributs en tant que paramètres positionnels.  Pour chaque argument obligatoire, l'attribut doit également fournir une propriété en lecture seule correspondante afin que la valeur de l'argument puisse être récupérée au moment de l'exécution.  Cette règle vérifie que, pour chaque paramètre de constructeur, vous avez défini la propriété correspondante.  
  
 Les attributs peuvent également définir des arguments facultatifs, qui sont également appelés arguments nommés.  Ces arguments sont fournis aux constructeurs d'attributs par noms et doivent disposer d'une propriété en lecture\/écriture correspondante.  
  
 Pour les arguments obligatoires et facultatifs, les propriétés correspondantes et les paramètres de constructeur doivent utiliser le même nom mais une casse différente.  Les propriétés utilisent la casse Pascal et les paramètres la casse mixte.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez une propriété en lecture seule pour chaque paramètre de constructeur qui en est dépourvu.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si vous ne souhaitez pas que la valeur de l'argument obligatoire soit récupérable.  
  
## Exemples d'attributs personnalisés  
  
### Description  
 L'exemple suivant présente deux attributs qui définissent un paramètre \(positionnel\) obligatoire.  La définition de la première implémentation de l'attribut est incorrecte.  La seconde implémentation est correcte.  
  
### Code  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## Arguments positionnels et nommés  
  
### Description  
 Les arguments positionnels et nommés indiquent clairement aux consommateurs de votre bibliothèque les arguments qui sont obligatoires pour l'attribut et ceux qui sont facultatifs.  
  
 L'exemple suivant présente l'implémentation d'un attribut qui a des arguments positionnels et des arguments nommés.  
  
### Code  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### Commentaires  
 L'exemple suivant indique comment appliquer l'attribut personnalisé à deux propriétés.  
  
### Code  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## Règles connexes  
 [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Voir aussi  
 [Attributs](../Topic/Attributes1.md)