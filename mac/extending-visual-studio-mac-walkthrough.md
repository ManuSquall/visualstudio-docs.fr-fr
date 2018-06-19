---
title: 'Procédure pas à pas : Extension de Visual Studio pour Mac'
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: fdfbc5c10c3b49165960938f7f8832f61a37a805
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
ms.locfileid: "31625072"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Procédure pas à pas : Extension de Visual Studio pour Mac

Cette rubrique vous guide à travers la création d’[un package d’extension simple](https://github.com/mjh4/AddIns/tree/master/DateInserter). Le package d’extension crée une nouvelle commande pour le menu Edition de Visual Studio pour Mac, qui permet à l’utilisateur d’insérer la date et l’heure actuelles dans un document texte ouvert.

Cet exemple utilise Add-in Maker. Add-in Maker crée un modèle de projet et le remplit avec les fichiers nécessaires pour notre package d’extension personnalisé.

1.   Commencez par lancer Visual Studio pour Mac, s’il n’est pas déjà ouvert :

  ![Capture d’écran de Visual Studio pour Mac](media/extending-visual-studio-mac-addin3.png)

2.   Installez le _package d’extension Add-in Maker_ en utilisant le Gestionnaire d’extensions. Dans le menu Visual Studio, choisissez **Extensions...**  :

  ![Onglet Gestionnaire de compléments](media/extending-visual-studio-mac-addin4.png)

3.   Accédez à l’onglet Galerie et tapez `Addin Maker` dans la barre de recherche en haut à droite. Sélectionnez Addin Maker dans la catégorie Développement de compléments et cliquez sur <kbd>Installer</kbd>. Si rien ne s’affiche, cliquez sur Actualiser et relancez la recherche :

  ![Gestionnaire de compléments](media/extending-visual-studio-mac-addin5.png)

4.   Maintenant qu’Addin Maker est installé, vous pouvez démarrer la création d’un package d’extension. Commencez par créer une solution.

5.  Dans la boîte de dialogue **Nouvelle solution**, choisissez le modèle **Autre > Divers > Général > Xamarin Studio Addin > C#** et, sur l’écran suivant, nommez la nouvelle solution `DateInserter` :

  ![Création d’une solution](media/extending-visual-studio-mac-addin7New.png)

6.   Visual Studio pour Mac remplira une nouvelle solution :

  ![Solution remplie](media/extending-visual-studio-mac-addin8.png)

7.   Supprimez le code du modèle dans `Manifest.addin.xml` et remplacez-le par le code suivant :

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
        <ExtensionModel>
            <Extension path = "/MonoDevelop/Ide/Commands/Edit">
                <Command id = "DateInserter.DateInserterCommands.InsertDate"
                    _label = "Insert Date"
                    defaultHandler = "DateInserter.InsertDateHandler" />
            </Extension>

            <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
                <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
            </Extension>
        </ExtensionModel>
    ```

8.   Vous devez maintenant configurer les fichiers qui vont au final gérer l’insertion de la date et de l’heure dans l’éditeur de texte. Cliquez avec le bouton droit sur le nœud du projet et ajoutez un nouveau fichier. Sélectionnez **Général > Classe vide** et nommez le nouveau fichier *InsertDateHandler* :

  ![Gestionnaire d’insertion de date](media/extending-visual-studio-mac-addin9.png)

9.   Supprimons le code du modèle dans `InsertDateHandler.cs` et remplaçons-le par le code suivant :

    ```cs
    using MonoDevelop.Components.Commands;
    using MonoDevelop.Ide;
    using MonoDevelop.Ide.Gui;
    using System;

    namespace DateInserter
    {
        class InsertDateHandler : CommandHandler
        {
            protected override void Run()
            {

            }

            protected override void Update(CommandInfo info)
            {

            }
        }
    }
    ```

  Nous développerons ces deux méthodes d’espace réservé plus tard.

10.   Cliquez avec le bouton droit sur le projet **DateInserter** et sélectionnez **Ajouter > Nouveau fichier**. Sélectionnez **Général > Énumération vide**, puis nommez le nouveau fichier *DateInserterCommands* :

  ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11.   Ajoutez la commande `InsertDate` en tant que nouvelle énumération dans le fichier `DateInserterCommands.cs` :

    ``` cs
    using System;

    namespace DateInserter
    {
        public enum DateInserterCommands
        {
            InsertDate,
        }
    }
    ```

12.   À ce stade, vous devez avoir un package d’extension fonctionnel. Vous pouvez le tester en enregistrant votre travail et en exécutant l’application. L’IDE lancera une nouvelle instance de Visual Studio pour Mac avec le nouveau package d’extension installé. Si vous accédez au **menu Edition**, vous voyez que Visual Studio pour Mac a une nouvelle option appelée **Insert Date** (Insérer la date), comme illustré par la capture d’écran ci-dessous :

  ![Commande Insert date](media/extending-visual-studio-mac-addin11.png)

  Notez que la sélection d’Insert Date à partir du menu n’a aucun effet, car l’implémentation actuelle a seulement des méthodes d’espace réservé.

13.   Le framework est en place pour le package d’extension, et il est temps d’écrire le code qui permet l’insertion de la date. Vérifiez d’abord que la **commande Insert Date** est activée seulement quand l’utilisateur a un fichier texte ouvert en remplaçant la méthode `Update` dans `InsertDateHandler.cs` par le code suivant :

    ```cs
    protected override void Update(CommandInfo info)
    {
        info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14.   Mettez à jour la méthode `Run` de la commande pour qu’elle insère la date et l’heure avec le code suivant :

    ``` cs
    protected override void Run () {
        var editor = IdeApp.Workbench.ActiveDocument.Editor;
        var date = DateTime.Now.ToString ();
        editor.InsertAtCaret (date);

    }
    ```

15.   Enfin, exécutons notre package d’extension pour le tester. Dans la nouvelle instance de Visual Studio pour Mac, sélectionnez **Edition > Insert Date**. La date et l’heure actuelles sont insérées à notre point d’insertion, comme illustré par la capture d’écran ci-dessous :

  ![Capture d’écran - Insérer la date](media/extending-visual-studio-mac-addin12.png)
