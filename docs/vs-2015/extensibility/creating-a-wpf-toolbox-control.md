---
title: Création d’un contrôle de boîte à outils WPF | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0785ebf5177e892bd5c450525af10dd61d381fc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496145"
---
# <a name="creating-a-wpf-toolbox-control"></a>Création d’un contrôle de boîte à outils WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [création d’un contrôle de boîte à outils WPF](https://docs.microsoft.com/visualstudio/extensibility/creating-a-wpf-toolbox-control).  
  
Le modèle de contrôle de boîte à outils WPF (Windows Presentation Framework) vous permet de créer des contrôles WPF qui sont automatiquement ajoutés à la **boîte à outils** lorsque l’extension est installée. Cette rubrique montre comment utiliser le modèle pour créer un **boîte à outils** contrôle que vous pouvez distribuer à d’autres utilisateurs.  
  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Création d’un contrôle de boîte à outils WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Créer une Extension avec un contrôle de boîte à outils WPF  
  
1.  Créez un projet VSIX nommé `MyToolboxControl`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Quand le projet s’ouvre, ajoutez un **contrôle de boîte à outils WPF** modèle d’élément nommé `MyToolboxControl`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **contrôle de boîte à outils WPF**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour `MyToolboxControl.cs`.  
  
     La solution contient maintenant un contrôle utilisateur, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> qui ajoute le contrôle à la **boîte à outils**et un **Microsoft.VisualStudio.ToolboxControl** dans le manifeste VSIX pour l’entrée de composant  déploiement.  
  
#### <a name="to-create-the-control-ui"></a>Pour créer le contrôle de l’interface utilisateur  
  
1.  Ouvrez MyToolboxControl.xaml dans le concepteur.  
  
     Le concepteur affiche un <xref:System.Windows.Controls.Grid> contrôle contenant un <xref:System.Windows.Controls.Button> contrôle.  
  
2.  Organiser la disposition de grille. Lorsque vous sélectionnez le <xref:System.Windows.Controls.Grid> contrôler, les barres de contrôle bleues apparaissent sur les bords supérieur et gauche de la grille. Vous pouvez ajouter des lignes et des colonnes à la grille en cliquant sur les barres.  
  
3.  Ajouter des contrôles enfants à la grille. Vous pouvez positionner un contrôle enfant en le faisant glisser à partir de la **boîte à outils** à une section de la grille, ou en définissant son `Grid.Row` et `Grid.Column` attributs dans le XAML. L’exemple suivant ajoute deux étiquettes sur la ligne du haut de la grille et un bouton sur la deuxième ligne.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Renommer le contrôle  
 Par défaut, votre contrôle apparaît dans le **boîte à outils** comme **MyToolboxControl** dans un groupe nommé **MyToolboxControl.MyToolboxControl**. Vous pouvez modifier ces noms dans le fichier MyToolboxControl.xaml.cs.  
  
1.  Ouvrez MyToolboxControl.xaml.cs en mode code.  
  
2.  Rechercher la classe MyToolboxControl et renommez-le TestControl. (Le plus rapide pour ce faire consiste à renommer la classe, puis sélectionnez **renommer** dans le menu contextuel et effectuez les étapes. (Pour plus d’informations sur la **renommer** de commande, consultez [Renommer (refactorisation c#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3.  Accédez à la `ProvideToolboxControl` d’attribut et modifiez la valeur du premier paramètre à **Test**. Il s’agit du nom du groupe qui contiendra le contrôle dans le **boîte à outils**.  
  
     Le code résultant doit ressembler à ceci :  
  
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
  
## <a name="building-testing-and-deployment"></a>Génération, test et déploiement  
 Lorsque vous déboguez le projet, vous devez rechercher le contrôle est installé dans le **boîte à outils** de l’instance expérimentale de Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle  
  
1.  Régénérez le projet et démarrer le débogage.  
  
2.  Dans la nouvelle instance de Visual Studio, créez un projet d’application WPF. Assurez-vous que le concepteur XAML est ouvert.  
  
3.  Recherchez votre contrôle dans la **boîte à outils** et faites-la glisser vers l’aire de conception.  
  
4.  Démarrez le débogage de l’application WPF.  
  
5.  Vérifiez que votre contrôle s’affiche.  
  
#### <a name="to-deploy-the-control"></a>Pour déployer le contenu  
  
1.  Une fois que vous générez le projet testé, vous trouverez le fichier .vsix dans le dossier \bin\debug\ du projet.  
  
2.  Vous pouvez l’installer sur un ordinateur local en double-cliquant sur le fichier .vsix et en suivant la procédure d’installation. Pour désinstaller le contrôle, accédez à **outils / Extensions et mises à jour** et recherchez l’extension de contrôle, puis cliquez sur **désinstallation**.  
  
3.  Chargez le fichier .vsix sur un réseau ou un site web.  
  
     Si vous chargez le fichier à la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site Web, les autres utilisateurs peuvent utiliser **outils / Extensions et mises à jour** dans Visual Studio pour rechercher le contrôle en ligne et l’installer.
