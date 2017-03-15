---
title: "Cr&#233;ation d&#39;un syst&#232;me de projet de base, partie 2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "écriture d'un système de projet"
  - "système de projet"
  - "didacticiel"
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Cr&#233;ation d&#39;un syst&#232;me de projet de base, partie 2
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La première procédure pas à pas de cette série, [Création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md), montre comment créer un système de projet de base. Cette procédure pas à pas s'appuie sur le système de projet de base en ajoutant un modèle Visual Studio, une page de propriétés et autres fonctionnalités. Vous devez effectuer la première procédure avant de commencer celle\-ci.  
  
 Cette procédure pas à pas explique comment créer un type de projet qui a le .myproj d'extension de nom de fichier projet. Pour terminer la procédure pas à pas, il est inutile de créer votre propre langue, car la procédure pas à pas emprunte du système de projet Visual c\# existant.  
  
 Cette procédure pas à pas explique comment effectuer ces tâches :  
  
-   Créer un modèle de Visual Studio.  
  
-   Déployer un modèle Visual Studio.  
  
-   Créer un nœud d'enfant de type de projet dans le **Nouveau projet** boîte de dialogue.  
  
-   Activer la substitution de paramètres dans le modèle Visual Studio.  
  
-   Créer une page de propriétés du projet.  
  
> [!NOTE]
>  Les étapes décrites dans cette procédure pas à pas sont basées sur un projet c\#. Toutefois, à l'exception des caractéristiques telles que les extensions de nom de fichier et le code, vous pouvez utiliser la même procédure que pour un projet Visual Basic.  
  
