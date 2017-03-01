---
title: "Création d’un fichier de la Page Démarrer | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 2902ac3b5cd4fd038bdaf277a8390d5eb9e96b28
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-start-page"></a>Création d’une Page de démarrage personnalisée
Vous pouvez créer une Page de démarrage personnalisée en suivant les étapes décrites dans ce document.  
  
## <a name="creating-a-blank-start-page"></a>Création d’une page de démarrage vierge  
 Vérifiez tout d’abord, une Page de démarrage vierge en créant un fichier .xaml qui a une structure de balise que Visual Studio reconnaît. Ensuite, ajoutez le balisage et code-behind pour produire l’apparence et les fonctionnalités que vous souhaitez.  
  
#### <a name="to-create-a-blank-start-page"></a>Pour créer une Page de démarrage vierge  
  
1.  Créez un nouveau projet du type **Application WPF** (**Visual c# / bureau Windows**.  
  
2.  Ajoutez une référence à `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Ouvrez le fichier XAML dans l’éditeur XML et modifier le niveau supérieur \<fenêtre > élément à un \<UserControl > élément sans supprimer les déclarations d’espace de noms.  
  
4.  Supprimer le `x:Class` déclaration de l’élément de niveau supérieur. Cela rend le contenu XAML compatible avec la fenêtre d’outils de Visual Studio qui héberge la page de démarrage.  
  
5.  Ajoutez les déclarations d’espace de noms suivantes au niveau supérieur \<UserControl > élément.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Ces espaces de noms vous permettent d’accéder aux commandes de Visual Studio, les contrôles et les paramètres de l’interface utilisateur. Pour plus d’informations, consultez [ajoutant les commandes Visual Studio à une Page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     L’exemple suivant montre le balisage dans le fichier .xaml pour une Page de démarrage vierge. Tout contenu personnalisé doit être placé dans interne <xref:System.Windows.Controls.Grid>élément.</xref:System.Windows.Controls.Grid>  
  
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
  
6.  Ajouter des contrôles à vide \<UserControl > élément pour remplir votre Page de démarrage personnalisée. Pour plus d’informations sur l’ajout de fonctionnalités spécifiques à Visual Studio, consultez [ajoutant les commandes Visual Studio à une Page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Test et application de la page de démarrage personnalisée  
 Ne définissez pas l’instance principale de Visual Studio pour exécuter la Page de démarrage personnalisée jusqu'à ce que vous vérifiez qu’elle ne bloque pas Visual Studio. Au lieu de cela, le test dans l’instance expérimentale.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Pour tester une Page de démarrage personnalisée créée manuellement  
  
1.  Copiez votre fichier XAML et les fichiers texte ou balisage fichiers, à la **%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ ** dossier.  
  
2.  Si votre page de démarrage fait référence à des contrôles ou les types dans les assemblys qui ne sont pas installés par Visual Studio, copiez les assemblys et les coller ensuite dans *dossier d’installation de Visual Studio***\Common7\IDE\PrivateAssemblies\\**.  
  
3.  À l’invite de commandes de Visual Studio, tapez **devenv /rootsuffix Exp** pour ouvrir une instance expérimentale de Visual Studio.  
  
4.  Dans l’instance expérimentale, accédez à la **Outils / Options / environnement / démarrage** page et sélectionnez votre fichier XAML à partir de la **personnaliser la Page de démarrage** liste déroulante.  
  
5.  Dans le menu **Affichage** , cliquez sur **Page de démarrage**.  
  
     Votre page de démarrage personnalisée doit être affiché. Si vous souhaitez modifier les fichiers, vous devez fermez l’instance expérimentale, apporter les modifications, copiez et collez les fichiers modifiés, puis puis ouvrez à nouveau l’instance expérimentale pour afficher les modifications.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Pour appliquer le personnalisé page de démarrage dans l’instance principale de Visual Studio  
  
-   Après avoir testé votre Page de démarrage et a déterminé qu’il soit stable, utiliser le **personnaliser la Page de démarrage** option dans le **Options** boîte de dialogue pour le sélectionner comme page de démarrage dans l’instance principale de Visual Studio  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Ajout de code XAML personnalisé à la Page de démarrage](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Ajout du contrôle utilisateur à la Page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)   
 [Ajout de commandes de Visual Studio à une Page de démarrage](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Procédure pas à pas : Enregistrement des paramètres utilisateur sur une Page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Déploiement de Pages de démarrage personnalisées](../extensibility/deploying-custom-start-pages.md)
