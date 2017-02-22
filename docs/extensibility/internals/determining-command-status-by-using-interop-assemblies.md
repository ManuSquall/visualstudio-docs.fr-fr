---
title: "D&#233;terminer l&#39;&#233;tat de la commande &#224; l&#39;aide des assemblys d&#39;interop&#233;rabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys PIA, déterminer l'état de commande"
  - "gestion avec les assemblys d'interopérabilité, état de commandes"
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# D&#233;terminer l&#39;&#233;tat de la commande &#224; l&#39;aide des assemblys d&#39;interop&#233;rabilit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage doit garder trace de l'état des commandes qu'il peut gérer. L'environnement ne peut pas déterminer lorsqu'une commande au sein de votre VSPackage est activée ou désactivée. Il incombe à votre package VS pour informer l'environnement à propos des États de la commande, par exemple, l'état général des commandes telles que **Couper**, **copie**, et **Coller**.  
  
## Sources de Notification d'état  
 L'environnement reçoit des informations sur les commandes via les VSPackages' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(méthode\), qui fait partie de la mise en œuvre du VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. L'environnement appelle le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode du VSPackage sous deux conditions :  
  
-   Lorsqu'un utilisateur ouvre un menu principal ou un menu contextuel \(en cliquant\), l'environnement exécute la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode sur toutes les commandes de ce menu pour déterminer leur état.  
  
-   Lorsque le VSPackage demande que l'environnement de mise à jour de l'interface utilisateur actuelle \(UI\). Dans ce cas que les commandes qui sont actuellement visibles par l'utilisateur, tels que les **Couper**, **copie**, et **Coller** de regroupement dans la barre d'outils standard, sont activés et désactivés en réponse aux actions utilisateur et du contexte.  
  
 Étant donné que l'interpréteur de commandes héberge plusieurs packages VS, les performances du shell seraient dégraderont inacceptable si cela était requis pour interroger chaque VSPackage pour déterminer l'état de la commande. Au lieu de cela, votre VSPackage doit notifier activement l'environnement lors de son interface utilisateur change au moment de la modification. Pour plus d'informations sur la notification de mise à jour, consultez la page [Mise à jour de l’Interface utilisateur](../../extensibility/updating-the-user-interface.md).  
  
## Échec de Notification d'état  
 Échec de votre package VS pour notifier l'environnement un commande de changement d'état peut placer l'interface utilisateur dans un état incohérent. N'oubliez pas que vos commandes de menu contexte ou menu peuvent être placés sur une barre d'outils de configuration par l'utilisateur. Par conséquent, mise à jour de l'interface utilisateur uniquement lorsque ouvre un menu ou le menu contextuel n'est pas suffisant.  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implémentation](../../extensibility/internals/command-implementation.md)