---
title: La mise à jour de l’Interface utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db5be965119d1564f2a4bf8a15892af7142663e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186358"
---
# <a name="updating-the-user-interface"></a>Mise à jour de l'interface utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une fois que vous implémentez une commande, vous pouvez ajouter le code pour mettre à jour l’interface utilisateur avec l’état de vos nouvelles commandes.  
  
 Dans une application Win32 classique, le jeu de commandes peut être interrogé en continu et l’état des commandes individuelles peut être ajusté pendant que l’utilisateur consulte les. Toutefois, étant donné que le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell peut héberger un nombre illimité de VSPackages, interrogation complète risque de diminuer la réactivité, en particulier d’interrogation sur les assemblys d’interopérabilité entre le code managé et COM.  
  
### <a name="to-update-the-ui"></a>Pour mettre à jour de l’interface utilisateur  
  
1. Effectuez l’une des opérations suivantes :  
  
    - Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
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
  
    - Dans les VSPackages qui hébergent un contrôle ActiveX à l’aide du modèle d’activation sur place dans une fenêtre, il peut être plus pratique d’utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> (méthode). Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode dans le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface sont fonctionnellement équivalents. Les deux font l’environnement à interroger à nouveau l’état de toutes les commandes. En règle générale, une mise à jour n’est pas effectuée immédiatement. Au lieu de cela, une mise à jour est différée jusqu’au temps d’inactivité. L’interpréteur de commandes met en cache l’état de la commande permettant de maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquer la `DontCache` indicateur lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez l’indicateur avec précaution, car les performances peuvent diminuer.  
  
         Notez que vous pouvez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface en appelant le `QueryInterface` méthode sur un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> de l’objet ou en achetant l’interface à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implémentation](../extensibility/internals/command-implementation.md)
