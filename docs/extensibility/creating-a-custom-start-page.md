---
title: Création d’une page de démarrage personnalisée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739629"
---
# <a name="creating-a-custom-start-page"></a>Création d’une page de démarrage personnalisée

Vous pouvez créer une page de démarrage personnalisée en suivant les étapes de ce document.

## <a name="create-a-blank-start-page"></a>Créer une page de démarrage vierge

Tout d’abord, faire une page de démarrage vierge en créant un fichier *.xaml* qui a une structure de tag que Visual Studio reconnaîtra. Ensuite, ajoutez la balisage et le code-derrière pour produire l’apparence et la fonctionnalité que vous voulez.

1. Créez un nouveau projet du type **d’application WPF** **(Visual C'** > **Windows Desktop**).

2. Ajoutez une référence à `Microsoft.VisualStudio.Shell.14.0`.

3. Ouvrez le fichier XAML dans l’éditeur \<XML et modifiez \<l’élément de> fenêtre de haut niveau en un élément de> d’utilisateurcontrol sans supprimer aucune des déclarations d’espace nom.

4. Supprimer `x:Class` la déclaration de l’élément de haut niveau. Cela rend le contenu XAML compatible avec la fenêtre d’outils Visual Studio qui héberge la page De démarrage.

5. Ajoutez les déclarations d’espace nom \<suivant à l’élément de> utilisateur de haut niveau.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Ces espaces nominaux vous permettent d’accéder aux commandes, aux contrôles et aux paramètres de l’interface utilisateur visual studio. Pour plus d’informations, voir [add Visual Studio commandes à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     L’exemple suivant montre la majoration dans le fichier *.xaml* pour une page de démarrage vierge. Tout contenu personnalisé doit <xref:System.Windows.Controls.Grid> aller dans l’élément intérieur.

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. Ajoutez des commandes \<à l’élément vide UserControl> pour remplir votre page de démarrage personnalisée. Pour plus d’informations sur la façon d’ajouter des [fonctionnalités](../extensibility/adding-visual-studio-commands-to-a-start-page.md)spécifiques à Visual Studio, voir ajouter des commandes De studio visuel à une page de démarrage .

## <a name="test-and-apply-the-custom-start-page"></a>Testez et appliquez la page de démarrage personnalisée

Ne définissez pas l’instance principale de Visual Studio pour exécuter la page de démarrage personnalisée jusqu’à ce que vous vérifiez qu’il ne s’écrase pas Visual Studio. Au lieu de cela, le tester dans l’instance expérimentale.

### <a name="to-test-a-manually-created-custom-start-page"></a>Pour tester une page de démarrage personnalisée créée manuellement

1. Copiez votre fichier XAML, et tous les fichiers texte à l’appui ou fichiers de *balisage, au\\ dossier %USERPROFILE%-My Documents-Visual Studio 2015-StartPages.*

2. Si votre page de démarrage fait référence à des contrôles ou des types dans des assemblages qui ne sont pas installés par Visual Studio, copiez les assemblages et collez-les dans le dossier d’installation visual studio ' *Common7'IDE’PrivateAssemblies\\*.

3. Lors d’une invite de commande Visual Studio, type **devenv/rootsuffix Exp** pour ouvrir une instance expérimentale de Visual Studio.

4. Dans le cas expérimental, rendez-vous sur la page **Tools** > **Options** > **Environment** > **Startup** et sélectionnez votre fichier XAML à partir de la page De démarrage **personnalisée.**

5. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.

     Votre page de démarrage personnalisée doit être affichée. Si vous souhaitez modifier des fichiers, vous devez fermer l’instance expérimentale, apporter les modifications, copier et coller les fichiers modifiés, puis rouvrir l’instance expérimentale pour afficher les modifications.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Appliquer la page de départ personnalisée dans l’instance principale de Visual Studio

- Après avoir testé votre page de démarrage et constaté qu’elle était stable, utilisez l’option **Customize Start Page** dans la boîte de dialogue **Options** pour la sélectionner comme page de départ dans l’instance principale de Visual Studio

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Ajoutez XAML personnalisé à la page de départ](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Ajouter le contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)
- [Ajoutez des commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Procédure pas à pas : enregistrez les paramètres de l’utilisateur sur une page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Déployer des pages de démarrage personnalisées](../extensibility/deploying-custom-start-pages.md)
