---
title: "Mise en œuvre de la gestion des commandes pour les projets imbriqu&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets imbriqués, l'implémentation de la gestion des commandes"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Mise en œuvre de la gestion des commandes pour les projets imbriqu&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'IDE peut passer des commandes qui sont passées via <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> et les interfaces d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> aux projets imbriqués, ou les projets parents peuvent filtrer ou remplacer des commandes.  
  
> [!NOTE]
>  Seuls les commandes d'habitude gérées par le projet parent peuvent être filtrées.  Les commandes telles qu' **Build** et **Deploy** gérées par l'IDE ne peuvent pas être filtrées.  
  
 les étapes suivantes décrivent le processus pour implémenter la gestion de commande.  
  
## Procédures  
  
#### pour implémenter la gestion de commande  
  
1.  Lorsque l'utilisateur sélectionne un projet imbriqué ou un nœud dans un projet imbriqué :  
  
    1.  L'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> .  
  
     – ou –  
  
    1.  Si la commande provenait d'une fenêtre hiérarchie, telle qu'une commande de menu contextuel dans l'explorateur de solutions, l'IDE appelle la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> sur le parent du projet.  
  
2.  Le projet parent peut examiner les paramètres à passer à `QueryStatus`, tel qu' `pguidCmdGroup` et `prgCmds`, déterminer si le projet parent doit filtrer les commandes.  Si le projet parent est implémenté de filtrer les commandes, il doit définir :  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     Le projet parent doit retourner `S_OK`.  
  
     Si le projet parent ne filtre pas la commande, il doit simplement retourner `S_OK`.  Dans ce cas, l'IDE itinéraire automatiquement la commande au projet enfant.  
  
     Le projet parent ne doit pas le routage la commande au projet enfant.  L'IDE exécute cette tâche.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Commandes, Menus et barres d'outils](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [Projets d'imbrication](../../extensibility/internals/nesting-projects.md)