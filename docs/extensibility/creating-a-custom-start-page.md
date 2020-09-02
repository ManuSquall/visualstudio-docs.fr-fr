---
title: Création d’une page de démarrage personnalisée | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: ed35948158866b7d0bbb2e458c8f8bc2f7b3f844
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903673"
---
# <a name="creating-a-custom-start-page"></a>Création d’une page de démarrage personnalisée

Vous pouvez créer une page de démarrage personnalisée en suivant les étapes décrites dans ce document.

## <a name="create-a-blank-start-page"></a>Créer une page de démarrage vierge

Tout d’abord, créez une page de démarrage vierge en créant un fichier *. Xaml* qui a une structure de balises que Visual Studio doit reconnaître. Ajoutez ensuite le balisage et le code-behind pour produire l’apparence et les fonctionnalités souhaitées.

1. Créez un nouveau projet de type **application WPF** (**Visual C#**  >  **Windows Desktop**).

2. Ajoutez une référence à `Microsoft.VisualStudio.Shell.14.0`.

3. Ouvrez le fichier XAML dans l’éditeur XML et remplacez l’élément de niveau supérieur \<Window> par un \<UserControl> élément sans supprimer les déclarations d’espace de noms.

4. Supprimez la `x:Class` déclaration de l’élément de niveau supérieur. Cela rend le contenu XAML compatible avec la fenêtre Outil Visual Studio qui héberge la page de démarrage.

5. Ajoutez les déclarations d’espaces de noms suivantes à l’élément de niveau supérieur \<UserControl> .

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Ces espaces de noms vous permettent d’accéder aux commandes, aux contrôles et aux paramètres de l’interface utilisateur de Visual Studio. Pour plus d’informations, consultez [Ajouter des commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     L’exemple suivant montre le balisage dans le fichier *. Xaml* pour une page de démarrage vierge. Tout contenu personnalisé doit figurer dans l' <xref:System.Windows.Controls.Grid> élément interne.

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

6. Ajoutez des contrôles à l' \<UserControl> élément vide pour remplir votre page de démarrage personnalisée. Pour plus d’informations sur l’ajout de fonctionnalités spécifiques à Visual Studio, consultez [Ajouter des commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Test et application de la page de démarrage personnalisée

Ne définissez pas l’instance principale de Visual Studio pour exécuter la page de démarrage personnalisée avant de vérifier qu’elle ne bloque pas Visual Studio. Au lieu de cela, testez-le dans l’instance expérimentale.

### <a name="to-test-a-manually-created-custom-start-page"></a>Pour tester une page de démarrage personnalisée créée manuellement

1. Copiez votre fichier XAML, ainsi que tous les fichiers texte de prise en charge ou fichiers de balisage, dans le dossier *%UserProfile%\My Documents\Visual Studio 2015 \ StartPages \\ *

2. Si votre page de démarrage fait référence à des contrôles ou des types dans des assemblys qui ne sont pas installés par Visual Studio, copiez les assemblys, puis collez-les dans *{dossier d’installation de Visual \\ Studio} \Common7\IDE\PrivateAssemblies*.

3. À une invite de commandes Visual Studio, tapez **devenv/Rootsuffix exp** pour ouvrir une instance expérimentale de Visual Studio.

4. Dans l’instance expérimentale, accédez à la **Tools**  >  page de démarrage de l’environnement**options**  >  **Environment**  >  **Startup** des outils et sélectionnez votre fichier XAML dans la liste déroulante personnaliser la **page de démarrage** .

5. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.

     Votre page de démarrage personnalisée doit être affichée. Si vous souhaitez modifier des fichiers, vous devez fermer l’instance expérimentale, apporter les modifications, copier et coller les fichiers modifiés, puis rouvrir l’instance expérimentale pour voir les modifications.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Pour appliquer la page de démarrage personnalisée dans l’instance principale de Visual Studio

- Une fois que vous avez testé votre page de démarrage et que vous l’avez trouvée comme stable, utilisez l’option **personnaliser la page de démarrage** dans la boîte de dialogue **options** pour la sélectionner comme page de démarrage dans l’instance principale de Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : ajouter du code XAML personnalisé à la page de démarrage](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Ajouter un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)
- [Ajouter des commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Procédure pas à pas : enregistrer les paramètres utilisateur sur une page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Déployer des pages de démarrage personnalisées](../extensibility/deploying-custom-start-pages.md)
