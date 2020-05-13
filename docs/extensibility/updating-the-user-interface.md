---
title: Mise à jour de l’interface utilisateur (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698887"
---
# <a name="updating-the-user-interface"></a>Mise à jour de l'interface utilisateur
Après avoir implémenté une commande, vous pouvez ajouter du code pour mettre à jour l’interface utilisateur avec l’état de vos nouvelles commandes.

 Dans une application Win32 typique, l’ensemble de commande peut être continuellement sondé et l’état des commandes individuelles peut être ajusté au fur et à mesure que l’utilisateur les voit. Cependant, parce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que la coquille peut accueillir un nombre illimité de VSPackages, les sondages étendus pourraient diminuer la réactivité, en particulier les sondages entre les assemblages interop entre le code géré et COM.

### <a name="to-update-the-ui"></a>Pour mettre à jour l’interface utilisateur

1. Effectuez l’une des opérations suivantes :

    - Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         Une <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface peut être <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> obtenue à partir du service, comme suit.

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

         Si le paramètre de l’est <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> non-zéro (`TRUE`), alors la mise à jour est effectuée avec synchronité et immédiatement. Nous vous recommandons de`FALSE`passer zéro ( ) pour ce paramètre pour aider à maintenir de bonnes performances. Si vous voulez éviter la `DontCache` mise en cache, appliquez le drapeau lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez le drapeau avec prudence ou les performances peuvent diminuer. Pour plus d’informations sur les drapeaux de commandement, consultez la documentation sur [l’élément drapeau de commandement.](../extensibility/command-flag-element.md)

    - Dans VSPackages qui hébergent un contrôle ActiveX en utilisant le modèle d’activation <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> sur place dans une fenêtre, il pourrait être plus pratique d’utiliser la méthode. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> dans l’interface et la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> sont fonctionnellement équivalentes. Les deux provoquent la ré-interrogation de l’environnement de l’état de toutes les commandes. En règle générale, une mise à jour n’est pas effectuée immédiatement. Au lieu de cela, une mise à jour est retardée jusqu’au temps d’inactivité. La coque cache l’état de commande pour aider à maintenir de bonnes performances. Si vous voulez éviter la `DontCache` mise en cache, appliquez le drapeau lorsque vous créez la commande dans le fichier .vsct. Néanmoins, utilisez le drapeau avec prudence parce que les performances peuvent diminuer.

         Notez que vous <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> pouvez obtenir `QueryInterface` l’interface en appelant la méthode sur un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objet ou en obtenant l’interface du <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service.

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implémentation](../extensibility/internals/command-implementation.md)
