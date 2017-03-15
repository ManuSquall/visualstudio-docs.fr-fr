---
title: "CA2109&#160;: Passez en revue les gestionnaires d&#39;&#233;v&#233;nements visibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2109&#160;: Passez en revue les gestionnaires d&#39;&#233;v&#233;nements visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode de gestion d'événements publique ou protégée a été détectée.  
  
## Description de la règle  
 Une méthode de gestion d'événements visible de l'extérieur présente un problème de sécurité qui requiert une révision.  
  
 Les méthodes de gestion d'événements ne doivent pas être exposées sauf nécessité absolue.  Un gestionnaire d'événements, un type délégué, qui appelle la méthode exposée peut être ajouté à tout événement tant que le gestionnaire et les signatures d'événement correspondent.  Les événements peuvent être potentiellement déclenchés par tout code et sont fréquemment déclenchés par un code système doté d'une confiance très élevée, en réponse à des actions de l'utilisateur, telles qu'un clic sur un bouton.  L'ajout d'une vérification de la sécurité à une méthode de gestion d'événements n'empêche pas un code d'enregistrer un gestionnaire d'événements qui appelle la méthode.  
  
 Une demande ne peut pas protéger de manière fiable une méthode appelée par un gestionnaire d'événements.  Les demandes de sécurité contribuent à protéger le code contre les appelants non approuvés par l'examen de ces derniers sur la pile des appels.  Un code qui ajoute un gestionnaire d'événements à un événement n'est pas nécessairement présent sur la pile des appels lorsque les méthodes de ce gestionnaire s'exécutent.  Par conséquent, la pile des appels peut avoir uniquement des appelants d'un niveau de confiance élevé lorsque la méthode de gestionnaire d'événements est appelée.  Cela provoque la réussite des demandes faites par la méthode de gestionnaire d'événements.  De plus, l'autorisation demandée peut être déclarée lorsque la méthode est appelée.  Pour ces raisons, le risque lié à la correction d'une violation de cette règle ne peut être évalué qu'après avoir passé en revue la méthode de gestion d'événements.  Lorsque vous passez en revue votre code, tenez compte des problèmes suivants :  
  
-   Est\-ce que votre gestionnaire d'événements exécute des opérations dangereuses ou exploitables, telles que la déclaration d'autorisations ou la suppression de l'autorisation d'un code non managé ?  
  
-   En termes de sécurité, quelles menaces peuvent pénétrer votre code ou en sortir sachant qu'il peut s'exécuter n'importe quand uniquement avec des appelants dotés d'une confiance très élevée sur la pile ?  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, révisez la méthode et évaluez les éléments suivants :  
  
-   Pouvez\-vous rendre la méthode de gestion d'événements non publique ?  
  
-   Pouvez\-vous placer toutes les fonctionnalités dangereuses hors du gestionnaire d'événements ?  
  
-   Si une demande de sécurité est imposée, peut\-elle l'être d'une autre manière ?  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement après une révision de sécurité méticuleuse afin de s'assurer que votre code ne constitue pas une menace pour la sécurité.  
  
## Exemple  
 Le code suivant présente une méthode de gestion d'événements qui peut être employée à des fins préjudiciables par un code malveillant.  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## Voir aussi  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/fr-fr/324c14f8-54ff-494d-9fd1-bfd20962c8ba)