---
title: Création d’un contrôle de boîte à outils WPF (fr) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739568"
---
# <a name="create-a-wpf-toolbox-control"></a>Créez un contrôle de boîte à outils WPF

Le modèle de contrôle de boîte à outils WPF (Windows Presentation Framework) vous permet de créer des contrôles WPF qui sont automatiquement ajoutés à la boîte à **outils** lorsque l’extension est installée. Ce pas-fort montre comment utiliser le modèle pour créer un contrôle **Toolbox** que vous pouvez distribuer à d’autres utilisateurs.

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Créer le contrôle de la boîte à outils

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Créez une extension avec un contrôle WPF Toolbox

1. Créer un projet `MyToolboxControl`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Lorsque le projet s’ouvre, ajoutez un `MyToolboxControl`modèle d’élément de contrôle **WPF Toolbox** nommé . Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le dialogue **Add New Item,** rendez-vous sur Visual C **'Extensibility** **Visual C#** > et sélectionnez **WPF Toolbox Control**. Dans le champ **nom** au bas de la fenêtre, changer le nom du fichier de commande pour *MyToolboxControl.cs*.

    La solution contient maintenant un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> contrôle utilisateur, un qui ajoute le contrôle à la boîte à **outils**, et une entrée **Microsoft.VisualStudio.ToolboxControl** Asset dans le manifeste VSIX pour le déploiement.

#### <a name="to-create-the-control-ui"></a>Pour créer l’interface utilisateur de contrôle

1. Ouvrez *MyToolboxControl.xaml* dans le designer.

    Le concepteur affiche un contrôle <xref:System.Windows.Controls.Grid> contenant un contrôle <xref:System.Windows.Controls.Button>.

2. Disposer la disposition de la grille. Lorsque vous <xref:System.Windows.Controls.Grid> sélectionnez le contrôle, les barres de commande bleues apparaissent sur les bords supérieurs et gauches de la grille. Vous pouvez ajouter des lignes et des colonnes à la grille en cliquant sur les barres.

3. Ajouter les commandes pour enfants à la grille. Vous pouvez positionner un contrôle de l’enfant en le faisant glisser `Grid.Row` `Grid.Column` de la boîte à **outils** à une section de la grille, ou en définissant son et ses attributs dans le XAML. L’exemple suivant ajoute deux étiquettes sur la première rangée de la grille et un bouton sur la deuxième rangée.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Renommer le contrôle

 Par défaut, votre contrôle apparaîtra dans la **boîte à outils** comme **MyToolboxControl** dans un groupe nommé **MyToolboxControl.MyToolboxControl**. Vous pouvez modifier ces noms dans le *fichier MyToolboxControl.xaml.cs.*

1. Ouvrez *MyToolboxControl.xaml.cs* dans la vue de code.

2. Trouvez `MyToolboxControl` la classe et renommez-la à TestControl. (La façon la plus rapide de le faire est de renommer la classe, puis de sélectionner **Rename** à partir du menu contexte et de compléter les étapes. (Pour plus d’informations sur la commande **Rename,** voir [Rename refactoring (C)](../ide/reference/rename.md).)

3. Aller à `ProvideToolboxControl` l’attribut et changer la valeur du premier paramètre à **Test**. C’est le nom du groupe qui contiendra le contrôle dans la **boîte à outils**.

    Le code qui en résulte devrait ressembler à ceci :

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Construire, tester et déployer

 Lorsque vous débaillez le projet, vous devez trouver le contrôle installé dans la boîte à **outils** de l’instance expérimentale de Visual Studio.

### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle

1. Reconstruire le projet et commencer à débogage.

2. Dans la nouvelle instance de Visual Studio, créez un projet d’application WPF. Assurez-vous que le concepteur XAML est ouvert.

3. Recherchez votre contrôle dans la **boîte à outils** et faites-la glisser vers l’aire de conception.

4. Commencez à débogage de l’application WPF.

5. Vérifiez que votre contrôle apparaît.

### <a name="to-deploy-the-control"></a>Pour déployer le contenu

1. Après avoir construit le projet testé, vous pouvez trouver le fichier *.vsix* dans le\* dossier de déboiffage du projet.

2. Vous pouvez l’installer sur un ordinateur local en cliquant deux fois sur le fichier *.vsix* et en suivant la procédure d’installation. Pour désinstaller le contrôle, allez à **Tools** > **Extensions et Mises à jour** et rechercher l’extension de contrôle, puis cliquez sur **Uninstall**.

3. Téléchargez le fichier *.vsix* sur un réseau ou sur un site Web.

    Si vous téléchargez le fichier sur le site Web [Visual Studio Marketplace,](https://marketplace.visualstudio.com/) d’autres utilisateurs peuvent utiliser **Tools** > **Extensions and Updates** in Visual Studio pour trouver le contrôle en ligne et l’installer.
