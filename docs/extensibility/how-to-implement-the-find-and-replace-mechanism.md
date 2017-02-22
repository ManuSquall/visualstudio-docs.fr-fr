---
title: "Comment : impl&#233;menter la rechercher et remplacer le m&#233;canisme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - rechercher et remplacer"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Comment : impl&#233;menter la rechercher et remplacer le m&#233;canisme
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio fournit deux façons d'implémenter la zone rechercher\/les remplace.  Une solution consiste à passer une image de texte au shell et l'permet de gérer rechercher, la mise en surbrillance, et remplacer du texte.  Cela permet aux utilisateurs de spécifier plusieurs étendues de texte.  Sinon, votre VSPackage peut contrôler cette fonctionnalité elle\-même.  Dans les deux cas vous devez informer le shell sur la cible actuelle et les cibles pour tous les documents ouverts.  
  
### pour implémenter la recherche\/remplacez  
  
1.  Implémentez l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> sur l'un des objets retournés par les propriétés <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> ou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>de frame.  Si vous créez un éditeur personnalisé, vous devez implémenter cette interface dans le cadre de la classe d'éditeur personnalisée.  
  
2.  Utilisez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> pour spécifier les options que votre application prend en charge d'éditeur et pour indiquer si elles implémentent trouver d'image de texte.  
  
     Si votre application prend en charge d'éditeur présente l'image recherche, implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Sinon, implémentez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> et l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  si vous appliquez l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> et les méthodes d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> , vous pouvez simplifier vos tâches les recherchant en appelant l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> .  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>