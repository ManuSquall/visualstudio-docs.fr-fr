---
title: "Implémentation de commandes | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bd3c23baffe767083bc541fa9e2e8718834b3ee1
ms.lasthandoff: 02/22/2017

---
# <a name="command-implementation"></a>Implémentation de la commande
Pour implémenter une commande dans un VSPackage, vous devez effectuer les tâches suivantes :  
  
1.  Dans le fichier .vsct, définir un groupe de commandes, puis ajoutez la commande à celui-ci. Pour plus d’informations, consultez [Table de commandes Visual Studio (. Les fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Enregistrer la commande avec Visual Studio.  
  
3.  Implémenter la commande.  
  
 Les sections suivantes expliquent comment s’inscrire et de mettre en œuvre des commandes.  
  
## <a name="registering-commands-with-visual-studio"></a>L’enregistrement de commandes avec Visual Studio  
 Si votre commande apparaît dans un menu, vous devez ajouter <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>à votre VSPackage et les utiliser comme valeur le nom du menu ou de son ID de ressource.</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 En outre, vous devez inscrire la commande avec le <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Vous pouvez obtenir ce service à l’aide de la <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>méthode si votre VSPackage est dérivé <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
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
  
## <a name="implementing-commands"></a>Implémentation des commandes  
 Il existe plusieurs manières d’implémenter des commandes. Si vous souhaitez une commande de menu statique, qui est une commande qui s’affiche toujours la même façon et dans le même menu, créer la commande en utilisant <xref:System.ComponentModel.Design.MenuCommand>comme indiqué dans les exemples dans la section précédente.</xref:System.ComponentModel.Design.MenuCommand> Pour créer une commande statique, vous devez fournir un gestionnaire d’événements qui est chargé d’exécuter la commande. Étant donné que la commande est toujours activé et visible, il est inutile de le fournir son état à Visual Studio. Si vous souhaitez modifier le statut d’une commande selon certaines conditions, vous pouvez créer la commande en tant qu’instance de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>classe et, dans son constructeur, fournissez un gestionnaire d’événements pour exécuter la commande et un gestionnaire d’état de la requête pour notifier Visual Studio lorsque le statut de la commande.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Vous pouvez également implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>comme partie d’une classe de commande ou, vous pouvez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Si vous fournissez une commande dans le cadre d’un projet.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Les deux interfaces et <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>toutes les classes ont des méthodes qui signalent une modification de l’état d’une commande à Visual Studio et autres méthodes qui fournissent l’exécution de la commande.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>  
  
 Lorsqu’une commande est ajoutée au service de commande, il est une chaîne de commandes. Lorsque vous implémentez les méthodes de notification et l’exécution de statut de la commande, veillez à fournir uniquement pour cette commande particulière et pour transmettre tous les autres cas sur les autres commandes de la chaîne. Si vous ne parvenez pas à passer la commande (généralement en retournant <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio cesse de fonctionner correctement.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
## <a name="query-status-methods"></a>Méthodes d’état de requête  
 Si vous implémentez un le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>(méthode) ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>(méthode), vérifiez le GUID de la commande jeu auquel appartient la commande et l’ID de la commande.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Respectez les règles ci-dessous.  
  
-   Si le GUID n’est pas reconnu, votre implémentation d’une méthode doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   Si votre implémentation de ces deux méthodes reconnaît le GUID, mais n’a pas réellement implémenté la commande, la méthode doit retourner <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   Si votre implémentation de ces deux méthodes reconnaît le GUID et la commande, alors que la méthode doit définir le champ Indicateurs de la commande de chaque commande (dans le `prgCmds` paramètre) en utilisant les indicateurs suivants :  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Si la commande est prise en charge.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Si la commande ne doit pas être visible.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Si la commande est activée et qu’il semble avoir été archivé.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Si la commande est activée.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Si la commande doit être masquée s’il apparaît dans un menu contextuel.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Si la commande est un contrôleur de menu et n’est pas activée, mais sa liste déroulante n’est pas vide et est toujours disponible.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> (Cet indicateur est rarement utilisé.)  
  
-   Si la commande a été définie dans le fichier .vsct avec le `TextChanges` indicateur, définissez les paramètres suivants :  
  
    -   Définir le `rgwz` élément de la `pCmdText` paramètre vers le nouveau texte de la commande.  
  
    -   Définir le `cwActual` élément de la `pCmdText` paramètre à la taille de la chaîne de commande.  
  
 Également vous assurer que le contexte actuel n’est pas une fonction d’automation, sauf si votre commande est conçu spécifiquement pour gérer les fonctions d’automatisation.  
  
 Pour indiquer que vous prenez en charge une commande particulière, retournée <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Pour toutes les autres commandes, retournez <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 Dans l’exemple suivant, la méthode de l’état de la requête commence par s’assurer que le contexte n’est pas une fonction d’automation, puis recherche le GUID du jeu de commandes correcte et l’ID de commande. La commande elle-même est définie pour être activé et pris en charge. Aucune autre commande n’est pris en charge.  
  
```  
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
 Implémentation de la méthode execute est semblable à l’implémentation de la méthode de l’état de la requête. Tout d’abord, vérifiez que le contexte n’est pas une fonction d’automatisation. Ensuite tester le GUID et l’ID de commande. Si le GUID ou commande ID n’est pas reconnu, retournez <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 Pour traiter la commande, exécuter et retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK>Si l’exécution réussit.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Votre commande est responsable de la détection d’erreurs et de notification ; Par conséquent, renvoyer un code d’erreur si l’exécution échoue. L’exemple suivant montre comment la méthode d’exécution doit être implémentée.  
  
```  
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
 [Comment ajouter des éléments d’Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
