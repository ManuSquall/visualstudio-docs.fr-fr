---
title: "CA1045&#160;: Ne pas passer de types par r&#233;f&#233;rence | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
helpviewer_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1045&#160;: Ne pas passer de types par r&#233;f&#233;rence
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode publique ou protégée dans un type public est dotée d'un paramètre `ref` qui accepte un type primitif, un type référence ou un type valeur qui ne fait pas partie des types intégrés.  
  
## Description de la règle  
 Passer des types par référence \(en utilisant `out` ou `ref`\) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour.  Par ailleurs, la différence entre les paramètres `out` et `ref`est généralement peu comprise.  
  
 Lorsqu'un type référence est passé "par référence", la méthode projette d'utiliser le paramètre pour retourner une instance différente de l'objet. \(Passer un type référence par référence est également connu comme l'utilisation d'un pointeur double, d'un pointeur vers un pointeur, ou d'une indirection double.\) À l'aide de la convention d'appel par défaut, qui revient à passer "par valeur", un paramètre qui accepte un type référence reçoit déjà un pointeur vers l'objet.  Le pointeur, et non l'objet sur lequel il pointe, est passé par valeur.  Passer par valeur signifie que la méthode ne peut pas modifier le pointeur afin que celui\-ci pointe sur une nouvelle instance du type référence, mais qu'elle peut modifier le contenu de l'objet sur lequel il pointe.  Pour la plupart des applications, ce procédé est suffisant et débouche sur le comportement que vous souhaitez.  
  
 Si une méthode doit retourner une instance différente, utilisez la valeur de retour de la méthode pour obtenir ce résultat.  Reportez\-vous à la classe <xref:System.String?displayProperty=fullName> pour connaître diverses méthodes qui fonctionnent sur les chaînes et retournent une nouvelle instance d'une chaîne.  En utilisant ce modèle, l'appelant est libre de décider si l'objet d'origine est conservé.  
  
 Bien que les valeurs de retour soient banales et très utilisées, l'application correcte des paramètres `out` et `ref` requiert des compétences en matière de conception et de codage de niveau intermédiaire.  Les architectes de bibliothèques qui réalisent un travail de conception destiné à une audience générale ne doivent pas s'attendre à ce que les utilisateurs maîtrisent l'exploitation des paramètres `out` ou `ref`.  
  
> [!NOTE]
>  Lors de l'utilisation des paramètres qui sont des structures de grande taille, les ressources supplémentaires requises pour copier ces structures peuvent avoir des conséquences sur les performances lors du passage par valeur.  Dans ces cas, vous pouvez envisager d'utiliser des paramètres `ref` ou `out`.  
  
## Comment corriger les violations  
 Pour corriger une infraction à cette règle provoquée par un type valeur, faites en sorte que la méthode retourne l'objet comme sa valeur de retour.  Si la méthode doit retourner plusieurs valeurs, refondez sa conception afin qu'elle retourne une unique instance d'un objet qui contient les valeurs.  
  
 Pour corriger une infraction à cette règle provoquée par un type référence, assurez\-vous que le retour d'une nouvelle instance de la référence correspond bien au comportement que vous souhaitez.  Dans l'affirmative, pour y parvenir, la méthode doit utiliser sa valeur de retour.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle ; toutefois, ce design peut engendrer des problèmes d'utilisation.  
  
## Exemple  
 La bibliothèque suivante présente deux implémentations d'une classe qui génère des réponses aux commentaires de l'utilisateur.  La première implémentation \(`BadRefAndOut`\) contraint l'utilisateur de la bibliothèque à gérer trois valeurs de retour.  La seconde implémentation \(`RedesignedRefAndOut`\) simplifie l'interaction de l'utilisateur en retournant une instance d'une classe de conteneur \(`ReplyData`\) qui gère les données sous la forme d'une unité unique.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## Exemple  
 L'application suivante illustre l'interaction de l'utilisateur.  L'appel à la bibliothèque dont la conception a été refondue \(méthode `UseTheSimplifiedClass`\) est plus simple, et les informations retournées par la méthode sont gérées facilement.  La sortie des deux méthodes est identique.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## Exemple  
 La bibliothèque exemple suivante illustre l'utilisation des paramètres `ref` des types référence, ainsi qu'une manière plus efficace d'implémenter cette fonctionnalité.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## Exemple  
 L'application suivante appelle chaque méthode de la bibliothèque pour illustrer le comportement.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Modification du pointeur \- passé par valeur :**  
**12345**  
**12345**  
**Modification du pointeur \- passé par référence :**  
**12345**  
**12345 ABCDE**  
**Passage par valeur de retour :**  
**12345 ABCDE**   
## Règles connexes  
 [CA1021 : Éviter les paramètres out](../code-quality/ca1021-avoid-out-parameters.md)