## Création d'un modèle Visual Studio  
 [Création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) montre comment créer un modèle de projet de base et l'ajouter au système de projet. Il montre également comment inscrire ce modèle dans Visual Studio à l'aide de la <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut, qui écrit le chemin d'accès complet du dossier \\Templates\\Projects\\SimpleProject\\ dans le Registre système.  
  
 En utilisant un modèle de Visual Studio \(fichier .vstemplate\) au lieu d'un modèle de projet de base, vous pouvez contrôler la façon dont le modèle apparaît dans le **Nouveau projet** boîte de dialogue et la façon dont les paramètres de modèle sont remplacés.  Un fichier .vstemplate est un fichier XML qui décrit comment les fichiers source sont inclus lors de la création d'un projet à l'aide du modèle de système de projet. Le système de projet lui\-même est généré en regroupant le fichier .vstemplate et les fichiers source dans un fichier .zip et déployé en copiant le fichier .zip vers un emplacement connu pour Visual Studio. Ce processus est expliqué en détail plus loin dans cette procédure pas à pas.  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez la solution SimpleProject que vous avez créé en suivant [Création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2.  Dans le fichier SimpleProjectPackage.cs, recherchez la l'attribut ProvideProjectFactory. Remplacez le deuxième paramètre \(le nom du projet\) avec la valeur null et le quatrième paramètre \(le chemin d'accès au dossier du modèle de projet\) avec « .\\\\NullPath », comme suit.  
  
    ```  
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null, "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj", ".\\NullPath", LanguageVsTemplate = "SimpleProject")]  
    ```  
  
3.  Ajoutez un fichier XML nommé SimpleProject.vstemplate dans le dossier \\Templates\\Projects\\SimpleProject\\.  
  
4.  Remplacez le contenu de SimpleProject.vstemplate par le code suivant.  
  
    ```xml  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"> <TemplateData> <Name>SimpleProject Application</Name> <Description> A project for creating a SimpleProject application </Description> <Icon>SimpleProject.ico</Icon> <ProjectType>SimpleProject</ProjectType> </TemplateData> <TemplateContent> <Project File="SimpleProject.myproj" ReplaceParameters="true"> <ProjectItem ReplaceParameters="true" OpenInEditor="true"> Program.cs </ProjectItem> <ProjectItem ReplaceParameters="true" OpenInEditor="false"> AssemblyInfo.cs </ProjectItem> </Project> </TemplateContent> </VSTemplate>  
    ```  
  
5.  Dans le **propriétés** fenêtre, sélectionnez toutes les cinq fichiers dans le dossier de \\Templates\\Projects\\SimpleProject\\ ensemble le **Action de génération** à **ZipProject**.  
  
 ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
 La section \< TemplateData \> détermine l'emplacement et l'apparence du type de projet SimpleProject dans les **Nouveau projet** boîte de dialogue, comme suit :  
  
-   L'élément \< Name \> désigne le modèle de projet application de SimpleProject.  
  
-   L'élément \< Description \> contient la description qui s'affiche dans le **Nouveau projet** boîte de dialogue lorsque le modèle de projet est sélectionné.  
  
-   L'élément \< Icon \> Spécifie l'icône qui s'affiche avec le type de projet SimpleProject.  
  
-   L'élément \< ProjectType \> désigne le type de projet dans le **Nouveau projet** boîte de dialogue. Ce nom remplace le paramètre de nom de projet de l'attribut ProvideProjectFactory.  
  
    > [!NOTE]
    >  L'élément \< ProjectType \> doit correspondre à la `LanguageVsTemplate` argument de la `ProvideProjectFactory` attribut dans le fichier SimpleProjectPackage.cs.  
  
 La section \< TemplateContent \> décrit ces fichiers sont générés lorsqu'un nouveau projet est créé :  
  
-   SimpleProject.myproj  
  
-   Program.cs  
  
-   AssemblyInfo.cs  
  
 Les trois fichiers ont `ReplaceParameters` définie sur true, ce qui permet la substitution de paramètres.  Le fichier Program.cs a `OpenInEditor` définie sur true, ce qui provoque le fichier à ouvrir dans l'éditeur de code lorsqu'un projet est créé.  
  
 Pour plus d'informations sur les éléments dans le schéma de modèle Visual Studio, consultez le [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Si un projet possède plusieurs modèles de Visual Studio, chaque modèle est dans un dossier distinct. Chaque fichier dans ce dossier doit posséder le **Action de génération** la valeur **ZipProject**.  
  
## Ajout d'un fichier .vsct minimale  
 Visual Studio doit être exécuté en mode d'installation reconnaisse un modèle Visual Studio nouvel ou modifié. Le mode d'installation requiert un fichier .vsct. Par conséquent, vous devez ajouter un fichier .vsct minimal au projet.  
  
1.  Ajoutez un fichier XML nommé SimpleProject.vsct au projet SimpleProject.  
  
2.  Remplacez le contenu du fichier SimpleProject.vsct par le code suivant.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"> </CommandTable>  
    ```  
  
3.  Définir le **Action de génération** de ce fichier à **VSCTCompile**. Vous pouvez cela uniquement dans le fichier .csproj, pas dans le **propriétés** fenêtre. Assurez\-vous que le **Action de génération** de ce fichier est défini sur **aucun** à ce stade.  
  
    1.  Cliquez sur le nœud SimpleProject, puis cliquez sur **SimpleProject.csproj modifier**.  
  
    2.  Dans le fichier .csproj, recherchez l'élément SimpleProject.vsct.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Modifier l'action de génération pour **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  le fichier projet et fermer l'éditeur.  
  
    5.  Le nœud SimpleProject d'enregistrement, puis, dans le **l'Explorateur de solutions** cliquez sur **Recharger le projet**.  
  
## Examen des étapes de génération de modèle Visual Studio  
 Le système de génération de projet VSPackage exécute généralement Visual Studio en mode d'installation lorsque le fichier .vstemplate est modifié ou le projet qui contient le fichier .vstemplate est régénéré. Vous pouvez suivre le long en définissant le niveau de détail de MSBuild normale ou une version ultérieure.  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Développez le **projets et Solutions** nœud et sélectionnez **Générer et exécuter**.  
  
3.  Définissez **niveau de détail de sortie de génération du projet MSBuild** à **Normal**. Cliquez sur **OK**.  
  
4.  Régénérez le projet SimpleProject.  
  
 L'étape de génération pour créer le fichier .zip du projet doit ressembler à l'exemple suivant.  
  
```  
ZipProjects: 1>  Zipping ProjectTemplates 1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip... 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip". 1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip". 1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip 1>ZipItems: 1>  Zipping ItemTemplates 1>  SimpleProject ->  
```  
  
## Déploiement d'un modèle Visual Studio  
 Modèles Visual Studio ne contiennent pas les informations de chemin d'accès. Par conséquent, le fichier .zip du modèle doit être déployé dans un emplacement connu pour Visual Studio. L'emplacement du dossier ProjectTemplates est généralement **\< % LocalAppData% \> \\Microsoft\\VisualStudio\\14.0Exp\\ProjectTemplates**.  
  
 Pour déployer votre fabrique de projet, le programme d'installation doit avoir des privilèges d'administrateur. Il déploie des modèles sous le nœud d'installation de Visual Studio : **...\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates**.  
  
## Test d'un modèle Visual Studio  
 Tester votre fabrique de projet pour voir si elle crée une hiérarchie de projet en utilisant le modèle Visual Studio.  
  
1.  Réinitialiser l'instance expérimentale de Visual Studio SDK.  
  
     Sur [!INCLUDE[win7](../debugger/includes/win7_md.md)]: dans le menu Démarrer, recherchez le **Outils Microsoft Visual Studio ou de Microsoft Visual Studio SDK\/** dossier, puis sélectionnez **Réinitialiser l'instance expérimentale Microsoft Visual Studio**.  
  
     Sur les versions ultérieures de Windows : dans le menu Démarrer, tapez **Réinitialiser Microsoft Visual Studio \< version \> Instance expérimentale**.  
  
2.  Une fenêtre d'invite de commandes s'affiche. Lorsque vous voyez les mots `Press any key to continue`, appuyez sur ENTRÉE. Après la fermeture de la fenêtre, ouvrez Visual Studio.  
  
3.  Régénérez le projet SimpleProject et démarrer le débogage. L'instance expérimentale s'affiche.  
  
4.  Dans l'instance expérimentale, créez un projet de SimpleProject. Dans le **Nouveau projet** boîte de dialogue, sélectionnez **SimpleProject**.  
  
5.  Vous devez voir une nouvelle instance de SimpleProject.  
  
 ![](../extensibility/media/simpproj2_newproj.png "SimpProj2\_NewProj")  
  
 ![](../extensibility/media/simpproj2_myproj.png "SimpProj2\_MyProj")  
  
## Création d'un nœud enfant du Type de projet  
 Vous pouvez ajouter un nœud enfant à un nœud de type de projet dans le **Nouveau projet** boîte de dialogue.  Par exemple, pour le type de projet SimpleProject, vous pourriez avoir des nœuds enfants pour les applications de console, applications de fenêtre, les applications web et ainsi de suite.  
  
 Nœuds enfants sont créés en modifiant le fichier de projet et en ajoutant des enfants de \< OutputSubPath \> pour les éléments \< ZipProject \>. Lorsque vous copiez un modèle pendant la génération ou de déploiement, tous les nœuds enfants devient un sous\-dossier du dossier de modèles de projet.  
  
 Cette section montre comment créer un nœud enfant de la Console pour le type de projet SimpleProject.  
  
1.  Renommez le dossier \\Templates\\Projects\\SimpleProject\\ \\Templates\\Projects\\ConsoleApp\\.  
  
2.  Dans le **propriétés** fenêtre, sélectionnez les cinq fichiers dans le dossier \\Templates\\Projects\\ConsoleApp\\ et assurez\-vous que le **Action de génération** a **ZipProject**.  
  
3.  Dans le fichier SimpleProject.vstemplate, ajoutez la ligne suivante à la fin de la section \< TemplateData \>, juste avant la balise de fermeture.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Cela provoque le modèle Application Console s'affichent dans le nœud enfant de la Console et dans le nœud parent SimpleProject, qui se trouve un niveau au\-dessus du nœud enfant.  
  
4.  Enregistrez le fichier SimpleProject.vstemplate.  
  
5.  Dans le fichier .csproj, ajoutez \< OutputSubPath \> pour chacun des éléments ZipProject. Décharger le projet, comme précédemment et modifier le fichier projet.  
  
6.  Recherchez les éléments \< ZipProject \>. À chaque élément \< ZipProject \>, ajoutez un élément \< OutputSubPath \> et donnez\-lui la valeur Console. Le ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate"> <OutputSubPath>Console</OutputSubPath> </ZipProject> <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico"> <OutputSubPath>Console</OutputSubPath> </ZipProject>  
    ```  
  
7.  Ajoutez cette \< PropertyGroup \> dans le fichier projet :  
  
    ```  
    <PropertyGroup> <VsTemplateLanguage>SimpleProject</VsTemplateLanguage> </PropertyGroup>  
    ```  
  
8.  Enregistrez le fichier projet et recharger le projet.  
  
## Le nœud enfant de Type projet de test  
 Tester le fichier projet modifié pour voir si le **Console** nœud enfant s'affiche dans le **Nouveau projet** boîte de dialogue.  
  
1.  Exécutez le **Réinitialiser l'Instance expérimentale Microsoft Visual Studio** outil.  
  
2.  Régénérez le projet SimpleProject et démarrer le débogage. L'instance expérimentale doit apparaître.  
  
3.  Dans le **Nouveau projet** boîte de dialogue, cliquez sur le **SimpleProject** nœud. Le **Application Console** modèle doit apparaître dans le **modèles** volet.  
  
4.  Développez le **SimpleProject** nœud. Le **Console** nœud enfant doit apparaître. Le **SimpleProject Application** modèle continue d'apparaître dans les **modèles** volet.  
  
5.  . Cliquez sur **Annuler** et arrêter le débogage  
  
 ![](../extensibility/media/simpproj2_rollup.png "SimpProj2\_Rollup")  
  
 ![](../extensibility/media/simpproj2_subfolder.png "SimpProj2\_Subfolder")  
  
## En remplaçant les paramètres de modèle de projet  
 [Création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) vous a montré comment remplacer le `ProjectNode.AddFileFromTemplate` pour cela un type de base de la substitution de paramètres de modèle. Cette section explique comment utiliser les paramètres de modèle Visual Studio plus sophistiquées.  
  
 Lorsque vous créez un projet à l'aide d'un modèle Visual Studio dans le **Nouveau projet** boîte de dialogue modèle de paramètres sont remplacées par des chaînes pour personnaliser le projet. Un paramètre de modèle est un jeton spécial qui commence et se termine par un signe dollar, par exemple, $time$. Les deux paramètres suivants sont particulièrement utiles pour l'activation de la personnalisation dans les projets qui sont basés sur le modèle :  
  
-   $GUID \[1\-10\] $ est remplacé par un nouveau Guid. Vous pouvez spécifier jusqu'à 10 GUID uniques, par exemple, $guid1$.  
  
-   $safeprojectname$ correspond à celui fourni par un utilisateur dans le **Nouveau projet** boîte de dialogue, modifié afin de supprimer tous les espaces et les caractères non sécurisés.  
  
 Pour obtenir une liste complète des paramètres de modèle, consultez la page [Paramètres de modèle](../ide/template-parameters.md).  Si vous souhaitez créer votre propre paramètre de modèle personnalisé, consultez [NIB : Comment : passer des paramètres personnalisés aux modèles](http://msdn.microsoft.com/fr-fr/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### Pour remplacer les paramètres de modèle de projet  
  
1.  Dans le fichier SimpleProjectNode.cs, supprimez le `AddFileFromTemplate` \(méthode\).  
  
2.  Dans le fichier \\Templates\\Projects\\ConsoleApp\\SimpleProject.myproj, recherchez la propriété \< RootNamespace \> et modifiez sa valeur $safeprojectname $.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  Dans le fichier \\Templates\\Projects\\SimpleProject\\Program.cs, remplacez le contenu du fichier par le code suivant :  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace $safeprojectname$ { [Guid("$guid1$")] public class $safeprojectname$ { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
4.  Régénérez le projet SimpleProject et démarrer le débogage. L'instance expérimentale doit apparaître.  
  
5.  Créez une nouvelle application Console de SimpleProject. \(Dans le **types de projets** volet, sélectionnez **SimpleProject**. Sous **modèles Visual Studio installés**, sélectionnez **Application Console**.\)  
  
6.  Dans le projet nouvellement créé, ouvrez le fichier Program.cs. Il doit se présenter comme suit \(les valeurs GUID dans votre fichier diffèrent.\) :  
  
    ```  
    using System; using System.Collections.Generic; using System.Text; using System.Runtime.InteropServices;    // Guid namespace Console_Application1 { [Guid("00000000-0000-0000-00000000-00000000)"] public class Console_Application1 { static void Main(string[] args) { Console.WriteLine("Hello VSX!!!"); Console.ReadKey(); } } }  
    ```  
  
## Création d'une Page de propriétés de projet  
 Vous pouvez créer une page de propriétés pour votre type de projet afin que les utilisateurs peuvent afficher et modifier les propriétés dans les projets qui sont basés sur votre modèle. Cette section vous montre comment créer une page de propriétés de configuration indépendants. Cette page de propriétés de base utilise une grille de propriétés pour afficher les propriétés publiques que vous exposez dans votre classe de page de propriétés.  
  
 Dérivez votre classe de page de propriété de la `SettingsPage` classe de base. La grille des propriétés fournie par la `SettingsPage` classe tient compte des types de données primitifs plus et sait comment les afficher.  En outre, la `SettingsPage` classe sait comment rendre persistantes les valeurs de propriété dans le fichier projet.  
  
 La page de propriétés que vous créez dans cette section vous permet de modifier et enregistrer ces propriétés de projet :  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1.  Dans le fichier SimpleProjectPackage.cs, ajoutez `ProvideObject` attribut la `SimpleProjectPackage` classe :  
  
    ```  
    [ProvideObject(typeof(GeneralPropertyPage))] public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
     Ce code inscrit la classe de page de propriétés `GeneralPropertyPage` avec COM.  
  
2.  Dans le fichier SimpleProjectNode.cs, ajoutez ces deux méthodes substituées à la `SimpleProjectNode` classe :  
  
    ```  
    protected override Guid[] GetConfigurationIndependentPropertyPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; } protected override Guid[] GetPriorityProjectDesignerPages() { Guid[] result = new Guid[1]; result[0] = typeof(GeneralPropertyPage).GUID; return result; }  
    ```  
  
     Ces méthodes renvoient un tableau de la page de propriétés GUID.  Le GUID GeneralPropertyPage est le seul élément du tableau, donc la **Pages de propriétés** boîte de dialogue affichera une seule page.  
  
3.  Ajoutez un fichier de classe nommé GeneralPropertyPage.cs au projet SimpleProject.  
  
4.  Remplacez le contenu de ce fichier en utilisant le code suivant :  
  
    ```  
    using System; using System.Runtime.InteropServices; using Microsoft.VisualStudio; using Microsoft.VisualStudio.Project; using System.ComponentModel; namespace SimpleProject { [ComVisible(true)] [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")] public class GeneralPropertyPage : SettingsPage { private string assemblyName; private OutputType outputType; private string defaultNamespace; public GeneralPropertyPage() { this.Name = "General"; } [Category("AssemblyName")] [DisplayName("AssemblyName")] [Description("The output file holding assembly metadata.")] public string AssemblyName { get { return this.assemblyName; } } [Category("Application")] [DisplayName("OutputType")] [Description("The type of application to build.")] public OutputType OutputType { get { return this.outputType; } set { this.outputType = value; this.IsDirty = true; } } [Category("Application")] [DisplayName("DefaultNamespace")] [Description("Specifies the default namespace for added items.")] public string DefaultNamespace { get { return this.defaultNamespace; } set { this.defaultNamespace = value; this.IsDirty = true; } } protected override void BindProperties() { this.assemblyName = this.ProjectMgr.GetProjectProperty( "AssemblyName", true); this.defaultNamespace = this.ProjectMgr.GetProjectProperty( "RootNamespace", false); string outputType = this.ProjectMgr.GetProjectProperty( "OutputType", false); this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType); } protected override int ApplyChanges() { this.ProjectMgr.SetProjectProperty( "AssemblyName", this.assemblyName); this.ProjectMgr.SetProjectProperty( "OutputType", this.outputType.ToString()); this.ProjectMgr.SetProjectProperty( "RootNamespace", this.defaultNamespace); this.IsDirty = false; return VSConstants.S_OK; } } }  
    ```  
  
     La `GeneralPropertyPage` classe expose trois propriétés publiques AssemblyName et OutputType RootNamespace. AssemblyName n'ayant aucune méthode set, il est affiché comme une propriété en lecture seule. OutputType est une constante énumérée, afin qu'il apparaisse en tant que liste déroulante.  
  
     Le `SettingsPage` fournit la classe de base `ProjectMgr` pour conserver les propriétés. Le `BindProperties` utilise `ProjectMgr` pour récupérer les valeurs de propriété persistante et définir les propriétés correspondantes.  Le `ApplyChanges` utilise `ProjectMgr` pour obtenir les valeurs des propriétés et de les rendre persistants dans le fichier projet. La propriété méthode définit la valeur `IsDirty` sur true pour indiquer que les propriétés devaient être persistante.  La persistance survient lorsque vous enregistrez le projet ou la solution.  
  
5.  Régénérez la solution SimpleProject et démarrer le débogage. L'instance expérimentale doit apparaître.  
  
6.  Dans l'instance expérimentale, créez une nouvelle Application SimpleProject.  
  
7.  Visual Studio appelle votre fabrique de projet pour créer un projet en utilisant le modèle Visual Studio. Le nouveau fichier Program.cs est ouvert dans l'éditeur de code.  
  
8.  Cliquez sur le nœud de projet dans **l'Explorateur de solutions**, puis cliquez sur **propriétés**. Le **Pages de propriétés** boîte de dialogue s'affiche.  
  
 ![](../extensibility/media/simpproj2_proppage.png "SimpProj2\_PropPage")  
  
## La page de propriétés du projet de test  
 Vous pouvez maintenant tester si vous pouvez modifier et valeurs de propriété.  
  
1.  Dans le **Pages de propriétés MyConsoleApplication** boîte de dialogue, choisissez le **DefaultNamespace** à **MyApplication**.  
  
2.  Sélectionnez le **OutputType** propriété, puis sélectionnez **bibliothèque de classes**.  
  
3.  Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
4.  Rouvrez le **Pages de propriétés** boîte de dialogue zone et vérifiez que vos modifications ont été rendues persistantes.  
  
5.  Fermez l'instance expérimentale de Visual Studio.  
  
6.  Rouvrez l'instance expérimentale.  
  
7.  Rouvrez le **Pages de propriétés** boîte de dialogue zone et vérifiez que vos modifications ont été rendues persistantes.  
  
8.  Fermez l'instance expérimentale de Visual Studio.  
  
 ![](../extensibility/media/simpproj2_proppage2.png "SimpProj2\_PropPage2")