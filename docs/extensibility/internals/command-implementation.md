---
title: Mise en œuvre du commandement (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709577"
---
# <a name="command-implementation"></a>Mise en œuvre du commandement
Pour implémenter une commande dans un VSPackage, vous devez effectuer les tâches suivantes :

1. Dans le fichier *.vsct,* configurez un groupe de commandement, puis ajoutez la commande à elle. Pour plus d’informations, consultez [les fichiers visual Studio table de commande (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Enregistrez la commande auprès de Visual Studio.

3. Implémenter la commande.

Les sections suivantes expliquent comment enregistrer et mettre en œuvre les commandes.

## <a name="register-commands-with-visual-studio"></a>Enregistrez les commandes avec Visual Studio
 Si votre commande doit apparaître sur un <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> menu, vous devez ajouter le à votre VSPackage, et utiliser comme une valeur soit le nom du menu ou son ID de ressource.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 En outre, vous devez enregistrer <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>la commande auprès de la . Vous pouvez obtenir ce <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> service en utilisant la méthode <xref:Microsoft.VisualStudio.Shell.Package>si votre VSPackage est dérivé de .

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

## <a name="implement-commands"></a>Mettre en œuvre des commandes
 Il existe un certain nombre de façons de mettre en œuvre les commandes. Si vous voulez une commande de menu statique, qui est une commande qui apparaît <xref:System.ComponentModel.Design.MenuCommand> toujours de la même manière et sur le même menu, créez la commande en utilisant comme indiqué dans les exemples de la section précédente. Pour créer une commande statique, vous devez fournir un gestionnaire d’événements qui est responsable de l’exécution de la commande. Parce que la commande est toujours activée et visible, vous n’avez pas à fournir son statut à Visual Studio. Si vous souhaitez modifier l’état d’une commande en fonction de certaines <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> conditions, vous pouvez créer la commande en tant `QueryStatus` qu’instance de la classe et, dans son constructeur, fournir un gestionnaire d’événement pour exécuter la commande et un gestionnaire pour aviser Visual Studio lorsque l’état de la commande change. Vous pouvez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> également implémenter dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> cadre d’une classe de commande ou, vous pouvez implémenter si vous fournissez une commande dans le cadre d’un projet. Les deux interfaces <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> et la classe ont toutes des méthodes qui informent Visual Studio d’un changement dans le statut d’une commande, et d’autres méthodes qui fournissent l’exécution de la commande.

 Lorsqu’une commande est ajoutée au service de commandement, elle devient l’une d’une chaîne de commandes. Lorsque vous implémentez les méthodes de notification et d’exécution de l’état pour la commande, prenez soin de fournir uniquement cette commande particulière et de transmettre tous les autres cas aux autres commandes de la chaîne. Si vous ne réussissez pas à <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>transmettre la commande (généralement en revenant), Visual Studio peut cesser de fonctionner correctement.

## <a name="querystatus-methods"></a>Méthodes QueryStatus
 Si vous implémentez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> méthode ou la méthode, vérifiez le GUID de l’ensemble de commande auquel appartient la commande et l’ID de la commande. Respectez les règles ci-dessous.

- Si le GUID n’est pas reconnu, <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>votre mise en œuvre de l’une ou l’autre méthode doit revenir .

- Si votre mise en œuvre de l’une ou l’autre méthode reconnaît le GUID mais n’a pas mis en œuvre la commande, alors la méthode devrait revenir <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.

- Si votre mise en œuvre de l’une ou l’autre méthode reconnaît à la `prgCmds` fois le GUID et la commande, alors la méthode doit définir le champ de commande-drapeaux de chaque commande (dans le paramètre) en utilisant les drapeaux suivants: <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>

  - `OLECMDF_SUPPORTED`: La commande est soutenue.

  - `OLECMDF_INVISIBLE`: La commande ne doit pas être visible.

  - `OLECMDF_LATCHED`: La commande est bascule et semble avoir été vérifiée.

  - `OLECMDF_ENABLED`: La commande est activée.

  - `OLECMDF_DEFHIDEONCTXTMENU`: La commande doit être cachée si elle apparaît sur un menu raccourci.

  - `OLECMDF_NINCHED`: La commande est un contrôleur de menu et n’est pas activée, mais sa liste de menu déroulant n’est pas vide et est toujours disponible. (Ce drapeau est rarement utilisé.)

- Si la commande a été définie dans `TextChanges` le fichier *.vsct* avec le drapeau, définissez les paramètres suivants :

  - Définissez `rgwz` l’élément du `pCmdText` paramètre au nouveau texte de la commande.

  - Définissez `cwActual` l’élément du `pCmdText` paramètre à la taille de la chaîne de commande.

Aussi, assurez-vous que le contexte actuel n’est pas une fonction d’automatisation, sauf si votre commande est spécifiquement destinée à gérer les fonctions d’automatisation.

Pour indiquer que vous soutenez <xref:Microsoft.VisualStudio.VSConstants.S_OK>une commande particulière, retour . Pour toutes les autres <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>commandes, retour .

Dans l’exemple `QueryStatus` suivant, la méthode permet d’abord de s’assurer que le contexte n’est pas une fonction d’automatisation, puis trouve le GUID et l’ID de commande corrects. La commande elle-même est prête à être activée et soutenue. Aucune autre commande n’est soutenue.

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
 La mise `Exec` en œuvre `QueryStatus` de la méthode ressemble à la mise en œuvre de la méthode. Tout d’abord, assurez-vous que le contexte n’est pas une fonction d’automatisation. Ensuite, testez pour le GUID et l’ID de commande. Si l’ID GUID ou commande <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>n’est pas reconnu, retour .

 Pour gérer la commande, <xref:Microsoft.VisualStudio.VSConstants.S_OK> exécutez-la et revenez si l’exécution réussit. Votre commande est responsable de la détection et de la notification des erreurs; par conséquent, retournez un code d’erreur en cas d’échec de l’exécution. L’exemple suivant montre comment la méthode d’exécution doit être mise en œuvre.

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
