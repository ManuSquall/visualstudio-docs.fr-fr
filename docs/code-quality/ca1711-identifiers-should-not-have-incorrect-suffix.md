---
title: "CA1711&#160;: Les identificateurs ne doivent pas porter un suffixe incorrect | Microsoft Docs"
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
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711&#160;: Les identificateurs ne doivent pas porter un suffixe incorrect
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le suffixe d'un identificateur est inexact.  
  
## Description de la règle  
 Par convention, seuls les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou les types dérivés de ces types, doivent se terminer par des suffixes réservés spécifiques.  Les autres noms de types ne doivent pas utiliser ces suffixes réservés.  
  
 Le tableau suivant répertorie les suffixes réservés et les types et interfaces de base auxquels ils sont associés.  
  
|Suffixe|Type de base\/interface|  
|-------------|-----------------------------|  
|Attribut|<xref:System.Attribute?displayProperty=fullName>|  
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Délégué de gestionnaires d'événements|  
|Exception|<xref:System.Exception?displayProperty=fullName>|  
|Autorisation|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Stream|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 De plus, les suffixes suivants **ne doivent pas** être utilisés :  
  
-   Délégué  
  
-   Enum  
  
-   Impl \- utiliser 'Principal' à la place  
  
-   Ex ou suffixe semblable pour le distinguer d'une version antérieure du même type  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Supprimez le suffixe du nom du type.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas d'avertissement pour cette règle à moins que le suffixe n'ait une signification non équivoque dans le domaine de l'application.  
  
## Règles connexes  
 [CA1710 : Les identificateurs doivent être dotés d'un suffixe correct](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)  
  
## Voir aussi  
 [Attributs](../Topic/Attributes1.md)   
 [Événements et délégués](http://msdn.microsoft.com/fr-fr/d98fd58b-fa4f-4598-8378-addf4355a115)