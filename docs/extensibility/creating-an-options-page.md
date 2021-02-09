---
title: Création d’une page d’options | Microsoft Docs
description: Découvrez comment créer une page outils/options simple qui utilise une grille des propriétés pour examiner et définir des propriétés.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1069109cbda6b0385c9409a12f9f9c674ddec14c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877484"
---
# <a name="create-an-options-page"></a>Créer une page d’options

Cette procédure pas à pas crée une page outils/options simple qui utilise une grille des propriétés pour examiner et définir des propriétés.

 Pour enregistrer ces propriétés et les restaurer à partir d’un fichier de paramètres, procédez comme suit, puis consultez [créer une catégorie de paramètres](../extensibility/creating-a-settings-category.md).

 Le MPF fournit deux classes pour vous aider à créer des pages d’options Outils, la <xref:Microsoft.VisualStudio.Shell.Package> classe et la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Vous créez un VSPackage pour fournir un conteneur pour ces pages en sous-classant la `Package` classe. Vous créez chaque page d’options outils en dérivant de la `DialogPage` classe.

## <a name="prerequisites"></a>Prérequis

 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Créer une page de grille options des outils

 Dans cette section, vous allez créer une grille des propriétés options des outils simples. Vous utilisez cette grille pour afficher et modifier la valeur d’une propriété.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Pour créer le projet VSIX et ajouter un VSPackage

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX, qui contient les composants d’extension. Créez un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `MyToolsOptionsExtension` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».

2. Ajoutez un VSPackage en ajoutant un modèle d’élément de package Visual Studio nommé `MyToolsOptionsPackage` . Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**. Dans la **boîte de dialogue Ajouter un nouvel élément**, accédez à extensibilité des **éléments Visual C#**  >   et sélectionnez **package Visual Studio**. Dans le champ **nom** en bas de la boîte de dialogue, remplacez le nom de fichier par `MyToolsOptionsPackage.cs` . Pour plus d’informations sur la création d’un VSPackage, consultez [créer une extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Pour créer la grille des propriétés options des outils

1. Ouvrez le fichier *MyToolsOptionsPackage* dans l’éditeur de code.

2. Ajoutez l’instruction using suivante.

   ```csharp
   using System.ComponentModel;
   ```

3. Déclarez une `OptionPageGrid` classe et dérivez-la de <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Appliquez un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la `VSPackage` classe à assigner à la classe une catégorie d’options et un nom de page d’options pour le OptionPageGrid. Le résultat doit ressembler à ceci :

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Ajoutez une `OptionInteger` propriété à la `OptionPageGrid` classe.

    - Appliquez un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> à assigner à la propriété une catégorie de la grille des propriétés.

    - Appliquez un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> pour assigner un nom à la propriété.

    - Appliquez une <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> valeur à assigner à la propriété une description.

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
    > L’implémentation par défaut de <xref:Microsoft.VisualStudio.Shell.DialogPage> prend en charge les propriétés qui ont des convertisseurs appropriés ou qui sont des structures ou des tableaux qui peuvent être développés dans des propriétés qui ont des convertisseurs appropriés. Pour obtenir la liste des convertisseurs, consultez l' <xref:System.ComponentModel> espace de noms.

6. Générez le projet et commencez le débogage.

7. Dans l’instance expérimentale de Visual Studio, dans le menu **Outils** , cliquez sur **options**.

     Dans le volet gauche, vous devriez voir **ma catégorie**. (Les catégories d’options sont classées par ordre alphabétique. elles doivent donc apparaître à mi-chemin dans la liste.) Ouvrez **ma catégorie** , puis cliquez sur **ma page de grille**. La grille options s’affiche dans le volet droit. La catégorie de propriété est **My options** et le nom de propriété est **My Integer (option)**. L’option Description de la propriété, **mon entier**, s’affiche en bas du volet. Remplacez la valeur de la valeur initiale 256 par autre valeur. Cliquez sur **OK**, puis rouvrez la **page** de la grille. Vous pouvez voir que la nouvelle valeur persiste.

     Votre page d’options est également disponible via la zone de recherche de Visual Studio. Dans la zone de recherche située près du haut de l’IDE, tapez **ma catégorie** et vous verrez **ma catégorie-> la page** de la grille dans la liste des résultats.

