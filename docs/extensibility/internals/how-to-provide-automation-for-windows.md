---
title: "Comment : fournir l&#39;automatisation pour Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automation (Visual Studio SDK), les fenêtres Outil"
  - "fenêtres Outil, automation"
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Comment : fournir l&#39;automatisation pour Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

vous pouvez fournir l'automation pour le document et les fenêtres Outil.  Le fait de fournir l'automatisation est recommandée chaque fois que vous souhaitez rendre les objets Automation disponibles dans une fenêtre, et d'environnement ne fournit pas déjà un objet Automation prêt à l'emploi, comme c'est le cas avec une liste de tâches.  
  
## Automation pour les fenêtres Outil  
 L'environnement fournit l'automation dans une fenêtre Outil en retournant un objet standard d' <xref:EnvDTE.Window> comme indiqué dans la procédure suivante :  
  
#### Pour fournir l'automation pour les fenêtres Outil  
  
1.  Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> via l'environnement avec <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> comme paramètre d' `VSFPROPID` pour obtenir l'objet d' `Window` .  
  
2.  Lorsqu'un appelant demande un objet Automation de VSPackage\-détail pour votre fenêtre Outil via <xref:EnvDTE.Window.Object%2A>, l'environnement appelle `QueryInterface` pour `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, ou les interfaces d' `IDispatch` .  `IExtensibleObject` et `IVsExtensibleObject` fournissent une méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> .  
  
3.  Lorsque l'environnement appelle ensuite la méthode d' `GetAutomationObject` passant `NULL`, répondez en passant en arrière votre objet de VSPackage\-détail.  
  
4.  Si l'appel `QueryInterface` pour `IExtensibleObject` et de échec d' `IVsExtensibleObject` , l'environnement appelle `QueryInterface` pour `IDispatch`.  
  
## Automation pour les fenêtres de document  
 Un objet d' <xref:EnvDTE.Document> standard est également disponible à partir de l'environnement, bien qu'un éditeur peut avoir sa propre implémentation de l'objet d' `T:EnvDTE.Document` en implémentant l'interface d' `IExtensibleObject` et la réponse à `GetAutomationObject`.  
  
 En outre, un éditeur peut fournir un objet Automation de VSPackage\-détail, récupérées par le biais de la méthode d' <xref:EnvDTE.Document.Object%2A> , en implémentant les interfaces d' `IVsExtensibleObject` ou d' `IExtensibleObject` .  [Exemples d’extensibilité Visual Studio](../../misc/vssdk-samples.md) fournit un objet Automation de document\-détail RTF.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>