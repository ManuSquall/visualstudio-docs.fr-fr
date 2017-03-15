---
title: "Comment : h&#233;berger un &#233;diteur dans un autre &#233;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - hébergent un éditeur imbriqué"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment : h&#233;berger un &#233;diteur dans un autre &#233;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans Visual Studio vous pouvez héberger un dans un autre éditeur en spécifiant la fenêtre d'hébergement comme fenêtre parente.  Pour cela, définissez les paramètres <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> sur le frame de fenêtre enfant.  
  
### Pour installer le frame de fenêtre pour héberger un éditeur  
  
1.  Pointez sur un éditeur en tant qu'éditeur hébergé en créant un volet de fenêtre enfant.  
  
     Ce volet est l'endroit où le texte de l'éditeur disparaît.  
  
2.  Créez l'éditeur d'hébergement à l'aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ou la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
3.  Définissez les propriétés d' <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> et d' <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> dans l'implémentation du frame de fenêtre de l'éditeur hébergé en passant ces propriétés en tant que paramètres à la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> , respectivement.  
  
     Si vous devez récupérer ces paramètres, passez ces propriétés à la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .  
  
4.  appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> pour l'éditeur contenu.  
  
     L'éditeur s'affiche dans le volet hébergé de l'éditeur contenant.  
  
## Programmation fiable  
 **concepteur d'applications** dans Visual Studio Team Edition pour les architectes est un exemple d'un frame de fenêtre d'éditeur hébergement d'un autre éditeur.  **concepteur d'applications** héberge d'autres concepteurs dans son volet droit.  Un panneau concepteur \(ou la page de **Propriétés** \) pour chacun des concepteurs contenus est ajouté au frame de fenêtre contenant.