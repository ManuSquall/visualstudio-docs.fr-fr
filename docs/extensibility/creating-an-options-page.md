---
title: Création d’une Page d’Options | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d0888a584e31c26c9f64cdcff70cc2f5dc8a1453
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2018
---
# <a name="creating-an-options-page"></a>Création d’une Page d’Options
Cette procédure pas à pas crée une page Outils/Options simple qui utilise une grille de propriétés pour examiner et définir des propriétés.  
  
 Pour enregistrer ces propriétés et les restaurer à partir d’un fichier de paramètres, procédez comme suit, puis consultez [création d’une catégorie de paramètres](../extensibility/creating-a-settings-category.md).  
  
 MPF fournit deux classes pour vous aider à créer des pages Outils Options, la <xref:Microsoft.VisualStudio.Shell.Package> classe et la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Vous créez un VSPackage pour fournir un conteneur pour ces pages en sous-classant la classe de Package. Vous créez chaque page d’options Outils en dérivant de la classe de DialogPage.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Création d’une Page de grille d’Options Outils  
 Dans cette section, vous créez une grille de propriétés Options d’outils simple. Vous utilisez cette grille pour afficher et modifier la valeur d’une propriété.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Pour créer le projet VSIX et ajouter un VSPackage  
  
1.  Chaque extension de Visual Studio commence par un projet de déploiement VSIX qui contient les composants d’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `MyToolsOptionsExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Ajouter un VSPackage en ajoutant un modèle d’élément de Package Visual Studio nommé `MyToolsOptionsPackage`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **boîte de dialogue Ajouter un nouvel élément**, accédez à **éléments Visual c# / extensibilité** et sélectionnez **Package Visual Studio**. Dans le **nom** au bas de la boîte de dialogue, modifiez le nom de fichier à `MyToolsOptionsPackage.cs`. Pour plus d’informations sur la création d’un VSPackage, consultez [création d’une Extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Pour créer la grille des propriétés Outils/Options  
  
1.  Ouvrez le fichier MyToolsOptionsPackage dans l’éditeur de code.  
  
2.  Ajoutez le code suivant à l’aide d’instruction.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Déclarer une classe OptionPageGrid et dériver de <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Appliquer un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la classe VSPackage à affecter à la classe une catégorie d’options et le nom de la page options pour le OptionPageGrid. Le résultat doit ressembler à ceci :  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Ajouter un `OptionInteger` propriété le `OptionPageGrid` classe.  
  
    -   Appliquer un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> à affecter à la propriété d’une catégorie de la grille des propriétés.  
  
    -   Appliquer un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> pour attribuer à la propriété d’un nom.  
  
    -   Appliquer un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> à affecter à la propriété description.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> prend en charge les propriétés appropriées convertisseurs ou qui sont des structures ou les tableaux qui peuvent être étendus dans les propriétés qui ont des convertisseurs appropriés. Pour obtenir la liste des convertisseurs, consultez la <xref:System.ComponentModel> espace de noms.  
  
6.  Générez le projet et commencez le débogage.  
  
7.  Dans l’instance expérimentale de Visual Studio, sur le **outils** menu, cliquez sur **Options**.  
  
     Dans le volet gauche, vous devez voir **catégorie Mes**. (Les catégories d’options sont répertoriées par ordre alphabétique, afin qu’il doit apparaître sur à mi-chemin vers le bas de la liste.) Ouvrez **catégorie Mes** puis cliquez sur **ma Page de grille**. La grille d’options s’affiche dans le volet droit. La catégorie de propriété est **mes Options de**, et le nom de propriété est **mon Option de nombre entier**. La description de la propriété, **mon option entier**, apparaît au bas du volet. Remplacez la valeur de sa valeur initiale de 256 par autre chose. Cliquez sur **OK**, puis rouvrez **ma Page de grille**. Vous pouvez voir que la nouvelle valeur est conservée.  
  
     Votre page d’options est également disponible via le menu de lancement rapide de Visual Studio. Dans la fenêtre lancement rapide dans le coin supérieur droit de l’IDE, tapez **catégorie Mes** et vous verrez **catégorie Mes -> Page de grille** répertoriés dans la liste déroulante.  
  
## <a name="creating-a-tools-options-custom-page"></a>Création d’un fichier d’Options Outils Page  
 Dans cette section, vous créez une page Outils/Options avec une interface utilisateur personnalisée. Vous utilisez cette page pour afficher et modifier la valeur d’une propriété.  
  
1.  Ouvrez le fichier MyToolsOptionsPackage dans l’éditeur de code.  
  
2.  Ajoutez le code suivant à l’aide d’instruction.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Ajouter un `OptionPageCustom` classe juste avant la `OptionPageGrid` classe. Dérivez la nouvelle classe à partir de `DialogPage`.  
  
    ```csharp  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  Ajoutez un attribut GUID. Ajoutez une propriété OptionString :  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  Appliquer une seconde <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la classe VSPackage. Cet attribut affecte la classe d’une catégorie d’options et le nom de la page options.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  Ajouter un nouveau **contrôle utilisateur** nommé MyUserControl au projet.  
  
