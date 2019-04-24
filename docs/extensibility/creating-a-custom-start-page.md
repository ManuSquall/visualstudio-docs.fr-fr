---
title: Page de démarrage de création personnalisé | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4fc12744dbf979a338cbc551a715284dffdf7385
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090128"
---
# <a name="creating-a-custom-start-page"></a>Création d’une Page de démarrage personnalisée

Vous pouvez créer une Page de démarrage personnalisée en suivant les étapes décrites dans ce document.

## <a name="create-a-blank-start-page"></a>Créer une Page de démarrage vierge

Vérifiez tout d’abord, une Page de démarrage vierge en créant un *.xaml* fichier qui a une structure de balise que Visual Studio reconnaît. Ensuite, ajoutez le balisage et code-behind pour produire l’apparence et les fonctionnalités que vous souhaitez.

1. Créez un projet du type **Application WPF** (**Visual C#** > **Windows Desktop**).

2. Ajoutez une référence à `Microsoft.VisualStudio.Shell.14.0`.

3. Ouvrez le fichier XAML dans l’éditeur XML et modifiez le niveau supérieur \<fenêtre > élément à un \<UserControl > élément sans le supprimer d’une des déclarations d’espace de noms.

4. Supprimer le `x:Class` déclaration à partir de l’élément de niveau supérieur. Cela rend le contenu XAML compatible avec la fenêtre d’outil de Visual Studio qui héberge la Page de démarrage.

5. Ajoutez les déclarations d’espace de noms suivantes au niveau supérieur \<UserControl > élément.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Ces espaces de noms vous permettent d’accéder aux commandes de Visual Studio, les contrôles et les paramètres de l’interface utilisateur. Pour plus d’informations, consultez [commandes Ajouter Visual Studio à une Page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     L’exemple suivant montre le balisage dans le *.xaml* fichier pour une Page de démarrage vierge. N’importe quel contenu personnalisé doit être placé dans interne <xref:System.Windows.Controls.Grid> élément.

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

6. Ajouter des contrôles à la vider \<UserControl > élément pour remplir dans votre Page de démarrage personnalisée. Pour plus d’informations sur l’ajout de fonctionnalités spécifiques à Visual Studio, consultez [commandes Ajouter Visual Studio à une Page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Tester et appliquer la Page de démarrage personnalisée

Ne définissez pas l’instance principale de Visual Studio pour exécuter la Page de démarrage personnalisée avant de vérifier qu’il ne bloque pas Visual Studio. Au lieu de cela, le tester dans l’instance expérimentale.

### <a name="to-test-a-manually-created-custom-start-page"></a>Pour tester une Page de démarrage du personnalisés créés manuellement

1. Copie de votre fichier XAML et les fichiers texte ou balisage des fichiers, à la *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\*  dossier.

2. Si votre page de démarrage fait référence à des contrôles ou les types dans les assemblys qui ne sont pas installés par Visual Studio, copiez les assemblys et les coller ensuite dans *{dossier d’installation de Visual Studio} \Common7\IDE\PrivateAssemblies\\* .

3. À une invite de commandes Visual Studio, tapez **devenv /rootsuffix Exp** pour ouvrir une instance expérimentale de Visual Studio.

4. Dans l’instance expérimentale, accédez à la **outils** > **Options** > **environnement** > **dedémarrage** page et sélectionnez votre fichier XAML à partir de la **personnaliser la Page de démarrage** liste déroulante.

5. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.

     Votre page de démarrage personnalisée doit être affiché. Si vous souhaitez modifier tous les fichiers, fermez l’instance expérimentale, apportez les modifications, copiez et collez les fichiers modifiés et puis ouvrez à nouveau l’instance expérimentale pour afficher les modifications.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Pour appliquer personnalisé page de démarrage dans l’instance principale de Visual Studio

- Après avoir testé votre Page de démarrage et jugé stable, utilisez le **personnaliser la Page de démarrage** option dans le **Options** boîte de dialogue pour le sélectionner comme page de démarrage dans l’instance principale de Visual Studio

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Ajoutez le XAML personnalisé à la Page de démarrage](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Ajouter un contrôle utilisateur à la Page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)
- [Ajouter des commandes de Visual Studio à une Page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Procédure pas à pas : Enregistrer les paramètres utilisateur sur une Page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Déployer les Pages de démarrage personnalisées](../extensibility/deploying-custom-start-pages.md)