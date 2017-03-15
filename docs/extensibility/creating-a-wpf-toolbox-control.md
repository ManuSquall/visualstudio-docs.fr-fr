---
title: "Cr&#233;ation d’un contr&#244;le de bo&#238;te &#224; outils WPF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de boîte à outils"
  - "boîte à outils"
  - "wpf"
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Cr&#233;ation d’un contr&#244;le de bo&#238;te &#224; outils WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le modèle de contrôle de boîte à outils WPF \(Windows Presentation Framework\) vous permet de créer des contrôles WPF sont automatiquement ajoutées à la **boîte à outils** lorsque l’extension est installée. Cette rubrique montre comment utiliser le modèle pour créer un **boîte à outils** contrôle que vous pouvez distribuer à d’autres utilisateurs.  
  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’un contrôle de boîte à outils WPF  
  
#### Créez une Extension d’un contrôle de boîte à outils WPF  
  
1.  Créez un projet VSIX nommé `MyToolboxControl`. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\# \/ extensibilité**.  
  
2.  Lorsque le projet s’ouvre, ajoutez un **contrôle de boîte à outils WPF** modèle d’élément nommé `MyToolboxControl`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **contrôle de boîte à outils WPF**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour `MyToolboxControl.cs`.  
  
     La solution contient à présent un contrôle utilisateur, un `ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> qui ajoute le contrôle à la **boîte à outils**, et un **Microsoft.VisualStudio.ToolboxControl** entrée de ressource dans le manifeste VSIX pour le déploiement.  
  
#### Pour créer le contrôle de l’interface utilisateur  
  
1.  Ouvrez MyToolboxControl.xaml dans le concepteur.  
  
     Le concepteur affiche un contrôle <xref:System.Windows.Controls.Grid> contenant un contrôle <xref:System.Windows.Controls.Button>.  
  
2.  Modifier la disposition de grille. Lorsque vous sélectionnez le <xref:System.Windows.Controls.Grid> contrôler, barres de contrôles bleu apparaissent sur les bords supérieur et gauche de la grille. Vous pouvez ajouter des lignes et des colonnes à la grille en cliquant sur les barres.  
  
3.  Ajouter des contrôles enfants à la grille. Vous pouvez positionner un contrôle enfant en le faisant glisser à partir de la **boîte à outils** à une section de la grille, ou en définissant son `Grid.Row` et `Grid.Column` attributs en XAML. L’exemple suivant ajoute deux contrôles Label sur la ligne supérieure de la grille et un bouton sur la deuxième ligne.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## Renommer le contrôle  
 Par défaut, votre contrôle s’affiche dans le **boîte à outils** en tant que **MyToolboxControl** dans un groupe appelé **MyToolboxControl.MyToolboxControl**. Vous pouvez modifier ces noms dans le fichier MyToolboxControl.xaml.cs.  
  
1.  Ouvrez MyToolboxControl.xaml.cs en mode code.  
  
2.  Recherchez la classe MyToolboxControl et renommez\-le TestControl. \(Le moyen le plus rapide consiste à renommer la classe, puis sélectionnez **Renommer** dans le menu contextuel et suivez les étapes. \(Pour plus d’informations sur le **Renommer** de commande, consultez [Refactorisation de changement de nom \(C\#\)](../csharp-ide/rename-refactoring-csharp.md).\)  
  
3.  Accédez à le `ProvideToolboxControl` d’attribut et modifiez la valeur du premier paramètre pour **Test**. Il s’agit du nom du groupe qui contiendra le contrôle dans le **boîte à outils**.  
  
     Le code obtenu doit ressembler à ceci :  
  
    ```c#  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## Génération, test et déploiement  
 Lorsque vous déboguez le projet, vous devez trouver le contrôle est installé dans le **boîte à outils** de l’instance expérimentale de Visual Studio.  
  
#### Pour générer et tester le contrôle  
  
1.  Régénérez le projet et démarrer le débogage.  
  
2.  Dans la nouvelle instance de Visual Studio, créez un projet d’application WPF. Assurez\-vous que le concepteur XAML est ouvert.  
  
3.  Recherchez votre contrôle dans la **boîte à outils** et faites\-la glisser vers l’aire de conception.  
  
4.  Démarrez le débogage de l’application WPF.  
  
5.  Vérifiez que votre contrôle s’affiche.  
  
#### Pour déployer le contenu  
  
1.  Une fois que vous générez le projet testé, vous trouverez le fichier .vsix dans le dossier \\bin\\debug\\ du projet.  
  
2.  Vous pouvez l’installer sur un ordinateur local en double\-cliquant sur le fichier .vsix et en suivant la procédure d’installation. Pour désinstaller le contrôle, accédez à **Outils \/ Extensions et mises à jour** et recherchez l’extension de contrôle, puis cliquez sur **désinstallation**.  
  
3.  Chargez le fichier .vsix sur un réseau ou un site web.  
  
     Si vous téléchargez le fichier vers le [la galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site Web, les autres utilisateurs peuvent utiliser **Outils \/ Extensions et mises à jour** dans Visual Studio pour rechercher le contrôle en ligne et l’installer.