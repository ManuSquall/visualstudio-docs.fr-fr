---
title: Extension de la barre d’état Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711538"
---
# <a name="extend-the-status-bar"></a>Étendre la barre d’état
Vous pouvez utiliser la barre d’état Visual Studio au bas de l’IDE pour afficher des informations.

 Lorsque vous étendez la barre d’état, vous pouvez afficher des informations et des interfaces utilisateur dans quatre régions : la région de rétroaction, la barre de progression, la région d’animation et la région des concepteurs. La région de rétroaction vous permet d’afficher du texte et de mettre en évidence le texte affiché. La barre de progression montre des progrès progressifs pour les opérations à court terme telles que l’enregistrement d’un fichier. La région d’animation affiche une animation en boucle continue pour les opérations de longue durée ou le fonctionnement d’une longueur indéterminée, comme la construction de plusieurs projets dans une solution. Et la région de concepteur montre le numéro de ligne et de colonne de l’emplacement de curseur.

 Vous pouvez obtenir la barre <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> d’état <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> en utilisant l’interface (à partir du service). En outre, tout objet situé sur un cadre de fenêtre peut <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> s’inscrire comme objet client barre d’état en implémentant l’interface. Chaque fois qu’une fenêtre est activée, Visual Studio `IVsStatusbarUser` interroge l’objet situé sur cette fenêtre pour l’interface. S’il est <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> trouvé, il appelle la méthode sur l’interface retournée et l’objet peut mettre à jour la barre d’état de l’intérieur de cette méthode. Les fenêtres de documents, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> par exemple, peuvent utiliser la méthode pour mettre à jour l’information dans la région des concepteurs lorsqu’elles deviennent actives.

 Les procédures suivantes supposent que vous comprenez comment créer un projet VSIX et ajouter une commande de menu personnalisé. Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modifier la barre d’état
 Cette procédure vous montre comment définir et obtenir du texte, afficher du texte statique et mettre en évidence le texte affiché dans la zone de rétroaction de la barre d’état.

### <a name="read-and-write-to-the-status-bar"></a>Lire et écrire à la barre d’état

1. Créez un projet VSIX nommé **TestStatusBarExtension** et ajoutez une commande de menu nommée **TestStatusBarCommand**.

2. Dans *TestStatusBarCommand.cs*, remplacer le code`MenuItemCallback`de méthode de gestionnaire de commande ( ) par les éléments suivants :

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

3. Compilez le code et commencez à débogage.

4. Ouvrez le menu **Tools** dans l’instance expérimentale de Visual Studio. Cliquez sur le bouton **Invoke TestStatusBarCommand.**

     Vous devriez voir que le texte dans la barre d’état maintenant lit **Nous venons d’écrire à la barre de statut.** et la boîte de message qui apparaît a le même texte.

### <a name="update-the-progress-bar"></a>Mettre à jour la barre de progression

1. Dans cette procédure, nous allons montrer comment initialiser et mettre à jour la barre de progression.

2. Ouvrez le *fichier TestStatusBarCommand.cs* et `MenuItemCallback` remplacez la méthode par le code suivant :

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

3. Compilez le code et commencez à débogage.

4. Ouvrez le menu **Tools** dans l’instance expérimentale de Visual Studio. Cliquez **sur Invoke TestStatusBarCommand** bouton.

     Vous devriez voir que le texte dans la barre d’état lit maintenant **Écrit à la barre de progression.** Vous devriez également voir la barre de progression être mise à jour chaque seconde pendant 20 secondes. Après cela, la barre de statut et la barre de progression sont effacées.

### <a name="display-an-animation"></a>Afficher une animation

1. La barre d’état affiche une animation en boucle qui indique soit une opération de longue durée (par exemple, la construction de plusieurs projets dans une solution). Si vous ne voyez pas cette animation, assurez-vous d’avoir les paramètres **corrects** > **d’options d’outils** :

     Rendez-vous à l’onglet **Tools** > **Options** > **General** et **décochez automatiquement l’expérience visuelle en fonction de la performance du client.** Ensuite, vérifiez la sous-option **Activez une expérience visuelle client riche**. Vous devriez maintenant être en mesure de voir l’animation lorsque vous construisez le projet dans votre instance expérimentale de Visual Studio.

     Dans cette procédure, nous affichons l’animation Visual Studio standard qui représente la construction d’un projet ou d’une solution.

2. Ouvrez le *fichier TestStatusBarCommand.cs* et `MenuItemCallback` remplacez la méthode par le code suivant :

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

3. Compilez le code et commencez à débogage.

4. Ouvrez le menu **Tools** dans l’instance expérimentale de Visual Studio et cliquez sur **Invoke TestStatusBarCommand**.

     Lorsque vous voyez la boîte de message, vous devriez également voir l’animation dans la barre de statut à l’extrême droite. Lorsque vous rejetez la boîte de message, l’animation disparaît.
