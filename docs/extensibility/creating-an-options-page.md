---
title: "Cr&#233;ation d’une Page d’Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pages Outils Options [Kit de développement logiciel (SDK) Visual Studio], créer"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 62
---
# Cr&#233;ation d’une Page d’Options
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas crée une page Outils\/Options simple qui utilise une grille de propriétés pour examiner et définir des propriétés.  
  
 Pour enregistrer ces propriétés et les restaurer à partir d’un fichier de paramètres, procédez comme suit, puis consultez [Création d’une catégorie de paramètres](../extensibility/creating-a-settings-category.md).  
  
 Le MPF fournit deux classes pour vous aider à créer des pages d’Options Outils, la <xref:Microsoft.VisualStudio.Shell.Package> classe et la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Vous créez un VSPackage afin de fournir un conteneur pour ces pages en sous\-classant la classe de Package. Vous créez chaque page d’options Outils en dérivant de la classe DialogPage.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’une Page de grille d’Options Outils  
 Dans cette section, vous créez une grille de propriétés Outils\/Options simple. Vous utilisez cette grille pour afficher et modifier la valeur d’une propriété.  
  
#### Pour créer le projet VSIX et ajouter un VSPackage  
  
1.  Chaque extension de Visual Studio démarre avec un projet de déploiement VSIX qui contient les composants d’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `MyToolsOptionsExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\# \/ extensibilité**.  
  
2.  Ajouter un package VS en ajoutant un modèle d’élément de Package Visual Studio nommé `MyToolsOptionsPackage`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **boîte de dialogue Ajouter un nouvel élément**, accédez à **éléments Visual C\# \/ extensibilité** et sélectionnez **Package Visual Studio**. Dans le **nom** en bas de la boîte de dialogue, modifiez le nom du fichier à `MyToolsOptionsPackage.cs`. Pour plus d’informations sur la création d’un VSPackage, consultez [Création d'une Extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### Pour créer la grille des propriétés Outils\/Options  
  
1.  Ouvrez le fichier MyToolsOptionsPackage dans l’éditeur de code.  
  
2.  Ajoutez le code suivant à l’aide d’instruction.  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  Déclarez une classe OptionPageGrid et dériver de <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Appliquer une <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la classe VSPackage à affecter à la classe une catégorie d’options et le nom de la page options pour le OptionPageGrid. Le résultat doit ressembler à ceci :  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Ajouter un `OptionInteger` propriété du `OptionPageGrid` classe.  
  
    -   Appliquer un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> à affecter à la propriété d’une catégorie de la grille des propriétés.  
  
    -   Appliquer un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> à affecter à la propriété d’un nom.  
  
    -   Appliquer un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> à affecter à la propriété description.  
  
    ```c#  
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
    >  L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> prend en charge les propriétés convertisseurs appropriés ou qui sont des structures ou des tableaux qui peuvent être développés dans les propriétés qui ont des convertisseurs appropriés. Pour obtenir la liste des convertisseurs, consultez la <xref:System.ComponentModel> espace de noms.  
  
6.  Générez le projet et commencez le débogage.  
  
7.  Dans l’instance expérimentale de Visual Studio, sur le **outils** menu, cliquez sur **Options**.  
  
     Dans le volet gauche, vous devez voir **Mes catégorie**. \(Les catégories d’options sont répertoriées par ordre alphabétique, afin qu’il doit apparaître sur à mi\-chemin vers le bas de la liste.\) Ouvrez **Mes catégorie** puis cliquez sur **Ma Page de grille**. La grille d’options s’affiche dans le volet droit. La catégorie de propriété est **Mes Options de**, et le nom de propriété est **Mes Option entier**. La description de la propriété **mon option entier**, apparaît en bas du volet. Modifiez la valeur de sa valeur initiale de 256 à quelque chose d’autre. Cliquez sur **OK**, puis rouvrez **Ma Page de grille**. Vous pouvez voir que la nouvelle valeur est conservée.  
  
     Votre page d’options est également accessible via le lancement rapide de Visual Studio. Dans la fenêtre lancement rapide dans l’angle supérieur droit de l’IDE, tapez **Mes catégorie** et vous verrez **Mes catégorie \-\> Page de grille** répertoriés dans la liste déroulante.  
  
