---
title: "CA1810 : Initialisez les champs statiques de type r&#233;f&#233;rence en ligne | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1810 : Initialisez les champs statiques de type r&#233;f&#233;rence en ligne
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type référence déclare un constructeur statique explicite.  
  
## Description de la règle  
 Lorsqu'un type déclare un constructeur statique explicite, le compilateur juste\-à\-temps \(JIT, Just\-In\-Time\) ajoute une vérification à chacun des méthodes statiques et constructeurs d'instances du type afin de garantir que le constructeur statique a été appelé précédemment.  L'initialisation statique est déclenchée lorsque de l'accès à un membre statique ou lorsqu'une instance du type est créée.  Toutefois, l'initialisation statique n'est pas déclenchée si vous déclarez une variable du type sans l'utiliser, ce qui peut s'avérer important si l'initialisation modifie l'état global.  
  
 Lorsque toutes les données statiques sont initialisées inline et lorsqu'un constructeur statique explicite n'est pas déclaré, les compilateurs de langage intermédiaire de Microsoft MSIL \(MicroSoft Intermediate Language\) ajoutent à la définition de type MSIL l'indicateur `beforefieldinit` et un constructeur statique implicite qui initialise les données statiques.  Lorsque le compilateur JIT rencontre l'indicateur `beforefieldinit`, la plupart du temps, les vérifications du constructeur statique ne sont pas ajoutées.  L'exécution de l'initialisation statique est garantie avant tout accès à des champs statiques, mais non avant l'appel à une méthode statique ou à un constructeur d'instances.  Remarquez que l'initialisation statique peut se produire n'importe quand après la déclaration d'une variable du type.  
  
 Les vérifications des constructeurs statiques peuvent diminuer les performances.  Un constructeur statique est souvent utilisé uniquement pour initialiser des champs statiques, auquel cas vous devez seulement vous assurer que l'initialisation statique se produit avant le premier accès d'un champ statique.  Le comportement de `beforefieldinit` est adapté à ceux\-ci, ainsi qu'à la plupart des autres types.  Il est inadapté uniquement lorsque l'initialisation statique affecte l'état global et lorsqu'une des conditions suivantes est vraie :  
  
-   L'incidence sur l'état global est coûteuse et n'est pas nécessaire si le type n'est pas utilisé.  
  
-   Les effets de l'état global sont accessibles sans nécessiter d'accès à un champ statique du type.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu'elles sont déclarées et supprimez le constructeur statique.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si les performances ne constituent pas une priorité, ou si les modifications de l'état global dues à une initialisation statique sont coûteuses ou si leur exécution doit être garantie avant qu'une méthode statique du type soit appelée ou une instance du type créée.  
  
## Exemple  
 L'exemple suivant présente un type, `StaticConstructor`, qui enfreint la règle et un autre, `NoStaticConstructor`, qui remplace le constructeur statique au moyen d'une initialisation inline visant à satisfaire la règle.  
  
 [!CODE [FxCop.Performance.RefTypeStaticCtor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor#1)]  
  
 Remarquez l'ajout de l'indicateur `beforefieldinit` sur la définition MSIL pour la classe `NoStaticConstructor`.  
  
  **La norme ANSI publique auto StaticConstructor étend \[mscorlib\]System.Object {} \/\/ Fin de la classe StaticConstructor. La norme ANSI publique beforefieldinit de la classe NoStaticConstructor étend \[mscorlib\]System.Object { } \/\/ Fin de la classe NoStaticConstructor**   
## Règles connexes  
 [CA2207 : Initialisez les champs statiques des types valeur en ligne](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)