## <a name="create-a-tools-options-custom-page"></a>Créer une page personnalisée d’options d’outils

 Dans cette section, vous allez créer une page outils options avec une interface utilisateur personnalisée. Cette page vous permet d’afficher et de modifier la valeur d’une propriété.

1. Ouvrez le fichier *MyToolsOptionsPackage* dans l’éditeur de code.

2. Ajoutez l’instruction using suivante.

    ```csharp
    using System.Windows.Forms;
    ```

3. Ajoutez une `OptionPageCustom` classe, juste avant la `OptionPageGrid` classe. Dérivez la nouvelle classe de `DialogPage` .

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

4. Ajoutez un attribut GUID. Ajoutez une propriété OptionString :

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

5. Appliquez une seconde <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la classe VSPackage. Cet attribut affecte à la classe une catégorie d’options et un nom de page d’options.

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

6. Ajoutez un nouveau **contrôle utilisateur** nommé MyUserControl au projet.

7. Ajoutez un contrôle **TextBox** au contrôle utilisateur.

     Dans la fenêtre **Propriétés** , dans la barre d’outils, cliquez sur le bouton **événements** , puis double-cliquez sur l’événement **Leave** . Le nouveau gestionnaire d’événements s’affiche dans le code *MyUserControl.cs* .

8. Ajoutez un `OptionsPage` champ public, une `Initialize` méthode à la classe de contrôle et mettez à jour le gestionnaire d’événements pour définir la valeur de l’option sur le contenu de la zone de texte :

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

     Le `optionsPage` champ contient une référence à l’instance parente `OptionPageCustom` . La `Initialize` méthode s’affiche `OptionString` dans la **zone de texte**. Le gestionnaire d’événements écrit la valeur actuelle de la **zone de texte** dans lorsque le `OptionString` focus quitte la zone de **texte**.

9. Dans le fichier de code du package, ajoutez une substitution pour la `OptionPageCustom.Window` propriété à la `OptionPageCustom` classe pour créer, initialiser et retourner une instance de `MyUserControl` . La classe doit maintenant ressembler à ceci :

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

11. Dans l’instance expérimentale, cliquez sur **Outils**  >  **options**.

12. Recherchez **ma catégorie** , puis **ma page personnalisée**.

13. Modifiez la valeur de **OptionString**. Cliquez sur **OK**, puis rouvrez la **page personnalisée**. Vous pouvez voir que la nouvelle valeur est persistante.

## <a name="access-options"></a>Options d’accès

 Dans cette section, vous allez récupérer la valeur d’une option à partir du VSPackage qui héberge la page outils/options associée. La même technique peut être utilisée pour obtenir la valeur de n’importe quelle propriété publique.

1. Dans le fichier de code du package, ajoutez une propriété publique appelée **OptionInteger** à la classe **MyToolsOptionsPackage** .

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Ce code appelle <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> pour créer ou récupérer une `OptionPageGrid` instance. `OptionPageGrid` appelle <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> pour charger ses options, qui sont des propriétés publiques.

2. Ajoutez maintenant un modèle d’élément de commande personnalisé nommé **MyToolsOptionsCommand** pour afficher la valeur. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à extensibilité **Visual C#**  >   et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par *MyToolsOptionsCommand.cs*.

3. Dans le fichier *MyToolsOptionsCommand* , remplacez le corps de la méthode de la commande `ShowMessageBox` par ce qui suit :

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Générez le projet et commencez le débogage.

5. Dans l’instance expérimentale, dans le menu **Outils** , cliquez sur **appeler MyToolsOptionsCommand**.

     Une boîte de message affiche la valeur actuelle de `OptionInteger` .

## <a name="see-also"></a>Voir aussi

- [Pages Options et options](../extensibility/internals/options-and-options-pages.md)
