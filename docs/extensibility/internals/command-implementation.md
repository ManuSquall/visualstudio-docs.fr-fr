---
title: Implémentation de commandes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c307f54deff676ce1add8c745e9d92f1bb3fd657
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342199"
---
# <a name="command-implementation"></a>Implémentation de la commande
Pour implémenter une commande dans un VSPackage, vous devez effectuer les tâches suivantes :

1. Dans le *.vsct* de fichiers, configurer un groupe de commandes et puis ajoutez la commande à celui-ci. Pour plus d’informations, consultez [fichiers Visual Studio command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Inscrire la commande avec Visual Studio.

3. Implémenter la commande.

Les sections suivantes expliquent comment inscrire et implémenter des commandes.

## <a name="register-commands-with-visual-studio"></a>Commandes de s’inscrire avec Visual Studio
 Si votre commande doit apparaître dans un menu, vous devez ajouter le <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> à votre VSPackage et les utiliser en tant que valeur le nom du menu ou son ID de ressource.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 En outre, vous devez inscrire la commande avec le <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Vous pouvez obtenir ce service à l’aide de la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> méthode si votre VSPackage est dérivée de <xref:Microsoft.VisualStudio.Shell.Package>.

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

## <a name="implement-commands"></a>Commandes de l’implémenter
 Il existe plusieurs manières d’implémenter des commandes. Si vous souhaitez une commande de menu statique, qui est une commande qui s’affiche toujours la même façon et dans le même menu, créer la commande à l’aide de <xref:System.ComponentModel.Design.MenuCommand> comme indiqué dans les exemples dans la section précédente. Pour créer une commande statique, vous devez fournir un gestionnaire d’événements qui est chargé d’exécuter la commande. Étant donné que la commande est toujours activée et visible, il est inutile de fournir son état à Visual Studio. Si vous souhaitez modifier l’état d’une commande selon certaines conditions, vous pouvez créer la commande comme une instance de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe et, dans son constructeur, fournissez un gestionnaire d’événements pour exécuter la commande et un `QueryStatus` gestionnaire pour notifier Visual Studio lorsque l’état de la commande change. Vous pouvez également implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comme partie d’une classe de commande ou, vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> si vous fournissez une commande en tant que partie d’un projet. Les deux interfaces et la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe tous les avoir des méthodes de notification de Visual Studio d’un changement de l’état d’une commande et d’autres méthodes qui fournissent l’exécution de la commande.

 Lorsqu’une commande est ajoutée au service de commande, il est une chaîne de commandes. Lorsque vous implémentez les méthodes de notification et l’exécution de statut de la commande, veillez à fournir uniquement cette commande particulière et pour transmettre tous les autres cas, une session sur les autres commandes dans la chaîne. Si vous ne parvenez pas à passer la commande (généralement en retournant <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio peut cesser de fonctionner correctement.

## <a name="querystatus-methods"></a>Méthodes QueryStatus
 Si vous implémentez soit le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> méthode ou le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> (méthode), recherchez le GUID de la commande jeu auquel appartient la commande et l’ID de la commande. Respectez les règles ci-dessous.

- Si le GUID n’est pas reconnu, votre implémentation de soit la méthode doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.

- Si votre implémentation de deux méthodes reconnaît le GUID, mais n’a pas implémenté la commande, la méthode doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

- Si votre implémentation de deux méthodes reconnaît le GUID et la commande, la méthode doit définir le champ Indicateurs de commande de chaque commande (dans le `prgCmds` paramètre) à l’aide de ce qui suit <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> indicateurs :

    - `OLECMDF_SUPPORTED`: La commande est prise en charge.

    - `OLECMDF_INVISIBLE`: La commande ne doit pas être visible.

    - `OLECMDF_LATCHED`: La commande est activée et a été activée.

    - `OLECMDF_ENABLED`: La commande est activée.

    - `OLECMDF_DEFHIDEONCTXTMENU`: La commande doit être masquée s’il apparaît dans un menu contextuel.

    - `OLECMDF_NINCHED`: La commande est un contrôleur de menu et n’est pas activée, mais sa liste déroulante n’est pas vide et qu’il est toujours disponible. (Cet indicateur est rarement utilisé.)

- Si la commande a été définie dans le *.vsct* de fichiers avec le `TextChanges` indicateur, définissez les paramètres suivants :

    - Définir le `rgwz` élément de la `pCmdText` paramètre vers le nouveau texte de la commande.

    - Définir le `cwActual` élément de la `pCmdText` paramètre à la taille de la chaîne de commande.

En outre, assurez-vous que le contexte actuel n’est pas une fonction d’automatisation, sauf si votre commande est conçu spécifiquement pour gérer les fonctions d’automatisation.

Pour indiquer que vous prenez en charge une commande particulière, retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Pour toutes les autres commandes, retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

Dans l’exemple suivant, la `QueryStatus` méthode tout d’abord permet de s’assurer que le contexte n’est pas une fonction d’automation, puis recherche le bon GUID du jeu de commandes et l’ID de commande. La commande elle-même est définie sur activé et la prise en charge. Aucune autre commande n’est pris en charge.

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
 Implémentation de la `Exec` méthode s’apparente à l’implémentation de la `QueryStatus` (méthode). Tout d’abord, assurez-vous que le contexte n’est pas une fonction d’automatisation. Ensuite, le test pour le GUID et ID de commande. Si le GUID ou ID de commande n’est pas reconnu, retournez <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

 Pour gérer la commande, exécuter et retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> si l’exécution réussit. Votre commande est responsable de la détection d’erreur et de notification ; Par conséquent, retourner un code d’erreur si l’exécution échoue. L’exemple suivant montre comment la méthode d’exécution doit être implémentée.

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

- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)