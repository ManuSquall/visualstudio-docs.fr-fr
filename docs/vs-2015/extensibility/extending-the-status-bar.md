---
title: Extension de la barre d’État | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28fc1155279ec624cea576b5a70a25800d4ff837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204413"
---
# <a name="extending-the-status-bar"></a>Extension de la barre d’état
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser la barre d’état de Visual Studio au bas de l’IDE pour afficher des informations.  
  
 Lorsque vous étendez la barre d’État, vous pouvez afficher les informations et l’interface utilisateur dans quatre régions : la région de commentaires, la barre de progression, la zone d’animation et la zone du concepteur. La région de commentaires vous permet d’afficher du texte et de mettre en surbrillance le texte affiché. La barre de progression indique la progression incrémentielle pour les opérations de longue durée, telles que l’enregistrement d’un fichier. La zone d’animation affiche une animation en boucle continue pour les opérations de longue durée ou l’opération de longueur indéterminée, telle que la génération de plusieurs projets dans une solution. Et la zone du concepteur affiche le numéro de ligne et de colonne de l’emplacement du curseur.  
  
 Vous pouvez accéder à la barre d’État à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface (à partir du <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service). En outre, tout objet présent sur un frame de fenêtre peut s’inscrire en tant qu’objet client de barre d’État en implémentant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interface. Chaque fois qu’une fenêtre est activée, Visual Studio interroge l’objet sur cette fenêtre pour l' `IVsStatusbarUser` interface. S’il est trouvé, il appelle la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> méthode sur l’interface retournée et l’objet peut mettre à jour la barre d’État à partir de cette méthode. Par exemple, les fenêtres de document peuvent utiliser la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> méthode pour mettre à jour les informations dans la zone du concepteur lorsqu’elles deviennent actives.  
  
 Les procédures suivantes supposent que vous comprenez comment créer un projet VSIX et ajouter une commande de menu personnalisée. Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Modification de la barre d’État  
 Cette procédure vous montre comment définir et obtenir du texte, afficher du texte statique et mettre en surbrillance le texte affiché dans la zone de commentaires de la barre d’État.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Lecture et écriture dans la barre d’État  
  
1. Créez un projet VSIX nommé **TestStatusBarExtension** et ajoutez une commande de menu nommée **TestStatusBarCommand**.  
  
2. Dans TestStatusBarCommand.cs, remplacez le code de la méthode du gestionnaire de commandes (MenuItemCallback) par ce qui suit :  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3. Compilez le code et démarrez le débogage.  
  
4. Ouvrez le menu **Outils** dans l’instance expérimentale de Visual Studio. Cliquez sur le bouton **Invoke TestStatusBarCommand** .  
  
     Vous devez voir que le texte dans la barre d’État lit maintenant **« nous venons d’écrire dans la barre d’État ».** et la boîte de message qui s’affiche contient le même texte.  
  
#### <a name="updating-the-progress-bar"></a>Mise à jour de la barre de progression  
  
1. Dans cette procédure, nous allons montrer comment initialiser et mettre à jour la barre de progression.  
  
2. Ouvrez le fichier TestStatusBarCommand.cs et remplacez la méthode MenuItemCallback par le code suivant :  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3. Compilez le code et démarrez le débogage.  
  
4. Ouvrez le menu **Outils** dans l’instance expérimentale de Visual Studio. Cliquez sur le bouton **appeler TestStatusBarCommand** .  
  
     Vous devez voir que le texte dans la barre d’État lit maintenant **« écriture dans la barre de progression ».** Vous devez également voir la barre de progression être mise à jour toutes les secondes pendant 20 secondes. Après cela, la barre d’État et la barre de progression sont effacées.  
  
#### <a name="displaying-an-animation"></a>Affichage d’une animation  
  
1. La barre d’état affiche une animation en boucle qui indique une opération de longue durée (par exemple, la génération de plusieurs projets dans une solution). Si vous ne voyez pas cette animation, vérifiez que vous avez les paramètres **Outils/Options** appropriés :  
  
     Accédez à l’onglet **Outils/Options/général** et décochez l’option **Ajuster automatiquement l’expérience visuelle en fonction des performances du client**. Cochez ensuite la sous-option **activer l’expérience visuelle des clients enrichis**. Vous devez maintenant être en mesure de voir l’animation lorsque vous générez le projet dans votre instance expérimentale de Visual Studio.  
  
     Dans cette procédure, nous affichons l’animation Visual Studio standard qui représente la génération d’un projet ou d’une solution.  
  
2. Ouvrez le fichier TestStatusBarCommand.cs et remplacez la méthode MenuItemCallback par le code suivant :  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3. Compilez le code et démarrez le débogage.  
  
4. Ouvrez le menu **Outils** de l’instance expérimentale de Visual Studio et cliquez sur **appeler TestStatusBarCommand**.  
  
     Quand vous voyez la boîte de message, vous devez également voir l’animation dans la barre d’état située à l’extrême droite. Lorsque vous fermez la boîte de message, l’animation disparaît.