7.  Ajouter un **TextBox** vers le contrôle utilisateur.  
  
     Dans le **propriétés** sur la barre d’outils, cliquez sur le **événements** bouton, puis double-cliquez sur le **laisser** événement. Le Gestionnaire d’événements s’affiche dans le code MyUserControl.cs.  
  
8.  Ajouter un public `OptionsPage` champ, une `Initialize` méthode à la classe de contrôle et la mise à jour le Gestionnaire d’événements pour définir l’option de valeur pour le contenu de la zone de texte :  
  
    ```csharp  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     Le `optionsPage` champ contient une référence au parent `OptionPageCustom` instance. Le `Initialize` méthode affiche `OptionString` dans les **zone de texte**. Le Gestionnaire d’événements écrit la valeur actuelle de la **zone de texte** à la `OptionString` lorsque vous concentrer laisse le **zone de texte**.  
  
9. Dans le fichier de code de package, ajoutez un remplacement pour le `OptionPageCustom.Window` propriété à la classe OptionPageCustom pour créer, initialiser et retourner une instance de `MyUserControl`. La classe doit maintenant ressembler à ceci :  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Générez et exécutez le projet.  
  
11. Dans l’instance expérimentale, cliquez sur **Outils / Options**.  
  
12. Rechercher **ma catégorie** , puis **mon personnalisé Page**.  
  
13. Modifiez la valeur de **OptionString**. Cliquez sur **OK**, puis rouvrez **ma Page personnalisée**. Vous pouvez voir que la nouvelle valeur a rendu persistant.  
  
## <a name="accessing-options"></a>Accès aux Options  
 Dans cette section, vous obtenez la valeur d’une option du VSPackage qui héberge la page d’Options des outils associée. La même technique peut être utilisée pour obtenir la valeur d’une propriété publique.  
  
1.  Dans le fichier de code de package, ajoutez une propriété publique appelée **OptionInteger** à la **MyToolsOptionsPackage** classe.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Ce code appelle <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> à créer ou récupérer un `OptionPageGrid` instance. `OptionPageGrid` appels <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> pour charger ses options, qui sont des propriétés publiques.  
  
2.  Maintenant ajouter un modèle d’élément de commande personnalisée nommé **MyToolsOptionsCommand** pour afficher la valeur. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** au bas de la fenêtre, modifiez le nom de fichier de commande pour **MyToolsOptionsCommand.cs**.  
  
3.  Dans le fichier MyToolsOptionsCommand, remplacez le corps de la commande `ShowMessageBox` méthode avec les éléments suivants :  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Générez le projet et commencez le débogage.  
  
5.  Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **MyToolsOptionsCommand d’appeler**.  
  
     Une boîte de message affiche la valeur actuelle de `OptionInteger`.  
  
## <a name="see-also"></a>Voir aussi  
 [Options et pages Options](../extensibility/internals/options-and-options-pages.md)