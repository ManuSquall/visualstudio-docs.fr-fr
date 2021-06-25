---
title: Abonnement à un événement | Microsoft Docs
description: Découvrez comment créer une fenêtre outil qui répond aux événements dans une table de document en cours d’exécution dans le kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 01271016eed9a4a157b333a2f0435589b0a028d5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899389"
---
# <a name="subscribing-to-an-event"></a>Abonnement à un événement
Cette procédure pas à pas explique comment créer une fenêtre outil qui répond aux événements dans une table de document en cours d’exécution (RDT). Une fenêtre outil héberge un contrôle utilisateur qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . La <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode connecte l’interface aux événements.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Abonnement à des événements RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Pour créer une extension avec une fenêtre outil

1. Créez un projet nommé **RDTExplorer** à l’aide du modèle VSIX, puis ajoutez un modèle d’élément de fenêtre outil personnalisé nommé **RDTExplorerWindow**.

     Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Pour s’abonner à des événements RDT

1. Ouvrez le fichier RDTExplorerWindowControl. xaml et supprimez le bouton nommé `button1` . Ajoutez un <xref:System.Windows.Forms.ListBox> contrôle et acceptez le nom par défaut. L’élément Grid doit se présenter comme suit :

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Ouvrez le fichier RDTExplorerWindow. cs en mode Code. Ajoutez les directives d’utilisation suivantes au début du fichier.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modifiez la `RDTExplorerWindow` classe de sorte que, en plus de la dérivation à partir de la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe, elle implémente l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interface.

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

     Cela contient le cookie retourné par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode.

7. Remplacez la méthode Initialize () de RDTExplorerWindow pour vous inscrire aux événements RDT. Vous devez toujours accéder aux services dans la méthode Initialize () de ToolWindowPane, et non dans le constructeur.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> service est appelé pour obtenir une <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interface. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode connecte les événements RDT à un objet qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> , dans ce cas, un objet RDTExplorer.

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

     La <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> méthode supprime la connexion entre `RDTExplorer` et la notification d’événement RDT.

9. Ajoutez la ligne suivante au corps du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> Gestionnaire, juste avant l' `return` instruction.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Ajoutez une ligne semblable au corps du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> Gestionnaire et à d’autres événements que vous souhaitez afficher dans la zone de liste.

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

     Lorsque `OnBeforeLastDocument` les `OnAfterFirstDocument` événements et sont déclenchés, la notification de chaque événement s’affiche dans la liste des événements.
