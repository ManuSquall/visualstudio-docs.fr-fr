---
title: Extension de la barre d’état | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 499e6c2b34fcc5261ab8fb3a87a24e2cc0959d8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113740"
---
# <a name="extend-the-status-bar"></a>Étendre la barre d’état
Vous pouvez utiliser la barre d’état Visual Studio en bas de l’IDE pour afficher des informations.

 Lorsque vous étendez la barre d’état, vous pouvez afficher des informations et l’interface utilisateur dans quatre régions : la zone de commentaires, de la barre de progression, de la région d’animation et de la zone du concepteur. La zone de commentaires permet d’afficher du texte et mettre en surbrillance le texte affiché. La barre de progression indique la progression incrémentielle pour les opérations d’exécution courte telles que l’enregistrement d’un fichier. La région d’animation affiche une animation en boucle en continu pour les opérations longues ou l’opération de durée indéterminée, tels que la création de plusieurs projets dans une solution. Et la zone du concepteur affiche le numéro de ligne et colonne de l’emplacement du curseur.

 Vous pouvez obtenir la barre d’état à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface (à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service). En outre, n’importe quel objet doit se trouver sur un frame de fenêtre peut enregistrer en tant qu’un état de la barre objet client en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> interface. Chaque fois qu’une fenêtre est activée, Visual Studio interroge l’objet doit se trouver dans cette fenêtre pour le `IVsStatusbarUser` interface. Si trouvée, elle appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> méthode sur l’interface retournée et l’objet peut mettre à jour la barre d’état à partir de cette méthode. Document de windows, par exemple, peut utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> méthode pour mettre à jour les informations contenues dans la zone du concepteur quand ils sont activés.

 Les procédures suivantes supposent que vous comprenez comment créer un projet VSIX et ajouter une commande de menu personnalisé. Pour plus d’informations, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Modifier la barre d’état
 Cette procédure vous montre comment définir et obtenir le texte, afficher du texte statique et mettez en surbrillance le texte affiché dans la zone de commentaires de la barre d’état.

### <a name="read-and-write-to-the-status-bar"></a>Lire et écrire dans la barre d’état

1. Créez un projet VSIX nommé **TestStatusBarExtension** et ajoutez une commande de menu nommée **TestStatusBarCommand**.

2. Dans *TestStatusBarCommand.cs*, remplacez le code de méthode de gestionnaire de commande (`MenuItemCallback`) par le code suivant :

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

3. Compilez le code et démarrer le débogage.

4. Ouvrez le **outils** menu dans l’instance expérimentale de Visual Studio. Cliquez sur le **TestStatusBarCommand appeler** bouton.

     Vous devez voir que le texte dans la barre maintenant lectures **nous venons de la barre d’état.** et la boîte de message qui s’affiche comporte le même texte.

### <a name="update-the-progress-bar"></a>Mettre à jour de la barre de progression

1. Dans cette procédure, nous allons montrer comment initialiser et mettre à jour de la barre de progression.

2. Ouvrez le *TestStatusBarCommand.cs* fichier et remplacez le `MenuItemCallback` méthode avec le code suivant :

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

3. Compilez le code et démarrer le débogage.

4. Ouvrez le **outils** menu dans l’instance expérimentale de Visual Studio. Cliquez sur **TestStatusBarCommand appeler** bouton.

     Vous devez voir que le texte dans la barre maintenant lectures **écriture dans la barre de progression.** Vous devez également voir la barre de progression est mise à jour par seconde pendant 20 secondes. Après cela, la barre d’état et la barre de progression sont effacées.

### <a name="display-an-animation"></a>Afficher une animation

1. La barre d’état affiche une animation de boucle qui indique soit une opération longue (par exemple, la génération de plusieurs projets dans une solution). Si vous ne voyez pas cette animation, assurez-vous que vous avez la bonne **outils** > **Options** paramètres :

     Accédez à la **outils** > **Options** > **général** onglet et décochez la case **ajuster automatiquement l’expérience visuelle selon le client performances**. Puis activez sous-l’option de **activer l’expérience visuelle améliorée**. Vous devez maintenant être en mesure de voir l’animation lorsque vous générez le projet dans votre instance expérimentale de Visual Studio.

     Dans cette procédure, nous affichons l’animation de Visual Studio standard, qui représente la création d’un projet ou une solution.

2. Ouvrez le *TestStatusBarCommand.cs* fichier et remplacez le `MenuItemCallback` méthode avec le code suivant :

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

3. Compilez le code et démarrer le débogage.

4. Ouvrez le **outils** menu dans l’instance expérimentale de Visual Studio et cliquez sur **TestStatusBarCommand appeler**.

     Lorsque vous voyez la boîte de message, vous devez également voir l’animation dans la barre d’état à l’extrême droite. Lorsque vous fermez la boîte de message, l’animation disparaît.