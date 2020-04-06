---
title: Création d’une page Options (en anglais) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739515"
---
# <a name="create-an-options-page"></a>Créer une page d’options

Cette procédure pas à pas crée une page Tools/Options simple qui utilise une grille de propriété pour examiner et définir les propriétés.

 Pour enregistrer ces propriétés et les restaurer à partir d’un fichier de paramètres, suivez ces étapes, puis consultez [une catégorie de paramètres](../extensibility/creating-a-settings-category.md).

 Le MPF propose deux classes pour vous <xref:Microsoft.VisualStudio.Shell.Package> aider à <xref:Microsoft.VisualStudio.Shell.DialogPage> créer des pages Tools Options, la classe et la classe. Vous créez un VSPackage pour fournir un conteneur `Package` pour ces pages en sous-classant la classe. Vous créez chaque page d’options `DialogPage` d’outils en provenant de la classe.

## <a name="prerequisites"></a>Prérequis

 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Créer une page de grille Tools Options

 Dans cette section, vous créez une simple grille de propriété Tools Options. Vous utilisez cette grille pour afficher et modifier la valeur d’une propriété.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Créer le projet VSIX et ajouter un VSPackage

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX, qui contiendra les actifs d’extension. Créer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un projet `MyToolsOptionsExtension`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Ajoutez un VSPackage en ajoutant un `MyToolsOptionsPackage`modèle d’article Visual Studio Package nommé . Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le **dialogue Add New Item**, rendez-vous sur Visual **C’Items** > **Extensibility** et sélectionnez **Visual Studio Package**. Dans le champ **Nom** au bas du dialogue, `MyToolsOptionsPackage.cs`changer le nom du fichier à . Pour plus d’informations sur la façon de créer un VSPackage, voir [Créer une extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Créer le réseau de propriété Tools Options

1. Ouvrez le fichier *MyToolsOptionsPackage* dans l’éditeur de code.

2. Ajouter l’instruction suivante à l’aide de l’instruction.

   ```csharp
   using System.ComponentModel;
   ```

3. Déclarez `OptionPageGrid` une classe <xref:Microsoft.VisualStudio.Shell.DialogPage>et dérivez-la de .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Appliquer <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> un `VSPackage` à la classe pour attribuer à la classe une catégorie d’options et le nom de page d’options pour l’OptionPageGrid. Le résultat devrait ressembler à ceci:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Ajoutez `OptionInteger` une propriété `OptionPageGrid` à la classe.

    - Appliquer <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> un pour attribuer à la propriété une catégorie de réseau de propriété.

    - Appliquer <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> un pour attribuer à la propriété un nom.

    - Appliquer <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> un pour attribuer à la propriété une description.

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
    > La mise <xref:Microsoft.VisualStudio.Shell.DialogPage> en œuvre par défaut des propriétés de support qui ont des convertisseurs appropriés ou qui sont des structures ou des tableaux qui peuvent être élargis en propriétés qui ont des convertisseurs appropriés. Pour une liste de convertisseurs, voir l’espace <xref:System.ComponentModel> nom.

6. Générez le projet et commencez le débogage.

7. Dans l’exemple expérimental de Visual Studio, sur le menu **Outils** cliquez sur **Options**.

     Dans la vitre gauche, vous devriez voir **Ma catégorie**. (Les catégories d’options sont répertoriées par ordre alphabétique, de sorte qu’il devrait apparaître à mi-chemin de la liste.) Ouvrez **ma catégorie,** puis cliquez sur **My Grid Page**. La grille d’options apparaît dans la bonne vitre. La catégorie de propriété est **Mes options**, et le nom de la propriété est Mon **option Integer**. La description de la propriété, **Mon option d’intégration**, apparaît au bas de la vitre. Changez la valeur de sa valeur initiale de 256 à autre chose. Cliquez **SUR OK**, puis rouvrir Ma page de **grille**. Vous pouvez voir que la nouvelle valeur persiste.

     Votre page d’options est également disponible dans la boîte de recherche de Visual Studio. Dans la boîte de recherche près du haut de l’IDE, **tapez ma catégorie** et vous verrez **Ma catégorie -> My Grid Page** répertorié dans les résultats.

## <a name="create-a-tools-options-custom-page"></a>Créer une page personnalisée Tools Options

 Dans cette section, vous créez une page Options Outils avec une interface utilisateur personnalisée. Vous utilisez cette page pour afficher et modifier la valeur d’une propriété.

1. Ouvrez le fichier *MyToolsOptionsPackage* dans l’éditeur de code.

2. Ajouter l’instruction suivante à l’aide de l’instruction.

    ```csharp
    using System.Windows.Forms;
    ```

3. Ajoutez `OptionPageCustom` un cours, `OptionPageGrid` juste avant la classe. Dérivez la `DialogPage`nouvelle classe de .

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

4. Ajouter un attribut GUID. Ajouter une propriété OptionString :

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

5. Appliquez <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> une seconde à la classe VSPackage. Cet attribut attribue à la classe une catégorie d’options et le nom de page d’options.

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

7. Ajoutez un contrôle **TextBox** au contrôle de l’utilisateur.

     Dans la fenêtre **Propriétés,** sur la barre d’outils, cliquez sur le bouton **Événements,** puis cliquez double sur l’événement **Leave.** Le nouveau gestionnaire d’événements apparaît dans le code *MyUserControl.cs.*

8. Ajoutez un `OptionsPage` champ `Initialize` public, une méthode à la classe de contrôle et mettez à jour le gestionnaire d’événements pour définir la valeur d’option au contenu de la boîte de texte :

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

     Le `optionsPage` domaine fait référence `OptionPageCustom` à l’instance parente. La `Initialize` méthode `OptionString` s’affiche dans la **TextBox**. Le gestionnaire de l’événement écrit la `OptionString` valeur actuelle de la **TextBox** au moment où la mise au point quitte la **TextBox**.

9. Dans le fichier de code de `OptionPageCustom.Window` paquet, `OptionPageCustom` ajouter un remplacement pour la propriété `MyUserControl`à la classe pour créer, initialiser, et retourner une instance de . La classe devrait maintenant ressembler à ceci:

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

11. Dans le cas expérimental, cliquez sur **Options Outils** > **.**

12. Trouver **ma catégorie,** puis **ma page personnalisée**.

13. Modifier la valeur **d’OptionString**. Cliquez **SUR OK**, puis rouvrir Ma page **personnalisée**. Vous pouvez voir que la nouvelle valeur a persisté.

## <a name="access-options"></a>Options d’accès

 Dans cette section, vous obtenez la valeur d’une option à partir de la VSPackage qui héberge la page Options Outils associés. La même technique peut être utilisée pour obtenir la valeur de tout bien public.

1. Dans le fichier de code de paquet, ajoutez une propriété publique appelée **OptionInteger** à la classe **MyToolsOptionsPackage.**

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

     Ce code <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> appelle pour `OptionPageGrid` créer ou récupérer une instance. `OptionPageGrid`d’appels <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> à charger ses options, qui sont des biens publics.

2. Maintenant, ajoutez un modèle d’élément de commande personnalisé nommé **MyToolsOptionsCommand** pour afficher la valeur. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C’Extensibility** > **Extensibility** et **sélectionnez Custom Command**. Dans le champ **nom** au bas de la fenêtre, changer le nom du fichier de commande pour *MyToolsOptionsCommand.cs*.

3. Dans le fichier *MyToolsOptionsCommand,* remplacez le `ShowMessageBox` corps de la méthode de la commande par les éléments suivants :

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Générez le projet et commencez le débogage.

5. Dans le cas expérimental, sur le menu **Tools,** cliquez sur **Invoke MyToolsOptionsCommand**.

     Une boîte de message `OptionInteger`affiche la valeur actuelle de .

## <a name="see-also"></a>Voir aussi

- [Pages d’options et d’options](../extensibility/internals/options-and-options-pages.md)
