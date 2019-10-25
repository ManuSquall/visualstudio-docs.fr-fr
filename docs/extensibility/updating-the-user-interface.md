---
title: Mise à jour de l’interface utilisateur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718787"
---
# <a name="updating-the-user-interface"></a>Mise à jour de l'interface utilisateur
Après avoir implémenté une commande, vous pouvez ajouter du code pour mettre à jour l’interface utilisateur avec l’état de vos nouvelles commandes.

 Dans une application Win32 classique, le jeu de commandes peut être interrogé en permanence et l’état des commandes individuelles peut être ajusté lorsque l’utilisateur les affiche. Toutefois, étant donné que le shell [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut héberger un nombre illimité de VSPackages, l’interrogation étendue peut réduire la réactivité, en particulier l’interrogation entre les assemblys d’interopérabilité entre le code managé et COM.

### <a name="to-update-the-ui"></a>Pour mettre à jour l’interface utilisateur

1. Effectuez l’une des opérations suivantes :

    - Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.

         Une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> peut être obtenue à partir du service <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, comme suit.

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

         Si le paramètre de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> est différent de zéro (`TRUE`), la mise à jour est exécutée de façon synchrone et immédiatement. Nous vous recommandons de transmettre zéro (`FALSE`) pour ce paramètre afin de garantir des performances optimales. Si vous souhaitez éviter la mise en cache, appliquez l’indicateur `DontCache` lorsque vous créez la commande dans le fichier. vsct. Néanmoins, utilisez l’indicateur avec prudence ou les performances peuvent diminuer. Pour plus d’informations sur les indicateurs de commande, consultez la documentation sur les éléments de l' [indicateur de commande](../extensibility/command-flag-element.md) .

    - Dans les VSPackages qui hébergent un contrôle ActiveX à l’aide du modèle d’activation sur place dans une fenêtre, il peut être plus pratique d’utiliser la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>. La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> dans l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> et la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> dans l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> sont fonctionnellement équivalentes. Les deux font en sorte que l’environnement interroge à nouveau l’état de toutes les commandes. En règle générale, une mise à jour n’est pas effectuée immédiatement. Au lieu de cela, une mise à jour est différée jusqu’à l’heure d’inactivité. L’interpréteur de commandes met en cache l’état de la commande pour aider à maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquez l’indicateur `DontCache` lorsque vous créez la commande dans le fichier. vsct. Néanmoins, utilisez l’indicateur avec prudence, car les performances peuvent diminuer.

         Notez que vous pouvez obtenir l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> en appelant la méthode `QueryInterface` sur un objet <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> ou en obtenant l’interface à partir du service <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>.

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implémentation](../extensibility/internals/command-implementation.md)