## Création d’un fichier d’Options Outils Page  
 Dans cette section, vous créez une page Outils\/Options avec une interface utilisateur personnalisée. Cette page vous permet d’afficher et modifier la valeur d’une propriété.  
  
1.  Ouvrez le fichier MyToolsOptionsPackage dans l’éditeur de code.  
  
2.  Ajoutez le code suivant à l’aide d’instruction.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Ajouter un `OptionPageCustom` classe, juste avant la `OptionPageGrid` classe. Dérive de la nouvelle classe `DialogPage`.  
  
    ```c#  
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
  
    ```c#  
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
  
5.  Appliquer une seconde <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la classe VSPackage. Cet attribut affecte la classe une catégorie d’options et le nom de la page options.  
  
    ```c#  
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
  
7.  Ajouter un **TextBox** contrôle au contrôle utilisateur.  
  
     Dans le **propriétés** sur la barre d’outils, cliquez sur le **événements** bouton, puis double\-cliquez sur le **laisser** événement. Le nouveau gestionnaire d’événements s’affiche dans le code du fichier MyUserControl.cs.  
  
8.  Ajouter un public `OptionsPage` champ, une `Initialize` méthode à la classe de contrôle et la mise à jour le Gestionnaire d’événements pour définir l’option de valeur pour le contenu de la zone de texte :  
  
    ```c#  
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
  
     Le `optionsPage` champ contient une référence au parent `OptionPageCustom` instance. Le `Initialize` méthode affiche `OptionString` dans les **TextBox**. Le Gestionnaire d’événements écrit la valeur actuelle de la **TextBox** à le `OptionString` lorsque vous concentrer laisse le **TextBox**.  
  
9. Dans le fichier de code de package, ajoutez un remplacement pour le `OptionPageCustom.Window` propriété à créer, initialiser et retourner une instance de la classe OptionPageCustom `MyUserControl`. La classe doit maintenant ressembler à ceci :  
  
    ```c#  
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
  
11. Dans l’instance expérimentale, cliquez sur **Outils \/ Options**.  
  
12. Rechercher **Me catégorie** puis **Me personnalisé Page**.  
  
13. Modifiez la valeur de **OptionString**. Cliquez sur **OK**, puis rouvrez **Page personnalisée Mes**. Vous pouvez voir que la nouvelle valeur est persistante.  
  
## Accès aux Options  
 Dans cette section, vous obtenez la valeur d’une option dans le VSPackage qui héberge la page Outils\/Options associée. La même technique peut être utilisée pour obtenir la valeur d’une propriété publique.  
  
1.  Dans le fichier de code de package, ajoutez une propriété publique nommée **OptionInteger** à la **MyToolsOptionsPackage** \(classe\).  
  
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
  
     Ce code appelle <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> pour créer ou récupérer une `OptionPageGrid` instance.`OptionPageGrid` appels <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> pour charger ses options, qui sont des propriétés publiques.  
  
2.  Ajoutez maintenant un modèle d’élément commande personnalisée nommé **MyToolsOptionsCommand** pour afficher la valeur. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom du fichier de commandes **MyToolsOptionsCommand.cs**.  
  
3.  Dans le fichier MyToolsOptionsCommand, remplacez le corps de la commande `ShowMessageBox` méthode par le code suivant :  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Générez le projet et commencez le débogage.  
  
5.  Dans l’instance expérimentale, sur le **outils** menu, cliquez sur **MyToolsOptionsCommand appeler**.  
  
     Une boîte de message affiche la valeur actuelle de `OptionInteger`.  
  
## Voir aussi  
 [Options et Pages d’Options](../extensibility/internals/options-and-options-pages.md)