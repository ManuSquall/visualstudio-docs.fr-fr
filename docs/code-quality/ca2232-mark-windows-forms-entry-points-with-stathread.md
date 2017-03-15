---
title: "CA2232&#160;: Marquez les points d&#39;entr&#233;e Windows Forms avec STAThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2232&#160;: Marquez les points d&#39;entr&#233;e Windows Forms avec STAThread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un assembly référence l'espace de noms <xref:System.Windows.Forms>, et son point d'entrée n'est pas marqué avec l'attribut <xref:System.STAThreadAttribute?displayProperty=fullName>.  
  
## Description de la règle  
 <xref:System.STAThreadAttribute> indique que le modèle de thread COM pour l'application est un thread cloisonné \(STA, Single\-Threaded Apartment\).  Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement.  Si l'attribut n'est pas présent, l'application utilise le modèle MTA \(Multi\-Threaded Apartment\) qui n'est pas pris en charge pour les Windows Forms.  
  
> [!NOTE]
>  Les projets [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] qui utilisent l'infrastructure d'application n'ont pas à marquer la méthode **Main** avec STAThread.  Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] le fait automatiquement.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez l'attribut <xref:System.STAThreadAttribute> au point d'entrée.  Si l'attribut <xref:System.MTAThreadAttribute?displayProperty=fullName> est présent, supprimez\-le.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si vous développez pour le .NET Compact Framework pour lequel l'attribut <xref:System.STAThreadAttribute> n'est ni utile, ni pris en charge.  
  
## Exemple  
 Les exemples suivants présentent l'utilisation correcte de <xref:System.STAThreadAttribute>.  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]