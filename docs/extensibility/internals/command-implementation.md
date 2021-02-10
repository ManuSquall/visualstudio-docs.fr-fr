---
title: Implémentation de la commande | Microsoft Docs
description: En savoir plus sur l’implémentation des commandes dans Visual Studio, sur la configuration d’un groupe de commandes dans un VSPackage, l’ajout d’une commande, l’inscription de la commande et son implémentation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2031fd74a10c8725157908eaa906c1963a477526
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940109"
---
# <a name="command-implementation"></a>Implémentation de la commande
Pour implémenter une commande dans un VSPackage, vous devez effectuer les tâches suivantes :

1. Dans le fichier *. vsct* , configurez un groupe de commandes, puis ajoutez-y la commande. Pour plus d’informations, consultez [fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Inscrivez la commande avec Visual Studio.

3. Implémentez la commande.

Les sections suivantes expliquent comment inscrire et implémenter des commandes.

## <a name="register-commands-with-visual-studio"></a>Inscrire des commandes dans Visual Studio
 Si votre commande doit s’afficher dans un menu, vous devez ajouter le <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> à votre VSPackage et utiliser comme valeur le nom du menu ou son ID de ressource.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 En outre, vous devez enregistrer la commande avec le <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . Vous pouvez accéder à ce service à l’aide de la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode si votre VSPackage est dérivé de <xref:Microsoft.VisualStudio.Shell.Package> .

```
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
if ( null != mcs )
{
    // Create the command for the menu item.
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );
    mcs.AddCommand( menuItem );
}

```

## <a name="implement-commands"></a>Implémenter des commandes
 Il existe plusieurs façons d’implémenter des commandes. Si vous souhaitez une commande de menu statique, qui est une commande qui s’affiche toujours de la même façon et dans le même menu, créez la commande à l’aide de, <xref:System.ComponentModel.Design.MenuCommand> comme indiqué dans les exemples de la section précédente. Pour créer une commande statique, vous devez fournir un gestionnaire d’événements qui est responsable de l’exécution de la commande. Étant donné que la commande est toujours activée et visible, vous n’avez pas besoin de fournir son état à Visual Studio. Si vous souhaitez modifier l’état d’une commande en fonction de certaines conditions, vous pouvez créer la commande en tant qu’instance de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe et, dans son constructeur, fournir un gestionnaire d’événements pour exécuter la commande et un `QueryStatus` Gestionnaire pour notifier Visual Studio lorsque l’état de la commande change. Vous pouvez également implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> dans le cadre d’une classe de commande ou, vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> si vous fournissez une commande dans le cadre d’un projet. Les deux interfaces et la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe ont toutes des méthodes qui signalent à Visual Studio une modification de l’état d’une commande, ainsi que d’autres méthodes qui fournissent l’exécution de la commande.

 Lorsqu’une commande est ajoutée au service de commande, elle devient une chaîne de commandes. Lorsque vous implémentez la notification d’État et les méthodes d’exécution de la commande, veillez à fournir uniquement pour cette commande particulière et à transmettre tous les autres cas aux autres commandes de la chaîne. Si vous ne parvenez pas à passer la commande sur (en général, en retournant <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> ), Visual Studio peut cesser de fonctionner correctement.

## <a name="querystatus-methods"></a>Méthodes QueryStatus
 Si vous implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode ou la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> méthode, recherchez le GUID du jeu de commandes auquel appartient la commande et l’ID de la commande. Voici les conditions à respecter concernant la vidéo :

- Si le GUID n’est pas reconnu, votre implémentation de l’une ou l’autre des méthodes doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> .

- Si votre implémentation de l’une des méthodes reconnaît le GUID mais n’a pas implémenté la commande, la méthode doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

- Si votre implémentation de l’une des méthodes reconnaît à la fois le GUID et la commande, la méthode doit définir le champ des indicateurs de commande de chaque commande (dans le `prgCmds` paramètre) à l’aide des <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> indicateurs suivants :

  - `OLECMDF_SUPPORTED`: La commande est prise en charge.

  - `OLECMDF_INVISIBLE`: La commande ne doit pas être visible.

  - `OLECMDF_LATCHED`: La commande est activée et s’affiche pour être activée.

  - `OLECMDF_ENABLED`: La commande est activée.

  - `OLECMDF_DEFHIDEONCTXTMENU`: La commande doit être masquée si elle apparaît dans un menu contextuel.

  - `OLECMDF_NINCHED`: La commande est un contrôleur de menu et n’est pas activée, mais sa liste de menus déroulants n’est pas vide et est toujours disponible. (Cet indicateur est rarement utilisé.)

- Si la commande a été définie dans le fichier *. vsct* avec l' `TextChanges` indicateur, définissez les paramètres suivants :

  - Affectez `rgwz` à l’élément du `pCmdText` paramètre le nouveau texte de la commande.

  - Affectez `cwActual` à l’élément du `pCmdText` paramètre la taille de la chaîne de commande.

En outre, assurez-vous que le contexte actuel n’est pas une fonction Automation, sauf si votre commande est spécifiquement conçue pour gérer les fonctions d’automatisation.

Pour indiquer que vous prenez en charge une commande particulière, retournez <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Pour toutes les autres commandes, retournez <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

Dans l’exemple suivant, la `QueryStatus` méthode s’assure d’abord que le contexte n’est pas une fonction Automation, puis recherche le GUID et l’ID de commande corrects du jeu de commandes. La commande elle-même est configurée pour être activée et prise en charge. Aucune autre commande n’est prise en charge.

```csharp
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)
        {
            // make the Right command visible
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;
                return VSConstants.S_OK;
            }
        }
        return Constants.OLECMDERR_E_NOTSUPPORTED;
    }
}
```

## <a name="execution-methods"></a>Méthodes d’exécution
 L’implémentation de la `Exec` méthode ressemble à l’implémentation de la `QueryStatus` méthode. Tout d’abord, assurez-vous que le contexte n’est pas une fonction Automation. Ensuite, testez à la fois le GUID et l’ID de commande. Si le GUID ou l’ID de commande n’est pas reconnu, retournez <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

 Pour gérer la commande, exécutez-la et retournez <xref:Microsoft.VisualStudio.VSConstants.S_OK> si l’exécution a échoué. Votre commande est responsable de la détection des erreurs et de la notification. par conséquent, retourne un code d’erreur si l’exécution échoue. L’exemple suivant montre comment la méthode d’exécution doit être implémentée.

```csharp
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)
        {
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                //execute the command
                return VSConstants.S_OK;
            }
        }
    }
    return Constants.OLECMDERR_E_NOTSUPPORTED;
}
```

## <a name="see-also"></a>Voir aussi

- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
