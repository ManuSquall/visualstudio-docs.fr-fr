---
title: Création d’un système de projet de base, partie 2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6dfcae8855c2bdb821f61be65de39282db87dfd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336999"
---
# <a name="create-a-basic-project-system-part-2"></a>Créer un système de projet de base, partie 2
La première procédure pas à pas dans cette série, [créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md), montre comment créer un système de projet de base. Cette procédure pas à pas s’appuie sur le système de projet de base en ajoutant un modèle Visual Studio, une page de propriétés et autres fonctionnalités. Vous devez effectuer la première procédure avant de commencer celle-ci.

Cette procédure pas à pas explique comment créer un type de projet qui a l’extension de nom de fichier de projet *.myproj*. Pour terminer la procédure pas à pas, il est inutile de créer votre propre langage, car la procédure pas à pas utilise le système de projet Visual c# existant.

Cette procédure pas à pas explique comment accomplir ces tâches :

- Créer un modèle de Visual Studio.

- Déployer un modèle de Visual Studio.

- Créer un nœud enfant du type projet dans le **nouveau projet** boîte de dialogue.

- Activer la substitution de paramètre dans le modèle Visual Studio.

- Créer une page de propriétés de projet.

> [!NOTE]
> Les étapes décrites dans cette procédure pas à pas sont basées sur un projet c#. Toutefois, à l’exception des caractéristiques telles que les extensions de nom de fichier et le code, vous pouvez utiliser les mêmes étapes pour un projet Visual Basic.

## <a name="create-a-visual-studio-template"></a>Créer un modèle Visual Studio
- [Créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) montre comment créer un modèle de projet de base et l’ajouter au système de projet. Il montre également comment inscrire ce modèle avec Visual Studio à l’aide de la <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut, qui écrit le chemin d’accès complet de le *\\Templates\Projects\SimpleProject\\* dossier dans le système Registre.

À l’aide d’un modèle Visual Studio ( *.vstemplate* fichier) au lieu d’un modèle de projet de base, vous pouvez contrôler la façon dont le modèle apparaît dans le **nouveau projet** boîte de dialogue et comment les paramètres de modèle remplacée. Un *.vstemplate* fichier est un fichier XML qui décrit la façon dont les fichiers sources doivent être inclus lorsqu’un projet est créé en utilisant le modèle de système de projet. Le système de projet lui-même est généré en collectant les *.vstemplate* fichier et les fichiers source dans un *.zip* de fichiers et déployées en copiant le *.zip* vers un emplacement qui est connus pour Visual Studio. Ce processus est expliqué en détail plus loin dans cette procédure pas à pas.

1. Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez la solution SimpleProject que vous avez créé en suivant [créer un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. Dans le *SimpleProjectPackage.cs* de fichier, recherchez l’attribut ProvideProjectFactory. Remplacez-les par le deuxième paramètre (le nom du projet), avec NULL comme valeur et le quatrième paramètre (le chemin d’accès au dossier du modèle de projet) ». \\\NullPath », comme suit.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Ajouter un fichier XML nommé *SimpleProject.vstemplate* à la *\\Templates\Projects\SimpleProject\\* dossier.

4. Remplacez le contenu de *SimpleProject.vstemplate* avec le code suivant.

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

5. Dans le **propriétés** fenêtre, sélectionnez toutes les cinq fichiers dans le *\\Templates\Projects\SimpleProject\\* dossier et appliquez le **Action de génération** pour **ZipProject**.

    ![Dossier de projet simple](../extensibility/media/simpproj2.png "SimpProj2")

    Le \<TemplateData > section détermine l’emplacement et l’apparence du type de projet SimpleProject dans le **nouveau projet** boîte de dialogue, comme suit :

- Le \<nom > le modèle de projet application de SimpleProject noms d’éléments.

- Le \<Description > élément contient la description qui s’affiche dans le **nouveau projet** boîte de dialogue lorsque le modèle de projet est sélectionné.

- Le \<icône > élément spécifie l’icône qui apparaît avec le type de projet SimpleProject.

- Le \<ProjectType > élément désigne le type de projet dans le **nouveau projet** boîte de dialogue. Ce nom remplace le paramètre de nom de projet de l’attribut ProvideProjectFactory.

  > [!NOTE]
  > Le \<ProjectType > élément doit correspondre à la `LanguageVsTemplate` argument de la `ProvideProjectFactory` attribut dans le fichier SimpleProjectPackage.cs.

  Le \<TemplateContent > section décrit ces fichiers sont générés lorsqu’un nouveau projet est créé :

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Les trois fichiers ont `ReplaceParameters` définie sur true, ce qui permet la substitution de paramètres. Le *Program.cs* fichier a `OpenInEditor` définie sur true, ce qui provoque le fichier à ouvrir dans l’éditeur de code lorsqu’un projet est créé.

  Pour plus d’informations sur les éléments dans le schéma de modèle Visual Studio, consultez le [référence de schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Si un projet comporte plusieurs modèles de Visual Studio, chaque modèle est dans un dossier distinct. Chaque fichier dans ce dossier doit posséder le **Action de génération** définie sur **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Ajout d’un fichier .vsct minimale
 Visual Studio doit être exécuté en mode d’installation pour reconnaître un modèle Visual Studio nouvel ou modifié. Le mode d’installation nécessite un *.vsct* fichier qui doit être présent. Par conséquent, vous devez ajouter un minimale *.vsct* fichier au projet.

1. Ajouter un fichier XML nommé *SimpleProject.vsct* au projet SimpleProject.

2. Remplacez le contenu de la *SimpleProject.vsct* fichier par le code suivant.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Définir le **Action de génération** de ce fichier à **VSCTCompile**. Cela peut uniquement dans le *.csproj* de fichiers, pas dans le **propriétés** fenêtre. Assurez-vous que le **Action de génération** de ce fichier est défini sur **aucun** à ce stade.

    1. Cliquez sur le nœud SimpleProject et puis cliquez sur **SimpleProject.csproj modifier**.

    2. Dans le *.csproj* de fichiers, recherchez le *SimpleProject.vsct* élément.

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Modifier l’action de génération pour **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. le fichier projet et le fermer l’éditeur.

    5. Enregistrer le nœud SimpleProject, puis, dans le **l’Explorateur de solutions** cliquez sur **recharger le projet**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Examinez les étapes de build de modèle Visual Studio
 Le système de génération de projet VSPackage s’exécute généralement Visual Studio en mode d’installation lors de la *.vstemplate* fichier est modifié ou le projet qui contient le *.vstemplate* fichier est régénéré. Vous pouvez suivre la procédure en définissant le niveau de détail de MSBuild à la normale ou une version ultérieure.

1. Dans le menu **Outils**, cliquez sur **Options**.

2. Développez le **projets et Solutions** nœud, puis sélectionnez **générer et exécuter**.

3. Définissez **niveau de détail de sortie de génération de projet MSBuild** à **Normal**. Cliquez sur **OK**.

4. Régénérez le projet SimpleProject.

    L’étape de build pour créer le *.zip* fichier projet doit ressembler à l’exemple suivant.

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
Modèles Visual Studio ne contiennent pas les informations de chemin d’accès. Par conséquent, le modèle *.zip* fichier doit être déployé vers un emplacement connu pour Visual Studio. L’emplacement du dossier ProjectTemplates est généralement *< % LocalAppData% > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates*.

Pour déployer votre fabrique de projet, le programme d’installation doit avoir des privilèges d’administrateur. Il déploie des modèles sous le nœud d’installation de Visual Studio : *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Tester un modèle Visual Studio
Tester votre fabrique de projet pour voir si elle crée une hiérarchie de projet en utilisant le modèle Visual Studio.

1. Réinitialiser l’instance expérimentale de Visual Studio SDK.

    Sur [!INCLUDE[win7](../debugger/includes/win7_md.md)]: Sur le **Démarrer** menu, trouver la **outils Microsoft Visual Studio/Microsoft Visual Studio SDK/** dossier, puis sélectionnez **réinitialiser l’instance expérimentale Microsoft Visual Studio**.

    Les versions ultérieures de Windows : Sur le **Démarrer** , tapez **réinitialiser Microsoft Visual Studio \<version > Instance expérimentale**.

2. Une fenêtre d’invite de commandes s’affiche. Lorsque vous voyez les mots **appuyez sur n’importe quelle touche pour continuer**, cliquez sur **entrée**. Une fois que la fenêtre se ferme, ouvrez Visual Studio.

3. Régénérez le projet SimpleProject et démarrer le débogage. L’instance expérimentale s’affiche.

4. Dans l’instance expérimentale, créez un projet de SimpleProject. Dans le **nouveau projet** boîte de dialogue, sélectionnez **SimpleProject**.

5. Vous devez voir une nouvelle instance de SimpleProject.

    ![Nouvelle Instance de projet simple](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Mon projet nouvelle Instance](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Créer un nœud enfant du type de projet
Vous pouvez ajouter un nœud enfant à un nœud de type de projet dans le **nouveau projet** boîte de dialogue. Par exemple, pour le type de projet SimpleProject, vous pouvez avoir des nœuds enfants pour les applications de console, fenêtre applications, applications web et ainsi de suite.

Nœuds enfants sont créés en modifiant le fichier projet et en ajoutant \<OutputSubPath > enfants à la \<ZipProject > éléments. Lorsqu’un modèle est copié au cours de génération ou de déploiement, tous les nœuds enfants devient un sous-dossier du dossier de modèles de projet.

Cette section montre comment créer un nœud enfant de Console pour le type de projet SimpleProject.

1. Renommer le *\\Templates\Projects\SimpleProject\\* dossier  *\\Templates\Projects\ConsoleApp\\* .

2. Dans le **propriétés** fenêtre, sélectionnez toutes les cinq fichiers dans le *\\Templates\Projects\ConsoleApp\\* dossier et vérifiez que le **Action de génération**est défini sur **ZipProject**.

3. Dans le fichier SimpleProject.vstemplate, ajoutez la ligne suivante à la fin de la \<TemplateData > section, juste avant la balise de fermeture.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Cela entraîne le modèle d’Application de Console apparaissent dans le nœud enfant de la Console et dans le nœud parent SimpleProject, ce qui se trouve un niveau au-dessus du nœud enfant.

4. Enregistrer le *SimpleProject.vstemplate* fichier.

5. Dans le *.csproj* , ajoutez \<OutputSubPath > à chacun des éléments ZipProject. Décharger le projet, comme auparavant et modifiez le fichier projet.

6. Recherchez le \<ZipProject > éléments. À chaque \<ZipProject > élément, ajoutez un \<OutputSubPath > élément et lui donner la valeur de Console. Le ZipProject

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

7. Ajoutez ce \<PropertyGroup > dans le fichier de projet :

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Enregistrez le fichier projet et recharger le projet.

## <a name="test-the-project-type-child-node"></a>Le nœud enfant de type projet de test
Tester le fichier de projet modifié pour voir si le **Console** nœud enfant s’affiche dans le **nouveau projet** boîte de dialogue.

1. Exécutez le **réinitialiser l’Instance expérimentale Microsoft Visual Studio** outil.

2. Régénérez le projet SimpleProject et démarrer le débogage. L’instance expérimentale doit apparaître.

3. Dans le **nouveau projet** boîte de dialogue, cliquez sur le **SimpleProject** nœud. Le **Application Console** modèle doit apparaître dans le **modèles** volet.

4. Développez le **SimpleProject** nœud. Le **Console** nœud enfant doit apparaître. Le **SimpleProject Application** modèle continue d’apparaître dans le **modèles** volet.

5. Cliquez sur **Annuler** et arrêter le débogage.

    ![Cumul de projet simple](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Nœud projet simple de la Console](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Substituer des paramètres de modèle de projet
- [Création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) vous a montré comment remplacer le `ProjectNode.AddFileFromTemplate` pour cela un type de base de la substitution de paramètre de modèle. Cette section explique comment utiliser les paramètres de modèle Visual Studio plus sophistiquées.

Lorsque vous créez un projet à l’aide d’un modèle de Visual Studio dans le **nouveau projet** boîte de dialogue modèle de paramètres sont remplacés par des chaînes pour personnaliser le projet. Un paramètre de modèle est un jeton spécial qui commence et se termine par un signe dollar, par exemple, $time$. Les deux paramètres suivants sont particulièrement utiles pour l’activation de personnalisation dans les projets qui reposent sur le modèle :

- $GUID [1-10] $ est remplacé par un nouveau Guid. Vous pouvez spécifier jusqu'à 10 GUID uniques, par exemple, $guid1$.

- $safeprojectname$ est le nom fourni par un utilisateur dans le **nouveau projet** boîte de dialogue, modifié afin de supprimer tous les caractères sécurisés et des espaces.

  Pour obtenir la liste complète des paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Pour substituer des paramètres de modèle de projet

1. Dans le *SimpleProjectNode.cs* de fichiers, supprimez le `AddFileFromTemplate` (méthode).

2. Dans le  *\\Templates\Projects\ConsoleApp\SimpleProject.myproj* de fichiers, recherchez le \<RootNamespace > propriété et remplacez sa valeur $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. Dans le  *\\Templates\Projects\SimpleProject\Program.cs* de fichier, remplacez le contenu du fichier par le code suivant :

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

4. Régénérez le projet SimpleProject et démarrer le débogage. L’instance expérimentale doit apparaître.

5. Créer une nouvelle application de Console de SimpleProject. (Dans le **types de projets** volet, sélectionnez **SimpleProject**. Sous **modèles Visual Studio installés**, sélectionnez **Application Console**.)

6. Dans le projet nouvellement créé, ouvrez *Program.cs*. Il doit se présenter comme suit (les valeurs GUID dans votre fichier diffèrent.) :

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

## <a name="create-a-project-property-page"></a>Créer une page de propriétés de projet
Vous pouvez créer une page de propriétés pour votre type de projet afin que les utilisateurs peuvent afficher et modifier les propriétés dans les projets qui sont basés sur votre modèle. Cette section vous montre comment créer une page de propriétés indépendantes de la configuration. Cette page de propriétés de base utilise une grille de propriétés pour afficher les propriétés publiques que vous exposez dans votre classe de page de propriétés.

Dérivez votre classe de page de propriété de la `SettingsPage` classe de base. La grille des propriétés fournie par le `SettingsPage` classe tient compte des types de données les plus primitifs et sait comment les afficher. En outre, la `SettingsPage` classe sait comment conserver les valeurs de propriété au fichier projet.

La page de propriétés que vous créez dans cette section vous permet de modifier et enregistrer ces propriétés de projet :

- AssemblyName

- OutputType

- RootNamespace.

1. Dans le *SimpleProjectPackage.cs* de fichiers, ajoutez ceci `ProvideObject` attribut le `SimpleProjectPackage` classe :

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Cela inscrit la classe de page de propriété `GeneralPropertyPage` auprès de COM.

2. Dans le *SimpleProjectNode.cs* , ajoutez ces deux méthodes substituées pour la `SimpleProjectNode` classe :

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

    Ces deux méthodes retournent un tableau de la page de propriétés GUID. Le GUID GeneralPropertyPage est le seul élément dans le tableau, donc la **Pages de propriétés** boîte de dialogue affiche qu’une seule page.

3. Ajoutez un fichier de classe nommé *GeneralPropertyPage.cs* au projet SimpleProject.

4. Remplacez le contenu de ce fichier en utilisant le code suivant :

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

    Le `GeneralPropertyPage` classe expose trois propriétés publiques AssemblyName et OutputType RootNamespace. AssemblyName n’ayant aucune méthode set, il est affiché comme une propriété en lecture seule. OutputType est une constante énumérée, afin qu’il apparaisse en tant que liste déroulante.

    Le `SettingsPage` fournit la classe de base `ProjectMgr` pour rendre persistantes les propriétés. Le `BindProperties` méthode utilise `ProjectMgr` pour récupérer les valeurs de propriété persistante et de définir les propriétés correspondantes. Le `ApplyChanges` méthode utilise `ProjectMgr` pour obtenir les valeurs des propriétés et les conserver dans le fichier projet. La propriété set définit de la méthode `IsDirty` comme « true » pour indiquer que les propriétés devaient être rendues persistantes. Persistance se produit lorsque vous enregistrez le projet ou la solution.

5. Régénérez la solution SimpleProject et démarrer le débogage. L’instance expérimentale doit apparaître.

6. Dans l’instance expérimentale, créez une nouvelle Application SimpleProject.

7. Visual Studio appelle votre fabrique de projet pour créer un projet en utilisant le modèle Visual Studio. La nouvelle *Program.cs* fichier est ouvert dans l’éditeur de code.

8. Cliquez sur le nœud de projet dans **l’Explorateur de solutions**, puis cliquez sur **propriétés**. La boîte de dialogue **Pages de propriétés** s’affiche.

    ![Page de propriétés de projet simple](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>La page de propriétés de projet de test
Vous pouvez maintenant tester si vous pouvez modifier et modifier les valeurs de propriété.

1. Dans le **Pages de propriétés MyConsoleApplication** boîte de dialogue, choisissez le **DefaultNamespace** à **MyApplication**.

2. Sélectionnez le **OutputType** propriété, puis sélectionnez **bibliothèque de classes**.

3. Cliquez sur **appliquer**, puis cliquez sur **OK**.

4. Rouvrez le **Pages de propriétés** boîte de dialogue zone et vérifier que vos modifications ont été rendues persistantes.

5. Fermez l’instance expérimentale de Visual Studio.

6. Rouvrez l’instance expérimentale.

7. Rouvrez le **Pages de propriétés** boîte de dialogue zone et vérifier que vos modifications ont été rendues persistantes.

8. Fermez l’instance expérimentale de Visual Studio.
    ![Fermez l’instance expérimentale](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
