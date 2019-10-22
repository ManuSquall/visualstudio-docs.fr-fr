---
title: Abonnement à un événement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647928"
---
# <a name="subscribing-to-an-event"></a>Abonnement à un événement
Cette procédure pas à pas explique comment créer une fenêtre outil qui répond aux événements dans une table de document en cours d’exécution (RDT). Une fenêtre outil héberge un contrôle utilisateur qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> connecte l’interface aux événements.

## <a name="prerequisites"></a>Configuration requise
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Abonnement à des événements RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Pour créer une extension avec une fenêtre outil

1. Créez un projet nommé **RDTExplorer** à l’aide du modèle VSIX, puis ajoutez un modèle d’élément de fenêtre outil personnalisé nommé **RDTExplorerWindow**.

     Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Pour s’abonner à des événements RDT

1. Ouvrez le fichier RDTExplorerWindowControl. xaml et supprimez le bouton nommé `button1`. Ajoutez un contrôle <xref:System.Windows.Forms.ListBox> et acceptez le nom par défaut. L’élément Grid doit se présenter comme suit :

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Ouvrez le fichier RDTExplorerWindow.cs en mode Code. Ajoutez les directives d’utilisation suivantes au début du fichier.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modifiez la classe `RDTExplorerWindow` de sorte que, en plus de la dérivation de la classe <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, elle implémente l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implémentez l’interface. Placez le curseur sur le nom du IVsRunningDocTableEvents. Vous devriez voir une ampoule dans la marge de gauche. Cliquez sur la flèche vers le bas à droite de l’ampoule, puis sélectionnez **implémenter l’interface**.

5. Dans chaque méthode de l’interface, remplacez la ligne `throw new NotImplementedException();` par ce qui suit :

    ```csharp
    return VSConstants.S_OK;
    ```

6. Ajoutez un champ de cookie à la classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Cela contient le cookie retourné par la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>.

7. Remplacez la méthode Initialize () de RDTExplorerWindow pour vous inscrire aux événements RDT. Vous devez toujours accéder aux services dans la méthode Initialize () de ToolWindowPane, et non dans le constructeur.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> est appelé pour obtenir une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>. La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> connecte les événements RDT à un objet qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, dans ce cas, un objet RDTExplorer.

8. Mettez à jour la méthode Dispose () de RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> supprime la connexion entre `RDTExplorer` et la notification d’événement RDT.

9. Ajoutez la ligne suivante au corps du gestionnaire de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>, juste avant l’instruction `return`.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Ajoutez une ligne semblable au corps du gestionnaire de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> et à d’autres événements que vous souhaitez afficher dans la zone de liste.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.

12. Ouvrez **RDTExplorerWindow** (**affichage/autres fenêtres/RDTExplorerWindow**).

     La fenêtre **RDTExplorerWindow** s’ouvre avec une liste d’événements vide.

13. Ouvrez ou créez une solution.

     À mesure que `OnBeforeLastDocument` et `OnAfterFirstDocument` événements sont déclenchés, la notification de chaque événement s’affiche dans la liste des événements.
