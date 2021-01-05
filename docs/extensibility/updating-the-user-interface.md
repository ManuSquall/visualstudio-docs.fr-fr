---
title: Mise à jour de l’interface utilisateur | Microsoft Docs
description: Découvrez comment ajouter du code pour mettre à jour l’interface utilisateur après avoir implémenté une nouvelle commande dans votre VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: fae228b3fab1e25f92c02da2512abdd78edda0db
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716027"
---
# <a name="updating-the-user-interface"></a>Mise à jour de l'interface utilisateur
Après avoir implémenté une commande, vous pouvez ajouter du code pour mettre à jour l’interface utilisateur avec l’état de vos nouvelles commandes.

 Dans une application Win32 classique, le jeu de commandes peut être interrogé en permanence et l’état des commandes individuelles peut être ajusté lorsque l’utilisateur les affiche. Toutefois, dans la mesure où l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interpréteur de commandes peut héberger un nombre illimité de VSPackages, l’interrogation étendue peut réduire la réactivité, en particulier l’interrogation entre les assemblys d’interopérabilité entre le code managé et com.

### <a name="to-update-the-ui"></a>Pour mettre à jour l’interface utilisateur

1. Effectuez l’une des opérations suivantes :

    - Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         Une <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface peut être obtenue à partir du <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, comme suit.

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

         Si le paramètre de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> est différent de zéro ( `TRUE` ), la mise à jour est effectuée de façon synchrone et immédiate. Nous vous recommandons de passer zéro ( `FALSE` ) pour ce paramètre afin de garantir des performances optimales. Si vous souhaitez éviter la mise en cache, appliquez l' `DontCache` indicateur lorsque vous créez la commande dans le fichier. vsct. Néanmoins, utilisez l’indicateur avec prudence ou les performances peuvent diminuer. Pour plus d’informations sur les indicateurs de commande, consultez la documentation sur les éléments de l' [indicateur de commande](../extensibility/command-flag-element.md) .

    - Dans les VSPackages qui hébergent un contrôle ActiveX à l’aide du modèle d’activation sur place dans une fenêtre, il peut être plus pratique d’utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> méthode dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface et la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> méthode dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface sont fonctionnellement équivalentes. Les deux font en sorte que l’environnement interroge à nouveau l’état de toutes les commandes. En règle générale, une mise à jour n’est pas effectuée immédiatement. Au lieu de cela, une mise à jour est différée jusqu’à l’heure d’inactivité. L’interpréteur de commandes met en cache l’état de la commande pour aider à maintenir de bonnes performances. Si vous souhaitez éviter la mise en cache, appliquez l' `DontCache` indicateur lorsque vous créez la commande dans le fichier. vsct. Néanmoins, utilisez l’indicateur avec prudence, car les performances peuvent diminuer.

         Notez que vous pouvez obtenir l' <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface en appelant la `QueryInterface` méthode sur un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objet ou en obtenant l’interface à partir du <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> service.

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implémentation](../extensibility/internals/command-implementation.md)
