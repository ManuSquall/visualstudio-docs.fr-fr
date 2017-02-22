---
title: "CA1009&#160;: D&#233;clarer les gestionnaires d&#39;&#233;v&#233;nements correctement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1009&#160;: D&#233;clarer les gestionnaires d&#39;&#233;v&#233;nements correctement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un délégué qui gère un événement public ou protégé n'a ni la signature, ni le type de retour, ni les noms de paramètres appropriés.  
  
## Description de la règle  
 Les méthodes du gestionnaire d'événements acceptent deux paramètres.  Le premier est de type <xref:System.Object?displayProperty=fullName> et se nomme « sender ».  Il s'agit de l'objet qui déclenche l'événement.  Le deuxième paramètre est de type <xref:System.EventArgs?displayProperty=fullName> et se nomme « e ».  Il s'agit des données qui sont associées à l'événement.  Par exemple, si l'événement est déclenché à chaque fois qu'un fichier s'ouvre, les données d'événement contiennent en général le nom du fichier.  
  
 Les méthodes du gestionnaire d'événements ne doivent pas retourner de valeur.  En langage de programmation C\#, le type de retour `void` l'indique.  Un gestionnaire d'événements peut appeler plusieurs méthodes dans plusieurs objets.  Si les méthodes étaient autorisées à retourner une valeur, plusieurs valeurs de retour se présenteraient pour chaque événement, et seule la valeur de la dernière méthode appelée serait disponible.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, corrigez la signature, le type de retour, ou les noms de paramètres du délégué.  Pour plus d'informations, consultez l'exemple suivant :  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant indique un délégué qui est adapté à la gestion des événements.  Méthodes qui peuvent être appelées par ce gestionnaire d'événements conformément à la signature spécifiée dans les règles de conception.  `AlarmEventHandler` est le nom du type du délégué.  `AlarmEventArgs` dérive de la classe de base pour les données d'événement, <xref:System.EventArgs>, et conserve les données d'événement d'alarme.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## Règles connexes  
 [CA2109 : Passez en revue les gestionnaires d'événements visibles](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## Voir aussi  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Événements et délégués](http://msdn.microsoft.com/fr-fr/d98fd58b-fa4f-4598-8378-addf4355a115)