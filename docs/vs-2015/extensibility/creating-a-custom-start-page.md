---
title: Création d’une page de démarrage personnalisée | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acb7922658a5dd7db0839051a42a119733c8b1d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184205"
---
# <a name="creating-a-custom-start-page"></a>Création d’une page de démarrage personnalisée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous ne pouvez pas créer une page de démarrage personnalisée à l’aide du modèle de projet page de démarrage, comme décrit dans [pages de démarrage](../misc/creating-your-own-start-page.md), vous pouvez en créer une manuellement en suivant les étapes décrites dans ce document.  
  
## <a name="creating-a-blank-start-page"></a>Création d’une page de démarrage vierge  
 Tout d’abord, créez une page de démarrage vierge en créant un fichier. XAML qui a une structure de balises que Visual Studio doit reconnaître. Ajoutez ensuite le balisage et le code-behind pour produire l’apparence et les fonctionnalités souhaitées.  
  
#### <a name="to-create-a-blank-start-page"></a>Pour créer une page de démarrage vierge  
  
1. Créez un nouveau projet de type **application WPF** (**Visual C#/Bureau Windows**).  
  
2. Ajoutez une référence à `Microsoft.VisualStudio.Shell.14.0`.  
  
3. Ouvrez le fichier XAML dans l’éditeur XML et remplacez l’élément de niveau supérieur \<Window> par un \<UserControl> élément sans supprimer les déclarations d’espace de noms.  
  
4. Supprimez la `x:Class` déclaration de l’élément de niveau supérieur. Cela rend le contenu XAML compatible avec la fenêtre Outil Visual Studio qui héberge la page de démarrage.  
  
5. Ajoutez les déclarations d’espaces de noms suivantes à l’élément de niveau supérieur \<UserControl> .  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Ces espaces de noms vous permettent d’accéder aux commandes, aux contrôles et aux paramètres de l’interface utilisateur de Visual Studio. Pour plus d’informations, consultez [Ajout de commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     L’exemple suivant montre le balisage dans le fichier. XAML pour une page de démarrage vierge. Tout contenu personnalisé doit figurer dans l' <xref:System.Windows.Controls.Grid> élément interne.  
  
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
  
6. Ajoutez des contrôles à l' \<UserControl> élément vide pour remplir votre page de démarrage personnalisée. Pour plus d’informations sur l’ajout de fonctionnalités spécifiques à Visual Studio, consultez [Ajout de commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Test et application de la page de démarrage personnalisée  
 Ne définissez pas l’instance principale de Visual Studio pour exécuter la page de démarrage personnalisée avant de vérifier qu’elle ne bloque pas Visual Studio. Au lieu de cela, testez-le dans l’instance expérimentale.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Pour tester une page de démarrage personnalisée créée manuellement  
  
1. Copiez votre fichier XAML, ainsi que tous les fichiers texte de prise en charge ou fichiers de balisage, dans le dossier **%UserProfile%\My Documents\Visual Studio 2015 \ StartPages \\ **  
  
2. Si votre page de démarrage fait référence à des contrôles ou des types dans des assemblys qui ne sont pas installés par Visual Studio, copiez les assemblys, puis collez-les dans le _dossier d’installation de Visual Studio_** \\ \Common7\IDE\PrivateAssemblies**.  
  
3. À une invite de commandes Visual Studio, tapez **devenv/Rootsuffix exp** pour ouvrir une instance expérimentale de Visual Studio.  
  
4. Dans l’instance expérimentale, accédez à la page **Outils/Options/environnement/démarrage** , puis sélectionnez votre fichier XAML dans la liste déroulante **personnaliser la page de démarrage** .  
  
5. Dans le menu **Affichage** , cliquez sur **Page de démarrage**.  
  
     Votre page de démarrage personnalisée doit être affichée. Si vous souhaitez modifier des fichiers, vous devez fermer l’instance expérimentale, apporter les modifications, copier et coller les fichiers modifiés, puis rouvrir l’instance expérimentale pour voir les modifications.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Pour appliquer la page de démarrage personnalisée dans l’instance principale de Visual Studio  
  
- Une fois que vous avez testé votre page de démarrage et que vous l’avez trouvée comme stable, utilisez l’option **personnaliser la page de démarrage** dans la boîte de dialogue **options** pour la sélectionner comme page de démarrage dans l’instance principale de Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : ajout de code XAML personnalisé à la page de démarrage](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Ajout d’un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)   
 [Ajout de commandes Visual Studio à une page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Procédure pas à pas : enregistrement des paramètres utilisateur sur une page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Déploiement de pages de démarrage personnalisées](../extensibility/deploying-custom-start-pages.md)
