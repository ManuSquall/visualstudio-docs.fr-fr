---
title: "Comment : d&#233;clencher des &#233;v&#233;nements lorsque l&#39;&#233;diteur perd le Focus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - déclenchent des événements lors de la perte de focus"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Comment : d&#233;clencher des &#233;v&#233;nements lorsque l&#39;&#233;diteur perd le Focus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il est quelquefois nécessaire de déterminer quand un éditeur perd le focus sur le frame de fenêtre.  Par exemple, vous pouvez éventuellement extraire le code d'une fenêtre de code après l'éditeur ne soit plus centré sur celui\-ci.  La procédure suivante indique les étapes à suivre pour recevoir la notification du reproduire le de l'éditeur.  
  
### Pour déclencher un événement en réponse à un reproduire le de l'éditeur  
  
1.  surveillez les événements de sélection en obtenant un objet d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Appelez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> et celui\-ci votre objet d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> .  
  
3.  Dans l'appel à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, recherchez `elementid==SEID_WindowFrame`.  
  
4.  Testez le paramètre d' `varValueNew` pour deux opérations :  
  
    1.  Le frame de fenêtre que vous recherchez.  
  
    2.  Le point auquel votre programme perd la sélection à ce frame de fenêtre.