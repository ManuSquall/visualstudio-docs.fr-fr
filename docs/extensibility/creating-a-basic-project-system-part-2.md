---
title: Création d’un système de projet de base, Partie 2 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739714"
---
# <a name="create-a-basic-project-system-part-2"></a>Créer un système de projet de base, partie 2
La première procédure pas à pas de cette série, [Créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md), montre comment créer un système de projet de base. Cette procédure pas à pas s’appuie sur le système de projet de base en ajoutant un modèle Visual Studio, une page de propriété et d’autres fonctionnalités. Vous devez terminer la première procédure pas à pas avant de commencer celui-ci.

Ce pas-là enseigne comment créer un type de projet qui a l’extension nom de fichier de projet *.myproj*. Pour compléter la procédure pas à pas, vous n’avez pas à créer votre propre langue parce que la procédure pas à pas emprunte au système de projet Visual CMD existant.

Ce pas-là enseigne comment accomplir ces tâches :

- Créez un modèle Visual Studio.

- Déployez un modèle Visual Studio.

- Créez un nœud d’enfant de type projet dans la boîte de dialogue **du nouveau projet.**

- Activez la substitution des paramètres dans le modèle Visual Studio.

- Créez une page de propriété du projet.

> [!NOTE]
> Les étapes de cette procédure pas à pas sont basées sur un projet C. Toutefois, à l’exception de détails tels que les extensions de noms de fichiers et le code, vous pouvez utiliser les mêmes étapes pour un projet de base visuelle.

## <a name="create-a-visual-studio-template"></a>Créer un modèle Visual Studio
- [Créer un système de projet de base, la partie 1](../extensibility/creating-a-basic-project-system-part-1.md) montre comment créer un modèle de projet de base et l’ajouter au système de projet. Il montre également comment enregistrer ce modèle <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> avec Visual Studio en utilisant l’attribut, qui écrit le chemin complet du dossier * \\Templates-Projects-SimpleProject\\ * dans le registre du système.

En utilisant un modèle Visual Studio (fichier *.vstemplate)* au lieu d’un modèle de projet de base, vous pouvez contrôler comment le modèle apparaît dans la boîte de dialogue **Du nouveau projet** et comment les paramètres du modèle sont remplacés. Un fichier *.vstemplate* est un fichier XML qui décrit comment les fichiers sources doivent être inclus lorsqu’un projet est créé en utilisant le modèle du système de projet. Le système de projet lui-même est construit en recueillant le fichier *.vstemplate* et les fichiers source dans un fichier *.zip,* et déployé en copiant le fichier *.zip* à un endroit qui est connu de Visual Studio. Ce processus est expliqué plus en détail plus tard dans cette procédure pas à pas.

1. Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez la solution SimpleProject que vous avez créée en suivant [Créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. Dans le *fichier SimpleProjectPackage.cs,* trouvez l’attribut ProvideProjectFactory. Remplacer le deuxième paramètre (le nom du projet) par nul, et le quatrième paramètre (le chemin vers le dossier de modèle de projet) par ". \\"NullPath", comme suit.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Ajoutez un fichier XML nommé *SimpleProject.vstemplate* au * \\dossier\\ Templates-Projects-SimpleProject.*

4. Remplacez le contenu de *SimpleProject.vstemplate* par le code suivant.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. Dans la fenêtre **Propriétés,** sélectionnez les cinq fichiers dans le * \\dossier Templates-Projects-SimpleProject\\ * et définissez l’action **Build** à **ZipProject**.

    ![Dossier de projet simple](../extensibility/media/simpproj2.png "SimpProj2")

    La \<section TemplateData> détermine l’emplacement et l’apparence du type de projet SimpleProject dans la boîte de dialogue **du nouveau projet,** comme suit :

- Le \<nom> élément nomme le modèle de projet pour être simpleProject Application.

- L’élément \<description> contient la description qui apparaît dans la boîte de dialogue **du nouveau projet** lorsque le modèle de projet est sélectionné.

- L’élément \<Icon> spécifie l’icône qui apparaît avec le type de projet SimpleProject.

- Le \<ProjectType> élément nomme le type de projet dans la boîte de dialogue **du nouveau projet.** Ce nom remplace le paramètre du nom de projet de l’attribut ProvideProjectFactory.

  > [!NOTE]
  > L’élément \<ProjectType> doit `LanguageVsTemplate` correspondre `ProvideProjectFactory` à l’argument de l’attribut dans le dossier SimpleProjectPackage.cs.

  La \<section TemplateContent> décrit ces fichiers générés lors de la création d’un nouveau projet :

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Les trois `ReplaceParameters` fichiers se sont concrétaux, ce qui permet la substitution des paramètres. Le *fichier Program.cs* s’est `OpenInEditor` avéré vrai, ce qui provoque l’ouverture du fichier dans l’éditeur de code lors de la création d’un projet.

  Pour plus d’informations sur les éléments dans le schéma Visual Studio Template, voir la [référence schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Si un projet a plus d’un modèle Visual Studio, chaque modèle est dans un dossier séparé. Chaque fichier dans ce dossier doit avoir **l’action Build** ensemble à **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Ajout d’un fichier .vsct minimal
 Visual Studio doit être exécuté en mode configuration pour reconnaître un modèle de studio visuel nouveau ou modifié. Le mode d’installation nécessite la présence d’un fichier *.vsct.* Par conséquent, vous devez ajouter un fichier *.vsct* minimal au projet.

1. Ajoutez un fichier XML nommé *SimpleProject.vsct* au projet SimpleProject.

2. Remplacez le contenu du fichier *SimpleProject.vsct* par le code suivant.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Définissez **l’action** de construction de ce fichier à **VSCTCompile**. Vous ne pouvez le faire que dans le fichier *.csproj,* pas dans la fenêtre **Propriétés.** Assurez-vous que **l’action de construction** de ce fichier est définie à **Aucun** à ce stade.

    1. Cliquez à droite sur le nœud SimpleProject, puis cliquez sur **Edit SimpleProject.csproj**.

    2. Dans le fichier *.csproj,* localisez l’élément *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Modifier l’action de construction à **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. le dossier du projet et de fermer l’éditeur.

    5. Enregistrer le nœud SimpleProject, puis dans le **solution Explorer** cliquez sur **Reload Project**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Examiner les étapes de construction du modèle Visual Studio
 Le système de construction du projet VSPackage fonctionne généralement Visual Studio en mode configuration lorsque le fichier *.vstemplate* est modifié ou que le projet qui contient le fichier *.vstemplate* est reconstruit. Vous pouvez suivre en définissant le niveau de verbosité de MSBuild à normal ou supérieur.

1. Dans le menu **Outils** , cliquez sur **Options**.

2. Élargir le nœud **Projets et Solutions,** puis sélectionnez **Build and Run**.

3. Définir **MSBuild projet construire la verbosité de sortie** à la **normale**. Cliquez sur **OK**.

4. Reconstruire le projet SimpleProject.

    L’étape de construction pour créer le fichier de projet *.zip* doit ressembler à l’exemple suivant.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Déployer un modèle Visual Studio
Les modèles Visual Studio ne contiennent pas d’informations sur le chemin. Par conséquent, le fichier *.zip* modèle doit être déployé à un endroit qui est connu de Visual Studio. L’emplacement du dossier ProjectTemplates est généralement *<%LOCALAPPDATA%>-Microsoft-VisualStudio-14.0Exp-ProjectTemplates*.

Pour déployer votre usine de projet, le programme d’installation doit avoir des privilèges d’administrateur. Il déploie des modèles sous le nœud d’installation Visual Studio : *... 'Microsoft Visual Studio 14.0'Common7'IDE’ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testez un modèle Visual Studio
Testez votre usine de projet pour voir si elle crée une hiérarchie de projet en utilisant le modèle Visual Studio.

1. Réinitialisez l’instance expérimentale Visual Studio SDK.

    Sur [!INCLUDE[win7](../debugger/includes/win7_md.md)]: Sur le menu **Démarrer,** trouvez le dossier **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools,** puis **sélectionnez Reset l’instance expérimentale Microsoft Visual Studio**.

    Sur les versions ultérieures de Windows: Sur l’écran **d’accueil,** **tapez Reset la version Microsoft Visual Studio \<> Experimental Instance**.

2. Une fenêtre d’invite de commande apparaît. Lorsque vous voyez les mots **Appuyez sur toute clé pour continuer**, cliquez sur **ENTER**. Après la fermeture de la fenêtre, ouvrez Visual Studio.

3. Reconstruire le projet SimpleProject et commencer à débogage. L’instance expérimentale apparaît.

4. Dans le cas expérimental, créez un projet SimpleProject. Dans la boîte de dialogue **du nouveau projet,** sélectionnez **SimpleProject**.

5. Vous devriez voir une nouvelle instance de SimpleProject.

    ![Simple Projet Nouvelle Instance](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Mon projet Nouvelle Instance](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Créer un nœud d’enfant de type projet
Vous pouvez ajouter un nœud enfant à un nœud de type projet dans la boîte de dialogue **du nouveau projet.** Par exemple, pour le type de projet SimpleProject, vous pouvez avoir des nœuds d’enfant pour des applications de console, des applications de fenêtre, des applications Web, et ainsi de suite.

Les nœuds pour enfants sont \<créés en modifiant le fichier \<du projet et en ajoutant OutputSubPath> enfants aux éléments> ZipProject. Lorsqu’un modèle est copié lors de la construction ou du déploiement, chaque nœud enfant devient un sous-pli du dossier des modèles de projet.

Cette section montre comment créer un nœud d’enfant Console pour le type de projet SimpleProject.

1. Rebaptiser le * \\dossier Templates-Projects-SimpleProject\\ * à * \\Templates-Projects-ConsoleApp\\*.

2. Dans la fenêtre **Propriétés,** sélectionnez les cinq fichiers dans le * \\dossier Templates-Projects-ConsoleApp\\ * et assurez-vous que l’action **de construction** est réglée sur **ZipProject**.

3. Dans le fichier SimpleProject.vstemplate, ajoutez la ligne \<suivante à la fin de la section De> TemplateData, juste avant l’étiquette de clôture.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Cela provoque le modèle d’application console d’apparaître à la fois dans le nœud de l’enfant Console et dans le nœud parent SimpleProject, qui est un niveau au-dessus du nœud enfant.

4. Enregistrer le fichier *SimpleProject.vstemplate.*

5. Dans le fichier *.csproj,* ajoutez \<outputSubPath> à chacun des éléments ZipProject. Déchargez le projet, comme avant, et modifiez le fichier du projet.

6. Localiser \<les éléments zipProject>. Pour \<chaque élément ZipProject>, \<ajoutez un élément de> OutputSubPath et donnez-lui la console de valeur. Le ZipProject

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Ajoutez \<ce groupe de propriété> au dossier du projet :

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Enregistrer le dossier du projet et recharger le projet.

## <a name="test-the-project-type-child-node"></a>Testez le nœud enfant de type projet
Testez le fichier de projet modifié pour voir si le nœud d’enfant **Console** apparaît dans la boîte de dialogue **du nouveau projet.**

1. Exécutez le **Reset l’outil Microsoft Visual Studio Experimental Instance.**

2. Reconstruire le projet SimpleProject et commencer à débogage. L’instance expérimentale devrait apparaître

3. Dans le dialogue du **nouveau projet,** cliquez sur le nœud **SimpleProject.** Le modèle **d’application console** doit apparaître dans la vitre **Templates.**

4. Étendre le nœud **SimpleProject.** Le nœud d’enfant **console** doit apparaître. Le modèle **d’application SimpleProject** continue d’apparaître dans le volet **Templates.**

5. Cliquez **sur Annuler** et arrêter de débogage.

    ![Rollup projet simple](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Simple projet Console Node](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Remplacer les paramètres du modèle de projet
- [Création d’un système de projet de base, la partie 1](../extensibility/creating-a-basic-project-system-part-1.md) a montré comment remplacer la `ProjectNode.AddFileFromTemplate` méthode pour faire un type de base de substitution de paramètres de modèle. Cette section enseigne comment utiliser les paramètres de modèle Visual Studio plus sophistiqués.

Lorsque vous créez un projet en utilisant un modèle Visual Studio dans la boîte de dialogue **New Project,** les paramètres du modèle sont remplacés par des chaînes pour personnaliser le projet. Un paramètre de modèle est un jeton spécial qui commence et se termine par un signe de dollar, par exemple, $time$. Les deux paramètres suivants sont particulièrement utiles pour permettre la personnalisation dans les projets qui sont basés sur le modèle :

- $GUID[1-10]$ est remplacé par un nouveau Guid. Vous pouvez spécifier jusqu’à 10 GUID uniques, par exemple, $guid1$.

- $safeprojectname$ est le nom fourni par un utilisateur dans la boîte de dialogue **New Project,** modifié pour supprimer tous les personnages et espaces dangereux.

  Pour une liste complète des paramètres du modèle, voir paramètres [Template](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Remplacer les paramètres du modèle de projet

1. Dans le *fichier SimpleProjectNode.cs,* `AddFileFromTemplate` supprimez la méthode.

2. Dans le \< * \\fichier Templates-ProjectsMD ConsoleApp-SimpleProject.myproj,* localisez la propriété RootNamespace> et changez sa valeur en $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. Dans le * \\fichier Templates-ProjectsMD SimpleProjectMD Program.cs,* remplacez le contenu du fichier par le code suivant :

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. Reconstruire le projet SimpleProject et commencer à débogage. L’instance expérimentale devrait apparaître.

5. Créez une nouvelle application SimpleProject Console. (Dans le volet **de type Projet,** sélectionnez **SimpleProject**. Sous **Visual Studio modèles installés**, sélectionnez Console **Application**.)

6. Dans le nouveau projet, ouvert *Program.cs*. Il devrait ressembler à quelque chose comme ce qui suit (les valeurs GUID dans votre fichier sera différente.):

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Créer une page de propriété de projet
Vous pouvez créer une page de propriété pour votre type de projet afin que les utilisateurs puissent afficher et modifier les propriétés dans les projets qui sont basés sur votre modèle. Cette section vous montre comment créer une page de propriété indépendante de configuration. Cette page de propriété de base utilise une grille de propriétés pour afficher les propriétés publiques que vous exposez dans votre classe de page de propriété.

Dérivez votre classe `SettingsPage` de page de propriété de la classe de base. La grille de `SettingsPage` propriété fournie par la classe est au courant de la plupart des types de données primitives et sait comment les afficher. En outre, `SettingsPage` la classe sait comment maintenir la valeur des propriétés au dossier du projet.

La page de propriété que vous créez dans cette section vous permet de modifier et d’enregistrer ces propriétés de projet :

- AssemblyName

- OutputType

- RootNamespace.

1. Dans le fichier *SimpleProjectPackage.cs,* ajoutez `ProvideObject` cet `SimpleProjectPackage` attribut à la classe :

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Cela enregistre la classe `GeneralPropertyPage` de page de propriété avec COM.

2. Dans le fichier *SimpleProjectNode.cs,* ajoutez ces deux méthodes `SimpleProjectNode` prépondérer à la classe :

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Ces deux méthodes retournent un tableau de GUIDs de page de propriété. Le GuiD GeneralPropertyPage est le seul élément du tableau, de sorte que la boîte de dialogue **des Pages de propriété** n’affichera qu’une seule page.

3. Ajoutez un fichier de classe nommé *GeneralPropertyPage.cs* au projet SimpleProject.

4. Remplacer le contenu de ce fichier en utilisant le code suivant :

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    La `GeneralPropertyPage` classe expose les trois propriétés publiques AssemblyName, OutputType et RootNamespace. Étant donné que AssemblyName n’a pas de méthode définie, elle est affichée comme une propriété lue uniquement. OutputType est une constante énumérée, de sorte qu’il apparaît comme liste de dropdown.

    La `SettingsPage` classe `ProjectMgr` de base prévoit de persévérer les propriétés. La `BindProperties` méthode `ProjectMgr` utilise pour récupérer les valeurs de propriété persistées et définir les propriétés correspondantes. La `ApplyChanges` méthode `ProjectMgr` utilise pour obtenir les valeurs des propriétés et les persister dans le fichier du projet. La méthode de `IsDirty` l’ensemble de propriété s’établit pour indiquer que les propriétés doivent être persistées. La persistance se produit lorsque vous enregistrez le projet ou la solution.

5. Reconstruire la solution SimpleProject et commencer à débogage. L’instance expérimentale devrait apparaître.

6. Dans le cas expérimental, créez une nouvelle application SimpleProject.

7. Visual Studio appelle votre usine de projet pour créer un projet en utilisant le modèle Visual Studio. Le nouveau *fichier Program.cs* est ouvert dans l’éditeur de code.

8. Cliquez à droite sur le nœud de projet dans **Solution Explorer**, puis cliquez sur **Propriétés**. La boîte de dialogue **Pages de propriétés** s’affiche.

    ![Simple Page de propriété de projet](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testez la page de propriété du projet
Maintenant, vous pouvez tester si vous pouvez modifier et modifier la valeur des propriétés.

1. Dans la boîte de dialogue **MyConsoleApplication Property Pages,** changez le **DefaultNamespace** en **MyApplication**.

2. Sélectionnez la propriété **OutputType,** puis sélectionnez **La bibliothèque de classe**.

3. Cliquez sur **Appliquer**, puis sur **OK**.

4. Réouvrez la boîte de dialogue **des Pages de propriété** et vérifiez que vos modifications ont été persistées.

5. Fermez l’instance expérimentale de Visual Studio.

6. Rouvrez l’instance expérimentale.

7. Réouvrez la boîte de dialogue **des Pages de propriété** et vérifiez que vos modifications ont été persistées.

8. Fermez l’instance expérimentale de Visual Studio.
    ![Fermer l’instance expérimentale](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
