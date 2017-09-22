---
title: "S’abonner à un événement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 35
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 623f9f765c4abd6d22f1db386f7c3e0e57580f95
ms.contentlocale: fr-fr
ms.lasthandoff: 09/19/2017

---
# <a name="subscribing-to-an-event"></a>S’abonner à un événement
Cette procédure pas à pas explique comment créer une fenêtre outil qui répond aux événements dans une table de documents en cours d’exécution (r & DT). Une fenêtre outil héberge un contrôle utilisateur qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode connecte à l’interface pour les événements.  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>S’abonner aux événements de r & DT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Pour créer une extension avec une fenêtre outil  
  
1.  Créez un projet nommé **RDTExplorer** à l’aide du modèle VSIX et ajouter un modèle d’élément de fenêtre outil personnalisé nommé **RDTExplorerWindow**.  
  
     Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>S’abonner aux événements de r & DT  
  
1.  Ouvrez le fichier RDTExplorerWindowControl.xaml et supprimez le bouton nommé `button1`. Ajouter un <xref:System.Windows.Forms.ListBox> contrôler et acceptez le nom par défaut. L’élément de grille doit ressembler à ceci :  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2.  Ouvrez le fichier RDTExplorerWindow.cs en mode code. Ajoutez le code suivant à l’aide d’instructions au début du fichier.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Modifier la `RDTExplorerWindow` classe ainsi que, en plus de la dérivation à partir de la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> (classe), il implémente la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interface.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Implémentez l’interface. Placez le curseur sur le nom de IVsRunningDocTableEvents. Vous devez voir une ampoule dans la marge de gauche. Cliquez sur la flèche située à droite de l’ampoule et sélectionnez **implémenter l’interface**.  
  
5.  Chaque méthode dans l’interface, remplacez la ligne `throw new NotImplementedException();` avec ce :  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Ajoutez un champ de cookie à la classe RDTExplorerWindow.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Cela maintient le cookie qui est retourné par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> (méthode).  
  
7.  Substituez la méthode Initialize() du RDTExplorerWindow inscrire les événements de r & DT. Vous devez toujours obtenir les services dans la méthode Initialize() de la ToolWindowPane, pas dans le constructeur.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> service est appelé pour obtenir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interface. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode connecte les événements de r & DT à un objet qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, dans ce cas, un objet RDTExplorer.  
  
8.  Mettre à jour de la méthode Dispose() de la RDTExplorerWindow.  
  
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
  
     Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> méthode supprime la connexion entre `RDTExplorer` et la notification d’événement de r & DT.  
  
9. Ajoutez la ligne suivante dans le corps de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> gestionnaire, juste avant la `return` instruction.  
  
    ```csharp  
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
10. Ajouter une ligne semblable au corps de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> gestionnaire et à d’autres événements que vous souhaitez voir dans la zone de liste.  
  
    ```csharp  
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)  
    {  
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");  
        return VSConstants.S_OK;  
    }  
    ```  
  
11. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.  
  
12. Ouvrez le **RDTExplorerWindow** (**affichage / autres fenêtres / RDTExplorerWindow**).  
  
     Le **RDTExplorerWindow** fenêtre s’ouvre avec une liste d’événements vide.  
  
13. Ouvrez ou créez une solution.  
  
     En tant que `OnBeforeLastDocument` et `OnAfterFirstDocument` les événements sont déclenchés, la notification de chaque événement apparaît dans l’événement de liste.
