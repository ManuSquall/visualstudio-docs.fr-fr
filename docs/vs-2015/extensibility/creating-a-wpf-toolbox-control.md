---
title: Création d’un contrôle de boîte à outils WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 768d9747635f2106d16f755db6799e356c890838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197434"
---
# <a name="creating-a-wpf-toolbox-control"></a>Création d’un contrôle de boîte à outils WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le modèle de contrôle de boîte à outils WPF (Windows Presentation Framework) vous permet de créer des contrôles WPF qui sont automatiquement ajoutés à la **boîte à outils** lorsque l’extension est installée. Cette rubrique montre comment utiliser le modèle pour créer un contrôle de **boîte à outils** que vous pouvez distribuer à d’autres utilisateurs.  
  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Création d’un contrôle de boîte à outils WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Créer une extension avec un contrôle de boîte à outils WPF  
  
1. Créez un projet VSIX nommé `MyToolboxControl` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** sous **Visual C#/extensibilité**.  
  
2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de **contrôle de boîte à outils WPF** nommé `MyToolboxControl` . Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C#/extensibilité** et sélectionnez **contrôle de boîte à outils WPF**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par `MyToolboxControl.cs` .  
  
     La solution contient maintenant un contrôle utilisateur, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> qui ajoute le contrôle à la **boîte à outils**et une entrée de ressource **Microsoft. VisualStudio. ToolboxControl** dans le manifeste VSIX pour le déploiement.  
  
#### <a name="to-create-the-control-ui"></a>Pour créer l’interface utilisateur du contrôle  
  
1. Ouvrez MyToolboxControl. xaml dans le concepteur.  
  
     Le concepteur affiche un contrôle <xref:System.Windows.Controls.Grid> contenant un contrôle <xref:System.Windows.Controls.Button>.  
  
2. Organiser la disposition de la grille. Lorsque vous sélectionnez le <xref:System.Windows.Controls.Grid> contrôle, les barres de contrôle bleues apparaissent sur les bords supérieur et gauche de la grille. Vous pouvez ajouter des lignes et des colonnes à la grille en cliquant sur les barres.  
  
3. Ajoutez des contrôles enfants à la grille. Vous pouvez positionner un contrôle enfant en le faisant glisser de la **boîte à outils** vers une section de la grille, ou en définissant ses `Grid.Row` `Grid.Column` attributs et dans le XAML. L’exemple suivant ajoute deux étiquettes sur la ligne supérieure de la grille et un bouton sur la deuxième ligne.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Attribution d’un nouveau nom au contrôle  
 Par défaut, votre contrôle s’affiche dans la **boîte à outils** en tant que **MyToolboxControl** dans un groupe nommé **MyToolboxControl. MyToolboxControl**. Vous pouvez modifier ces noms dans le fichier MyToolboxControl.xaml.cs.  
  
1. Ouvrez MyToolboxControl.xaml.cs dans le mode Code.  
  
2. Recherchez la classe MyToolboxControl et renommez-la TestControl. (Le moyen le plus rapide consiste à renommer la classe, puis à sélectionner **Renommer** dans le menu contextuel et à effectuer les étapes. (Pour plus d’informations sur la commande **Rename** , consultez [refactorisation de changement de nom (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3. Accédez à l' `ProvideToolboxControl` attribut et remplacez la valeur du premier paramètre par **test**. Il s’agit du nom du groupe qui contiendra le contrôle dans la **boîte à outils**.  
  
     Le code obtenu doit ressembler à ceci :  
  
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
 Lorsque vous déboguez le projet, vous devez trouver le contrôle installé dans la **boîte à outils** de l’instance expérimentale de Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Pour générer et tester le contrôle  
  
1. Régénérez le projet et démarrez le débogage.  
  
2. Dans la nouvelle instance de Visual Studio, créez un projet d’application WPF. Assurez-vous que le Concepteur XAML est ouvert.  
  
3. Recherchez votre contrôle dans la **boîte à outils** et faites-la glisser vers l’aire de conception.  
  
4. Démarrez le débogage de l’application WPF.  
  
5. Vérifiez que votre contrôle s’affiche.  
  
#### <a name="to-deploy-the-control"></a>Pour déployer le contenu  
  
1. Après avoir généré le projet testé, vous pouvez trouver le fichier. VSIX dans le dossier \bin\debug\ du projet.  
  
2. Vous pouvez l’installer sur un ordinateur local en double-cliquant sur le fichier. vsix et en suivant la procédure d’installation. Pour désinstaller le contrôle, accédez à **Outils/extensions et mises à jour** , recherchez l’extension de contrôle, puis cliquez sur **désinstaller**.  
  
3. Chargez le fichier .vsix sur un réseau ou un site web.  
  
     Si vous téléchargez le fichier sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , d’autres utilisateurs peuvent utiliser **Outils/extensions et mises à jour** dans Visual Studio pour rechercher le contrôle en ligne et l’installer.
