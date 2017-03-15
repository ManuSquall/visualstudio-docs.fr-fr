---
title: "CA1021&#160;: &#201;viter les param&#232;tres out | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1021"
  - "AvoidOutParameters"
helpviewer_keywords: 
  - "AvoidOutParameters"
  - "CA1021"
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1021&#160;: &#201;viter les param&#232;tres out
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOutParameters|  
|CheckId|CA1021|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode publique ou protégée dans un type public dispose d'un paramètre `out`.  
  
## Description de la règle  
 Passer des types par référence \(en utilisant `out` ou `ref`\) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour.  Par ailleurs, la différence entre les paramètres `out` et `ref`est généralement peu comprise.  
  
 Lorsqu'un type référence est passé "par référence", la méthode projette d'utiliser le paramètre pour retourner une instance différente de l'objet.  Passer un type référence par référence est également connu comme l'utilisation d'un pointeur double, d'un pointeur vers un pointeur, ou d'une indirection double.  En utilisation la convention d'appel par défaut, qui revient à passer "par valeur", un paramètre qui accepte un type référence reçoit déjà un pointeur vers l'objet.  Le pointeur, et non l'objet sur lequel il pointe, est passé par valeur.  Passer par valeur signifie que la méthode ne peut pas modifier le pointeur afin que celui\-ci pointe vers une nouvelle instance du type référence.  Toutefois, elle peut modifier le contenu de l'objet sur lequel il pointe.  Pour la plupart des applications, ce procédé est suffisant et débouche sur le comportement désiré.  
  
 Si une méthode doit retourner une instance différente, utilisez la valeur de retour de la méthode pour obtenir ce résultat.  Reportez\-vous à la classe <xref:System.String?displayProperty=fullName> pour connaître diverses méthodes qui fonctionnent sur les chaînes et retournent une nouvelle instance d'une chaîne.  Lorsque ce modèle est utilisé, l'appelant doit décider si l'objet d'origine est ou non conservé.  
  
 Bien que les valeurs de retour soient banales et très utilisées, l'application correcte des paramètres `out` et `ref` requiert des compétences en matière de conception et de codage de niveau intermédiaire.  Les architectes de bibliothèques qui réalisent un travail de conception destiné à une audience générale ne doivent pas s'attendre à ce que les utilisateurs maîtrisent l'exploitation des paramètres `out` ou `ref`.  
  
## Comment corriger les violations  
 Pour corriger une infraction à cette règle provoquée par un type valeur, faites en sorte que la méthode retourne l'objet comme sa valeur de retour.  Si la méthode doit retourner plusieurs valeurs, refondez sa conception afin qu'elle retourne une unique instance d'un objet qui contient les valeurs.  
  
 Pour corriger une infraction à cette règle provoquée par un type référence, assurez\-vous que le retour d'une nouvelle instance de la référence correspond bien au comportement désiré.  Dans l'affirmative, pour y parvenir, la méthode doit utiliser sa valeur de retour.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle.  Toutefois, cette conception peut engendre des problèmes d'utilisation.  
  
## Exemple  
 La bibliothèque suivante présente deux implémentations d'une classe qui génère des réponses aux commentaires d'un utilisateur.  La première implémentation \(`BadRefAndOut`\) contraint l'utilisateur de la bibliothèque à gérer trois valeurs de retour.  La seconde implémentation \(`RedesignedRefAndOut`\) simplifie l'interaction de l'utilisateur en retournant une instance d'une classe de conteneur \(`ReplyData`\) qui gère les données sous la forme d'une unité unique.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## Exemple  
 L'application suivante illustre l'interaction de l'utilisateur.  L'appel à la bibliothèque dont la conception a été refondue \(méthode `UseTheSimplifiedClass`\) est plus simple, et les informations retournées par la méthode sont gérées facilement.  La sortie des deux méthodes est identique.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## Exemple  
 La bibliothèque exemple suivante illustre l'utilisation des paramètres `ref` des types référence, ainsi qu'une manière plus efficace d'implémenter cette fonctionnalité.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## Exemple  
 L'application suivante appelle chaque méthode de la bibliothèque pour illustrer le comportement.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Modification du pointeur \- passé par valeur :**  
**12345**  
**12345**  
**Modification du pointeur \- passé par référence :**  
**12345**  
**12345 ABCDE**  
**Passage par valeur de retour :**  
**12345 ABCDE**   
## Méthodes du modèle Try  
  
### Description  
 Les méthodes qui implémentent le modèle **Try\<quelque chose\> tel que**<xref:System.Int32.TryParse%2A?displayProperty=fullName> ne déclenchent pas cette violation.  L'exemple suivant présente une structure \(type valeur\) qui implémente la méthode <xref:System.Int32.TryParse%2A?displayProperty=fullName>.  
  
### Code  
 [!CODE [FxCop.Design.TryPattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern#1)]  
  
## Règles connexes  
 [CA1045 : Ne pas passer de types par référence](../code-quality/ca1045-do-not-pass-types-by-reference.md)