---
title: Abonnement à un événement (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699687"
---
# <a name="subscribing-to-an-event"></a>Abonnement à un événement
Cette procédure pas à pas explique comment créer une fenêtre d’outils qui répond aux événements dans une table de documents en cours d’exécution (RDT). Une fenêtre d’outil héberge <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>un contrôle utilisateur qui implémente . La <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode relie l’interface aux événements.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Abonnement aux événements RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Créer une extension avec une fenêtre d’outils

1. Créez un projet nommé **RDTExplorer** à l’aide du modèle VSIX et ajoutez un modèle d’élément de fenêtre d’outil personnalisé nommé **RDTExplorerWindow**.

     Pour plus d’informations sur la création d’une extension avec une fenêtre d’outil, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Pour vous abonner aux événements RDT

1. Ouvrez le fichier RDTExplorerWindowControl.xaml `button1`et supprimez le bouton nommé . Ajoutez <xref:System.Windows.Forms.ListBox> un contrôle et acceptez le nom par défaut. L’élément Grille devrait ressembler à ceci :

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Ouvrez le fichier RDTExplorerWindow.cs en vue de code. Ajoutez ce qui suit à l’aide de directives au début du fichier.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modifier `RDTExplorerWindow` la classe de sorte que, en <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> plus de dérivé <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> de la classe, il implémente l’interface.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implémenter l’interface. Placez le curseur sur le nom IVsRunningDocTableEvents. Vous devriez voir une ampoule dans la marge gauche. Cliquez sur la flèche Down vers la droite de l’ampoule et **sélectionnez l’interface Implement**.

5. Dans chaque méthode de l’interface, remplacez la ligne `throw new NotImplementedException();` par ceci :

    ```csharp
    return VSConstants.S_OK;
    ```

6. Ajoutez un champ de biscuits à la classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Cela contient le cookie qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> est retourné par la méthode.

7. Remplacer la méthode Initialize() de RDTExplorerWindow pour s’inscrire aux événements RDT. Vous devriez toujours obtenir des services dans la méthode Initialize() de l’ToolWindowPane, et non dans le constructeur.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> service est appelé <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> pour obtenir une interface. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode relie les événements RDT <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>à un objet qui implémente, dans ce cas, un objet RDTExplorer.

8. Mettre à jour la méthode RDTExplorerWindow’s Dispose().

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

     La <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> méthode supprime la `RDTExplorer` connexion entre la notification de l’événement RDT et la notification d’événements RDT.

9. Ajouter la ligne suivante au <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> corps du `return` gestionnaire, juste avant la déclaration.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Ajoutez une ligne similaire au <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> corps du gestionnaire et à d’autres événements que vous voulez voir dans la boîte de liste.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Générez le projet et commencez le débogage. L’instance expérimentale Visual Studio apparaît.

12. Ouvrez le **RDTExplorerWindow** (**Voir / Autres Fenêtres / RDTExplorerWindow**).

     La fenêtre **RDTExplorerWindow** s’ouvre sur une liste d’événements vide.

13. Ouvrez ou créez une solution.

     Au `OnBeforeLastDocument` `OnAfterFirstDocument` fur et à mesure que les événements sont déclenchés, la notification de chaque événement apparaît dans la liste des événements.
