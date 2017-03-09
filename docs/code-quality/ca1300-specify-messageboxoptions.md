---
title: "CA1300&#160;: Sp&#233;cifier MessageBoxOptions | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300&#160;: Sp&#233;cifier MessageBoxOptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode appelle une surcharge de la méthode <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> qui n'accepte pas d'argument <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.  
  
## Description de la règle  
 Pour afficher correctement une boîte de message pour les cultures qui utilisent un sens de lecture de droite à gauche, les membres <xref:System.Windows.Forms.MessageBoxOptions> et <xref:System.Windows.Forms.MessageBoxOptions> de l'énumération <xref:System.Windows.Forms.MessageBoxOptions> doivent être passés à la méthode <xref:System.Windows.Forms.MessageBox.Show%2A>.  Examinez la propriété <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> du contrôle conteneur pour déterminer s'il faut ou non utiliser un sens de lecture de droite à gauche.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez une surcharge de la méthode <xref:System.Windows.Forms.MessageBox.Show%2A> qui accepte un argument <xref:System.Windows.Forms.MessageBoxOptions>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la bibliothèque de code n'est pas localisée pour une culture dont le sens de lecture va de droite à gauche.  
  
## Exemple  
 L'exemple suivant présente une méthode qui affiche une boîte de message dotée des options appropriées au sens de lecture de la culture.  Un fichier de ressources, qui n'est pas présenté, est requis pour générer l'exemple.  Suivez les commentaires de l'exemple pour générer l'exemple sans fichier de ressources et tester la fonctionnalité de lecture de droite à gauche.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## Voir aussi  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ressources dans des applications de bureau](../Topic/Resources%20in%20Desktop%20Apps.md)