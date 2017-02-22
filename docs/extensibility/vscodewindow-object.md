---
title: "Objet de VSCodeWindow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSCodeWindow"
helpviewer_keywords: 
  - "vues (Visual Studio SDK), les objets VSCodeWindow"
  - "Objet de VsCodeWindow"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Objet de VSCodeWindow
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une fenêtre de code est une fenêtre de document spécialisé qui peut inclure une ou plusieurs vues de texte, généralement le <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objet.  
  
 Point de vue architectural, la fenêtre de code est une fenêtre de document qui se trouve dans un cadre de fenêtre. Point de vue fonctionnel, la fenêtre de code est simplement une fenêtre de document avec des fonctionnalités supplémentaires. Dans le mode d'interface multidocument \(MDI\), la fenêtre de code est l'enfant MDI. Pour plus d'informations, consultez [Personnalisation des fenêtres de Code à l’aide de l’API héritée](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Le tableau suivant présente les interfaces dans le <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objet.  
  
|Méthode|Description|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fournit un mécanisme d'accès générique pour trouver un service qui identifie un identificateur global unique \(GUID\).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Représente un enfant d'interface \(multidocument MDI\) document multiples contenant une ou plusieurs vues de code.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Remplit un frame de fenêtre.|  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/fr-fr/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)