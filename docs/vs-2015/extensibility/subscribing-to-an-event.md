---
title: Abonnement à un événement | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 77f277a63d08752ddbcb7e25bae4aa82867d280e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496001"
---
# <a name="subscribing-to-an-event"></a>Abonnement à un événement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [abonnement à un événement](https://docs.microsoft.com/visualstudio/extensibility/subscribing-to-an-event).  
  
Cette procédure pas à pas explique comment créer une fenêtre outil qui répond aux événements dans une table de documents en cours d’exécution (RDT). Une fenêtre outil héberge un contrôle utilisateur qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode connecte à l’interface pour les événements.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Abonnement aux événements RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Pour créer une extension avec une fenêtre outil  
  
1.  Créez un projet nommé **RDTExplorer** en utilisant le modèle VSIX et ajouter un modèle d’élément de fenêtre outil personnalisé nommé **RDTExplorerWindow**.  
  
     Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Pour vous abonner aux événements RDT  
  
1.  Ouvrez le fichier RDTExplorerWindowControl.xaml et supprimez le bouton nommé `button1`. Ajouter un <xref:System.Windows.Forms.ListBox> contrôler et acceptez le nom par défaut. L’élément Grid doit ressembler à ceci :  
  
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
  
3.  Modifier le `RDTExplorerWindow` , classe qui, en plus de la dérivation à partir de la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> (classe), il implémente le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interface.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    -   Implémentez l’interface. Placez le curseur sur le nom de IVsRunningDocTableEvents. Vous devez voir une ampoule dans la marge de gauche. Cliquez sur la flèche à droite de l’ampoule, puis sélectionnez **implémenter l’interface**.  
  
5.  Dans chaque méthode dans l’interface, remplacez la ligne `throw new NotImplementedException();` avec ce :  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6.  Ajoutez un champ de cookie à la classe RDTExplorerWindow.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Cela maintient le cookie qui est retourné par la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> (méthode).  
  
7.  Substituez la méthode de Initialize() de la RDTExplorerWindow pour enregistrer les événements RDT. Vous devez toujours obtenir les services dans la méthode Initialize() du ToolWindowPane, pas dans le constructeur.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     Le <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> service est appelé pour obtenir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interface. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> méthode connecte des événements RDT à un objet qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, dans ce cas, un objet RDTExplorer.  
  
8.  Mettre à jour de la méthode de Dispose() du RDTExplorerWindow.  
  
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
  
     Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> méthode supprime la connexion entre `RDTExplorer` et notification d’événement RDT.  
  
9. Ajoutez la ligne suivante au corps de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> gestionnaire, juste avant la `return` instruction.  
  
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
  
12. Ouvrez le **RDTExplorerWindow** (**vue / autres Windows / RDTExplorerWindow**).  
  
     Le **RDTExplorerWindow** fenêtre s’ouvre avec une liste d’événements vide.  
  
13. Ouvrez ou créez une solution.  
  
     En tant que `OnBeforeLastDocument` et `OnAfterFirstDocument` les événements sont déclenchés, la notification de chaque événement apparaît dans cette liste.

