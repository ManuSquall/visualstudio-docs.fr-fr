---
title: "Mise &#224; jour de l’Interface utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces utilisateur, mise à jour"
  - "commandes, mise à jour de l’interface utilisateur"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 41
---
# Mise &#224; jour de l’Interface utilisateur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une fois que vous implémentez une commande, vous pouvez ajouter le code pour mettre à jour l’interface utilisateur avec l’état de vos nouvelles commandes.  
  
 Dans une application Win32 standard, le jeu de commandes peut être interrogé en continu et l’état des commandes individuelles peut être ajusté pendant que l’utilisateur consulte les. Toutefois, étant donné que le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell peut héberger un nombre illimité de packages VS, étendue interrogation peut diminuer la réactivité, en particulier l’interrogation sur les assemblys d’interopérabilité entre le code managé et COM.  
  
### Pour mettre à jour l’interface utilisateur  
  
1.  Effectuez l’une des opérations suivantes :  
  
    -   Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         Un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface peut être obtenue à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de service, comme suit.  
  
        ```c#  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Si le paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> est différente de zéro \(`TRUE`\), puis la mise à jour est effectuée de façon synchrone et immédiatement. Nous vous recommandons de passer zéro \(`FALSE`\) pour ce paramètre afin de maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquer la `DontCache` indicateur lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez l’indicateur avec précaution ou diminuer les performances. Pour plus d’informations sur les indicateurs de commande, consultez le [Élément indicateur de commande](../extensibility/command-flag-element.md) documentation.  
  
    -   Dans les packages VS qui hébergent un contrôle ActiveX à l’aide du modèle d’activation en place dans une fenêtre, il peut être plus pratique d’utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface sont fonctionnellement équivalents. Les deux font l’environnement à interroger à nouveau l’état de toutes les commandes. En règle générale, une mise à jour n’est pas exécutée immédiatement. Au lieu de cela, une mise à jour est retardée jusqu'à ce que le temps d’inactivité. L’interpréteur de commandes met en cache l’état de la commande permettant de maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquer la `DontCache` indicateur lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez l’indicateur avec précaution, car les performances peuvent diminuer.  
  
         Notez que vous pouvez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface en appelant le `QueryInterface` méthode sur une <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> de l’objet ou en achetant l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service.  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implémentation](../extensibility/internals/command-implementation.md)