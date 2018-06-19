---
title: Création d’un contrôle de boîte à outils WPF | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b8bfbde2459998f13b8b19b17cfecba172538aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107801"
---
# <a name="creating-a-wpf-toolbox-control"></a>Création d’un contrôle de boîte à outils WPF
Le modèle de contrôle de boîte à outils WPF (Windows Presentation Framework) vous permet de créer des contrôles WPF sont automatiquement ajoutés à la **boîte à outils** lorsque l’extension est installée. Cette rubrique montre comment utiliser le modèle pour créer un **boîte à outils** contrôle que vous pouvez distribuer à d’autres utilisateurs.  
  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Création d’un contrôle de boîte à outils WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Créer une Extension avec un contrôle de boîte à outils WPF  
  
1.  Créez un projet VSIX nommé `MyToolboxControl`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Lorsque le projet s’ouvre, ajoutez un **contrôle de boîte à outils WPF** modèle d’élément nommé `MyToolboxControl`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **contrôle de boîte à outils WPF**. Dans le **nom** au bas de la fenêtre, modifiez le nom de fichier de commande pour `MyToolboxControl.cs`.  
  
     La solution contient désormais un contrôle utilisateur, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> qui ajoute le contrôle à la **boîte à outils**et un **Microsoft.VisualStudio.ToolboxControl** entrée de ressource dans le manifeste VSIX pour  déploiement.  
  
#### <a name="to-create-the-control-ui"></a>Pour créer le contrôle de l’interface utilisateur  
  
1.  Ouvrez MyToolboxControl.xaml dans le concepteur.  
  
     Le concepteur affiche un <xref:System.Windows.Controls.Grid> contrôle contenant un <xref:System.Windows.Controls.Button> contrôle.  
  
2.  Modifier la disposition de grille. Lorsque vous sélectionnez le <xref:System.Windows.Controls.Grid> contrôler, barres de contrôles bleu apparaissent sur les bords supérieur et gauche de la grille. Vous pouvez ajouter des lignes et des colonnes à la grille en cliquant sur les barres.  
  
3.  Ajouter des contrôles enfants dans la grille. Vous pouvez positionner un contrôle enfant en le faisant glisser à partir de la **boîte à outils** à une section de la grille, ou en définissant sa `Grid.Row` et `Grid.Column` attributs dans le code XAML. L’exemple suivant ajoute deux contrôles Label sur la ligne du haut de la grille et un bouton sur la deuxième ligne.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Renommer le contrôle  
 Par défaut, votre contrôle s’affiche dans le **boîte à outils** en tant que **MyToolboxControl** dans un groupe nommé **MyToolboxControl.MyToolboxControl**. Vous pouvez modifier ces noms dans le fichier MyToolboxControl.xaml.cs.  
  
1.  Ouvrez MyToolboxControl.xaml.cs dans le mode code.  
  
2.  Rechercher la classe MyToolboxControl et renommez-le TestControl. (La plus rapide pour ce faire consiste à renommer la classe, puis sélectionnez **renommer** dans le menu contextuel et effectuez les étapes. (Pour plus d’informations sur la **renommer** command, consultez [Renommer (refactorisation c#)](../ide/reference/rename.md).)
  
3.  Accédez à la `ProvideToolboxControl` d’attribut et modifiez la valeur du premier paramètre à **Test**. Il s’agit du nom du groupe qui contient le contrôle dans le **boîte à outils**.  
  
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
  
     Si vous téléchargez le fichier à la [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site Web, les autres utilisateurs peuvent utiliser **outils / Extensions et mises à jour** dans Visual Studio pour rechercher le contrôle en ligne et l’installer.