---
title: "CA1065 : Ne pas lever d&#39;exceptions dans des emplacements inattendus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1065 : Ne pas lever d&#39;exceptions dans des emplacements inattendus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode dont l'objet n'est pas de lever des exceptions lève une exception.  
  
## Description de la règle  
 Les méthodes dont l'objet n'est pas de lever des exceptions peuvent être catégorisées comme suit :  
  
-   Méthodes Property Get  
  
-   Méthodes d'accesseur d'événement  
  
-   Méthodes Equals  
  
-   Méthodes GetHashCode  
  
-   Méthodes ToString  
  
-   Constructeurs statiques  
  
-   Finaliseurs  
  
-   Méthodes Dispose  
  
-   Opérateurs d'égalité  
  
-   Opérateurs de cast implicites  
  
 Les sections suivantes traitent de ces types de méthode.  
  
### Méthodes Property Get  
 Les propriétés sont essentiellement des champs intelligents.  Elles doivent dès lors agir autant que possible comme un champ.  Les champs ne lèvent pas d'exceptions et les propriétés doivent faire de même.  Si vous avez une propriété qui lève une exception, envisagez d'en faire une méthode.  
  
 Les exceptions suivantes peuvent être levées par une méthode Property Get :  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> et tous les dérivés \(y compris <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> et tous les dérivés  
  
-   <xref:System.ArgumentException?displayProperty=fullName> \(uniquement à partir d'Indexed Get\)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException> \(uniquement à partir d'Indexed Get\)  
  
### Méthodes d'accesseur d'événement  
 Les accesseurs d'événement doivent être des opérations simples qui ne lèvent pas d'exceptions.  Un événement ne doit pas lever d'exception lorsque vous essayez d'ajouter ou de supprimer un gestionnaire d'événements.  
  
 Les exceptions suivantes sont autorisées à être levées à partir d'un accesseur d'événement :  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> et tous les dérivés \(y compris <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> et tous les dérivés  
  
-   <xref:System.ArgumentException> et dérivés  
  
### Méthodes Equals  
 Les méthodes **Equals** suivantes ne doivent pas lever d'exceptions :  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 Une méthode **Equals** doit retourner `true` ou `false` au lieu de lever une exception.  À titre d'exemple, si la méthode Equals est transmise avec deux types incompatibles, elle doit simplement retourner `false` au lieu de lever une <xref:System.ArgumentException>.  
  
### Méthodes GetHashCode  
 Les méthodes **GetHashCode** suivantes ne doivent pas, habituellement, lever d'exceptions :  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode \(t\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** doit toujours retourner une valeur.  Dans le cas contraire, vous pourriez perdre des éléments de la table de hachage.  
  
 Les versions de **GetHashCode** qui prennent un argument peuvent lever une <xref:System.ArgumentException>.  Toutefois, **Object.GetHashCode** ne doit jamais lever d'exception.  
  
### Méthodes ToString  
 Le débogueur utilise <xref:System.Object.ToString%2A?displayProperty=fullName> pour permettre l'affichage d'informations à propos des objets dans le format de chaîne.  Par conséquent, **ToString** ne doit pas modifier l'état d'un objet et lever d'exceptions.  
  
### Constructeurs statiques  
 Lever les exceptions d'un constructeur statique rend le type inutilisable dans le domaine d'application actuel.  Vous devez avoir une très bonne raison \(tel qu'un problème de sécurité\) pour lever l'exception d'un constructeur statique.  
  
### Finaliseurs  
 Lever l'exception d'un finaliseur entraîne l'échec rapide du CLR, ce qui démonte le processus.  Il convient dès lors toujours d'éviter de lever des exceptions dans un finaliseur.  
  
### Méthodes Dispose  
 Une méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ne doit pas lever d'exception.  Une méthode Dispose est souvent appelée comme composante de la logique de nettoyage dans une clause `finally`.  Par conséquent, lever explicitement une exception de la méthode Dispose oblige l'utilisateur à ajouter la gestion des exceptions dans la clause `finally`.  
  
 Le chemin d'accès **Dispose\(false\)** ne doit jamais lever d'exceptions car il est presque toujours appelé à partir d'un finaliseur.  
  
### Opérateurs d'égalité \(\=\=, \!\=\)  
 Comme les méthodes Equals, les opérateurs d'égalité doivent retourner `true` ou `false` et ne doivent pas lever d'exceptions.  
  
### Opérateurs de cast implicites  
 Comme l'utilisateur sait rarement si un opérateur de cast implicite a été appelé, une exception levée par l'opérateur de cast implicite est totalement inattendue.  Par conséquent, aucune exception ne doit être levée par des opérateurs de cast implicites.  
  
## Comment corriger les violations  
 Pour les accesseurs Get de propriété, modifiez la logique afin qu'il ne soit plus nécessaire de lever une exception ou remplacez la propriété par une méthode.  
  
 Pour tous les autres types de méthode répertoriés ci\-dessus, modifiez la logique afin qu'il ne soit plus nécessaire de lever une exception.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si la violation est provoquée par une déclaration d'exception au lieu d'une exception levée.  
  
## Règles connexes  
 [CA2219 : Ne pas lever d'exceptions dans les clauses d'exception](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)  
  
## Voir aussi  
 [Avertissements liés au design](../code-quality/design-warnings.md)