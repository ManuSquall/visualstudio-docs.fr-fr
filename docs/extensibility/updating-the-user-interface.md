---
title: La mise à jour de l’Interface utilisateur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f492a7d5c42fc18ac2a5516d4549a024d37b7d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981829"
---
# <a name="updating-the-user-interface"></a>Mise à jour de l'interface utilisateur
Une fois que vous implémentez une commande, vous pouvez ajouter le code pour mettre à jour l’interface utilisateur avec l’état de vos nouvelles commandes.  
  
 Dans une application Win32 classique, le jeu de commandes peut être interrogé en continu et l’état des commandes individuelles peut être ajusté pendant que l’utilisateur consulte les. Toutefois, étant donné que le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell peut héberger un nombre illimité de VSPackages, interrogation complète risque de diminuer la réactivité, en particulier d’interrogation sur les assemblys d’interopérabilité entre le code managé et COM.  
  
### <a name="to-update-the-ui"></a>Pour mettre à jour de l’interface utilisateur  
  
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
  
         Si le paramètre de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> est différente de zéro (`TRUE`), puis la mise à jour est effectuée de façon synchrone et immédiatement. Nous vous recommandons de passer zéro (`FALSE`) pour ce paramètre aider à maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquer la `DontCache` indicateur lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez l’indicateur avec précaution, ou les performances peuvent diminuer. Pour plus d’informations sur les indicateurs de commande, consultez le [élément Command Flag](../extensibility/command-flag-element.md) documentation.  
  
    -   Dans les VSPackages qui hébergent un contrôle ActiveX à l’aide du modèle d’activation sur place dans une fenêtre, il peut être plus pratique d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> (méthode). Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface sont fonctionnellement équivalents. Les deux font l’environnement à interroger à nouveau l’état de toutes les commandes. En règle générale, une mise à jour n’est pas effectuée immédiatement. Au lieu de cela, une mise à jour est différée jusqu’au temps d’inactivité. L’interpréteur de commandes met en cache l’état de la commande permettant de maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquer la `DontCache` indicateur lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez l’indicateur avec précaution, car les performances peuvent diminuer.  
  
         Notez que vous pouvez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface en appelant le `QueryInterface` méthode sur un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> de l’objet ou en achetant l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implémentation](../extensibility/internals/command-implementation.md)