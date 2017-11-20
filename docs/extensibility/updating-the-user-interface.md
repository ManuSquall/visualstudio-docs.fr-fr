---
title: "Mise à jour de l’Interface utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02bf66cba145b1d5fdaea899ca3af4ca2bcefbe1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="updating-the-user-interface"></a>Mise à jour de l'interface utilisateur
Après avoir implémenté une commande, vous pouvez ajouter le code pour mettre à jour l’interface utilisateur avec l’état de vos nouvelles commandes.  
  
 Dans une application Win32 classique, le jeu de commandes peut être interrogé en permanence et l’état des commandes individuelles peut être ajustée pendant que l’utilisateur consulte les. Toutefois, étant donné que le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell peut héberger un nombre illimité de VSPackages, interrogation étendue peut réduire les temps de réponse, en particulier d’interrogation entre les assemblys d’interopérabilité entre le code managé et COM.  
  
### <a name="to-update-the-ui"></a>Pour mettre à jour l’interface utilisateur  
  
1.  Effectuez l’une des opérations suivantes :  
  
    -   Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         Un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface peut être obtenue à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de service, comme suit.  
  
        ```csharp  
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
  
         Si le paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> est différente de zéro (`TRUE`), la mise à jour est effectuée de façon synchrone et immédiatement. Nous recommandons que vous transférez la valeur zéro (`FALSE`) pour ce paramètre aider à maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquer la `DontCache` indicateur lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez l’indicateur avec précaution, ou peuvent réduire les performances. Pour plus d’informations sur les indicateurs de commande, consultez le [élément indicateur de commande](../extensibility/command-flag-element.md) documentation.  
  
    -   Dans les VSPackages qui hébergent un contrôle ActiveX à l’aide du modèle d’activation en place dans une fenêtre, il peut être plus pratique d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> (méthode). Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface sont fonctionnellement équivalents. Les deux font l’environnement ré-interroge l’état de toutes les commandes. En règle générale, une mise à jour n’est pas effectuée immédiatement. Au lieu de cela, une mise à jour est différée jusqu'à ce que la durée d’inactivité. L’interpréteur de commandes met en cache l’état de la commande permettant de maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquer la `DontCache` indicateur lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez l’indicateur avec précaution, car les performances peuvent diminuer.  
  
         Notez que vous pouvez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface en appelant le `QueryInterface` méthode sur une <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> de l’objet ou à obtenir l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implémentation](../extensibility/internals/command-implementation.md)