---
title: Création d’un système de projet de base, partie 2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d44e99b584ec347abd407753f965170658969b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685410"
---
# <a name="creating-a-basic-project-system-part-2"></a>Création d’un système de projet de base, partie 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La première procédure pas à pas de cette série, [création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md), montre comment créer un système de projet de base. Cette procédure pas à pas s’appuie sur le système de projet de base en ajoutant un modèle Visual Studio, une page de propriétés et d’autres fonctionnalités. Vous devez effectuer la première procédure pas à pas avant de démarrer celle-ci.  
  
 Cette procédure pas à pas explique comment créer un type de projet avec l’extension de nom de fichier projet. MyProj. Pour effectuer la procédure pas à pas, vous n’avez pas à créer votre propre langue, car la procédure pas à pas emprunte le système de projet Visual C# existant.  
  
 Cette procédure pas à pas explique comment accomplir ces tâches :  
  
- Créez un modèle Visual Studio.  
  
- Déployez un modèle Visual Studio.  
  
- Créez un nœud enfant de type de projet dans la boîte de dialogue **nouveau projet** .  
  
- Activez la substitution de paramètre dans le modèle Visual Studio.  
  
- Créer une page de propriétés de projet.  
  
> [!NOTE]
> Les étapes de cette procédure pas à pas sont basées sur un projet C#. Toutefois, à l’exception des détails, tels que les extensions de nom de fichier et le code, vous pouvez utiliser les mêmes étapes pour un projet de Visual Basic.  
  
## <a name="creating-a-visual-studio-template"></a>Création d’un modèle Visual Studio  
 La [création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md) montre comment créer un modèle de projet de base et l’ajouter au système de projet. Il montre également comment inscrire ce modèle auprès de Visual Studio à l’aide de l' <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut, qui écrit le chemin d’accès complet du dossier \Templates\Projects\SimpleProject\ dans le registre système.  
  
 À l’aide d’un modèle Visual Studio (fichier. vstemplate) au lieu d’un modèle de projet de base, vous pouvez contrôler l’apparence du modèle dans la boîte de dialogue **nouveau projet** et le mode de substitution des paramètres de modèle.  Un fichier. vstemplate est un fichier XML qui décrit comment les fichiers sources doivent être inclus lors de la création d’un projet à l’aide du modèle de système de projet. Le système de projet lui-même est généré en recueillant le fichier. vstemplate et les fichiers sources dans un fichier. zip, puis déployé en copiant le fichier. zip dans un emplacement connu de Visual Studio. Ce processus est expliqué plus en détail plus loin dans cette procédure pas à pas.  
  
1. Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ouvrez la solution SimpleProject que vous avez créée en suivant la [section création d’un système de projet de base, partie 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2. Dans le fichier SimpleProjectPackage.cs, recherchez l’attribut ProvideProjectFactory. Remplacez le deuxième paramètre (nom du projet) par null et le quatrième paramètre (chemin d’accès au dossier de modèles de projet) par «. \\ \NullPath», comme suit.  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. Ajoutez un fichier XML nommé SimpleProject. vstemplate au dossier \Templates\Projects\SimpleProject\.  
  
4. Remplacez le contenu de SimpleProject. vstemplate par le code suivant.  
  
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
  
5. Dans la fenêtre **Propriétés** , sélectionnez les cinq fichiers dans le dossier \Templates\Projects\SimpleProject\ et définissez l' **action de génération** sur **ZipProject**.  
  
   ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
   La \<TemplateData> section détermine l’emplacement et l’apparence du type de projet SimpleProject dans la boîte de dialogue **nouveau projet** , comme suit :  
  
- L' \<Name> élément nomme le modèle de projet en application SimpleProject.  
  
- L' \<Description> élément contient la description qui apparaît dans la boîte de dialogue **nouveau projet** lorsque le modèle de projet est sélectionné.  
  
- L' \<Icon> élément spécifie l’icône qui s’affiche avec le type de projet SimpleProject.  
  
- L' \<ProjectType> élément nomme le type de projet dans la boîte de dialogue **nouveau projet** . Ce nom remplace le paramètre de nom de projet de l’attribut ProvideProjectFactory.  
  
  > [!NOTE]
  > L' \<ProjectType> élément doit correspondre à l' `LanguageVsTemplate` argument de l' `ProvideProjectFactory` attribut dans le fichier SimpleProjectPackage.cs.  
  
  La \<TemplateContent> section décrit les fichiers générés lors de la création d’un nouveau projet :  
  
- SimpleProject. MyProj  
  
- Program.cs  
  
- AssemblyInfo.cs  
  
  Les trois fichiers ont `ReplaceParameters` la valeur true, ce qui permet la substitution de paramètres.  Le fichier Program.cs a la `OpenInEditor` valeur true, ce qui entraîne l’ouverture du fichier dans l’éditeur de code lors de la création d’un projet.  
  
  Pour plus d’informations sur les éléments dans le schéma de modèle Visual Studio, consultez la [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
> Si un projet possède plusieurs modèles Visual Studio, tous les modèles se trouvent dans un dossier distinct. L' **action de génération** doit être définie sur **ZipProject**pour chaque fichier de ce dossier.  
  
## <a name="adding-a-minimal-vsct-file"></a>Ajout d’un fichier. vsct minimal  
 Visual Studio doit être exécuté en mode d’installation pour reconnaître un modèle Visual Studio nouveau ou modifié. Le mode d’installation nécessite la présence d’un fichier. vsct. Par conséquent, vous devez ajouter un fichier. vsct minimal au projet.  
  
1. Ajoutez un fichier XML nommé SimpleProject. vsct au projet SimpleProject.  
  
2. Remplacez le contenu du fichier SimpleProject. vsct par le code suivant.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3. Définissez l' **action de génération** de ce fichier sur **VSCTCompile**. Vous ne pouvez le faire que dans le fichier. csproj, et non dans la fenêtre **Propriétés** . Vérifiez que l' **action de génération** de ce fichier est définie sur **aucune** à ce stade.  
  
    1. Cliquez avec le bouton droit sur le nœud SimpleProject, puis cliquez sur **modifier SimpleProject. csproj**.  
  
    2. Dans le fichier. csproj, localisez l’élément SimpleProject. vsct.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3. Modifiez l’action de génération en **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4. le fichier projet et fermez l’éditeur.  
  
    5. Enregistrez le nœud SimpleProject, puis dans le **Explorateur de solutions** cliquez sur **recharger le projet**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Examen des étapes de génération de modèle Visual Studio  
 Le système de génération de projet VSPackage exécute généralement Visual Studio en mode d’installation lorsque le fichier. vstemplate est modifié ou que le projet qui contient le fichier. vstemplate est régénéré. Vous pouvez suivre la procédure en affectant au niveau de détail de MSBuild la valeur normal ou supérieur.  
  
1. Dans le menu **Outils** , cliquez sur **Options**.  
  
2. Développez le nœud **projets et solutions** , puis sélectionnez **générer et exécuter**.  
  
3. Définissez le niveau de détail de la **sortie de génération du projet MSBuild** sur **normal**. Cliquez sur **OK**.  
  
4. Régénérez le projet SimpleProject.  
  
   L’étape de génération pour créer le fichier projet. zip doit ressembler à l’exemple suivant.  
  
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
  
## <a name="deploying-a-visual-studio-template"></a>Déploiement d’un modèle Visual Studio  
 Les modèles Visual Studio ne contiennent pas d’informations de chemin d’accès. Par conséquent, le fichier. zip du modèle doit être déployé dans un emplacement connu de Visual Studio. L’emplacement du dossier ProjectTemplates est généralement ** \<%LOCALAPPDATA%> \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Pour déployer votre fabrique de projet, le programme d’installation doit disposer de privilèges d’administrateur. Il déploie des modèles sous le nœud d’installation de Visual Studio : **. ..\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates**.  
  
## <a name="testing-a-visual-studio-template"></a>Test d’un modèle Visual Studio  
 Testez votre fabrique de projet pour voir si elle crée une hiérarchie de projet à l’aide du modèle Visual Studio.  
  
1. Réinitialisez l’instance expérimentale du kit de développement logiciel (SDK) Visual Studio.  
  
    Sur [!INCLUDE[win7](../includes/win7-md.md)] : dans le menu Démarrer, recherchez le dossier **Microsoft Visual Studio/Kit de développement logiciel (SDK) Microsoft Visual Studio/Tools** , puis sélectionnez **Réinitialiser l’instance expérimentale de Microsoft Visual Studio**.  
  
    Sur les versions ultérieures de Windows : dans l’écran Démarrer, tapez **Réinitialiser l' \<version> Instance expérimentale Microsoft Visual Studio**.  
  
2. Une fenêtre d’invite de commandes s’affiche. Lorsque vous voyez les mots `Press any key to continue` , cliquez sur entrée. Une fois la fenêtre fermée, ouvrez Visual Studio.  
  
3. Régénérez le projet SimpleProject et démarrez le débogage. L’instance expérimentale s’affiche.  
  
4. Dans l’instance expérimentale, créez un projet SimpleProject. Dans la boîte de dialogue **nouveau projet** , sélectionnez **SimpleProject**.  
  
5. Une nouvelle instance de SimpleProject doit s’afficher.  
  
   ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
   ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Création d’un nœud enfant de type de projet  
 Vous pouvez ajouter un nœud enfant à un nœud de type de projet dans la boîte de dialogue **nouveau projet** .  Par exemple, pour le type de projet SimpleProject, vous pouvez avoir des nœuds enfants pour les applications console, les applications Windows, les applications Web, etc.  
  
 Les nœuds enfants sont créés en modifiant le fichier projet et \<OutputSubPath> en ajoutant des enfants aux \<ZipProject> éléments. Lorsqu’un modèle est copié pendant la génération ou le déploiement, chaque nœud enfant devient un sous-dossier du dossier modèles de projet.  
  
 Cette section montre comment créer un nœud enfant de la console pour le type de projet SimpleProject.  
  
1. Renommez le dossier \Templates\Projects\SimpleProject\ en \Templates\Projects\ConsoleApp \\ .  
  
2. Dans la fenêtre **Propriétés** , sélectionnez les cinq fichiers dans le dossier \Templates\Projects\ConsoleApp\ et assurez-vous que l' **action de génération** est définie sur **ZipProject**.  
  
3. Dans le fichier SimpleProject. vstemplate, ajoutez la ligne suivante à la fin de la \<TemplateData> section, juste avant la balise de fermeture.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Le modèle d’application console apparaît alors à la fois dans le nœud enfant de la console et dans le nœud parent SimpleProject, qui se trouve un niveau au-dessus du nœud enfant.  
  
4. Enregistrez le fichier SimpleProject. vstemplate.  
  
5. Dans le fichier. csproj, ajoutez \<OutputSubPath> à chacun des éléments ZipProject. Déchargez le projet, comme avant, puis modifiez le fichier projet.  
  
6. Recherchez les \<ZipProject> éléments. Pour chaque \<ZipProject> élément, ajoutez un \<OutputSubPath> élément et attribuez-lui la console de valeurs. ZipProject  
  
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
  
7. Ajoutez- \<PropertyGroup> le au fichier projet :  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8. Enregistrez le fichier projet et rechargez le projet.  
  
## <a name="testing-the-project-type-child-node"></a>Test du type de projet nœud enfant  
 Testez le fichier projet modifié pour voir si le nœud enfant de la **console** apparaît dans la boîte de dialogue **nouveau projet** .  
  
1. Exécutez l’outil de **réinitialisation de l’instance expérimentale de Microsoft Visual Studio** .  
  
2. Régénérez le projet SimpleProject et démarrez le débogage. L’instance expérimentale doit apparaître.  
  
3. Dans la boîte de dialogue **nouveau projet** , cliquez sur le nœud **SimpleProject** . Le modèle **application console** doit apparaître dans le volet **modèles** .  
  
4. Développez le nœud **SimpleProject** . Le nœud enfant de la **console** doit apparaître. Le modèle d' **application SimpleProject** continue à s’afficher dans le volet **modèles** .  
  
5. . Cliquer sur **Annuler** et arrêter le débogage  
  
   ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
   ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Substitution des paramètres du modèle de projet  
 La [création d’un système de projet de base, partie 1 a](../extensibility/creating-a-basic-project-system-part-1.md) montré comment remplacer la `ProjectNode.AddFileFromTemplate` méthode pour effectuer un type de substitution de paramètre de modèle de base. Cette section explique comment utiliser les paramètres de modèle Visual Studio plus sophistiqués.  
  
 Lorsque vous créez un projet à l’aide d’un modèle Visual Studio dans la boîte de dialogue **nouveau projet** , les paramètres de modèle sont remplacés par des chaînes pour personnaliser le projet. Un paramètre de modèle est un jeton spécial qui commence et se termine par un signe dollar, par exemple, $time $. Les deux paramètres suivants sont particulièrement utiles pour activer la personnalisation dans des projets basés sur le modèle :  
  
- $GUID [1-10] $ est remplacé par un nouveau GUID. Vous pouvez spécifier jusqu’à 10 GUID uniques, par exemple $guid $1.  
  
- $safeprojectname $ est le nom fourni par un utilisateur dans la boîte de dialogue **nouveau projet** , modifié pour supprimer tous les caractères non sécurisés et les espaces.  
  
  Pour obtenir une liste exhaustive des paramètres de modèle, consultez [Paramètres de modèle](../ide/template-parameters.md).  Si vous souhaitez créer votre propre paramètre de modèle personnalisé, consultez [plume : Comment : passer des paramètres personnalisés à des modèles](https://msdn.microsoft.com/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### <a name="to-substitute-project-template-parameters"></a>Pour remplacer les paramètres de modèle de projet  
  
1. Dans le fichier SimpleProjectNode.cs, supprimez la `AddFileFromTemplate` méthode.  
  
2. Dans le fichier \Templates\Projects\ConsoleApp\SimpleProject.myproj, recherchez la \<RootNamespace> propriété et remplacez sa valeur par $safeprojectname $.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3. Dans le fichier \Templates\Projects\SimpleProject\Program.cs, remplacez le contenu du fichier par le code suivant :  
  
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
  
4. Régénérez le projet SimpleProject et démarrez le débogage. L’instance expérimentale doit apparaître.  
  
5. Créez une application console SimpleProject. (Dans le volet **types de projets** , sélectionnez **SimpleProject**. Sous **modèles Visual Studio installés**, sélectionnez **application console**.)  
  
6. Dans le projet qui vient d’être créé, ouvrez Program.cs. Elle doit ressembler à ce qui suit (les valeurs GUID dans votre fichier seront différentes.) :  
  
    ```  
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
  
## <a name="creating-a-project-property-page"></a>Création d’une page de propriétés de projet  
 Vous pouvez créer une page de propriétés pour votre type de projet afin que les utilisateurs puissent afficher et modifier les propriétés dans les projets basés sur votre modèle. Cette section vous montre comment créer une page de propriétés indépendante de la configuration. Cette page de propriétés de base utilise une grille de propriétés pour afficher les propriétés publiques que vous exposez dans votre classe de page de propriétés.  
  
 Dérivez votre classe de page de propriétés de la `SettingsPage` classe de base. La grille de propriétés fournie par la `SettingsPage` classe est consciente de la plupart des types de données primitifs et sait comment les afficher.  En outre, la `SettingsPage` classe sait comment conserver les valeurs de propriété dans le fichier projet.  
  
 La page de propriétés que vous créez dans cette section vous permet de modifier et d’enregistrer les propriétés de ce projet :  
  
- AssemblyName  
  
- OutputType  
  
- RootNamespace.  
  
1. Dans le fichier SimpleProjectPackage.cs, ajoutez cet `ProvideObject` attribut à la `SimpleProjectPackage` classe :  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    Cela enregistre la classe `GeneralPropertyPage` de page de propriétés avec com.  
  
2. Dans le fichier SimpleProjectNode.cs, ajoutez ces deux méthodes substituées à la `SimpleProjectNode` classe :  
  
   ```  
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
  
    Ces deux méthodes retournent un tableau de GUID de page de propriétés.  Le GUID GeneralPropertyPage est le seul élément du tableau. la boîte de dialogue **pages de propriétés** n’affichera donc qu’une seule page.  
  
3. Ajoutez un fichier de classe nommé GeneralPropertyPage.cs au projet SimpleProject.  
  
4. Remplacez le contenu de ce fichier à l’aide du code suivant :  
  
   ```  
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
               this.assemblyName = this.ProjectMgr.GetProjectProperty(  
   "AssemblyName", true);  
               this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
   "RootNamespace", false);  
  
               string outputType = this.ProjectMgr.GetProjectProperty(  
   "OutputType", false);  
               this.outputType =   
   (OutputType)Enum.Parse(typeof(OutputType), outputType);  
           }  
  
           protected override int ApplyChanges()  
           {  
               this.ProjectMgr.SetProjectProperty(  
   "AssemblyName", this.assemblyName);  
               this.ProjectMgr.SetProjectProperty(  
   "OutputType", this.outputType.ToString());  
               this.ProjectMgr.SetProjectProperty(  
   "RootNamespace", this.defaultNamespace);  
               this.IsDirty = false;  
  
               return VSConstants.S_OK;  
           }  
       }  
   }  
   ```  
  
    La `GeneralPropertyPage` classe expose les trois propriétés publiques AssemblyName, OutputType et RootNamespace. Étant donné que AssemblyName n’a pas de méthode Set, il est affiché sous la forme d’une propriété en lecture seule. OutputType est une constante énumérée, donc elle apparaît sous forme de liste déroulante.  
  
    La `SettingsPage` classe de base fournit `ProjectMgr` pour rendre les propriétés persistantes. La `BindProperties` méthode utilise `ProjectMgr` pour récupérer les valeurs de propriétés persistantes et pour définir les propriétés correspondantes.  La `ApplyChanges` méthode utilise `ProjectMgr` pour récupérer les valeurs des propriétés et les rendre persistantes dans le fichier projet. La méthode Property Set affecte `IsDirty` à la valeur true pour indiquer que les propriétés doivent être persistantes.  La persistance se produit lorsque vous enregistrez le projet ou la solution.  
  
5. Régénérez la solution SimpleProject et démarrez le débogage. L’instance expérimentale doit apparaître.  
  
6. Dans l’instance expérimentale, créez une nouvelle application SimpleProject.  
  
7. Visual Studio appelle votre fabrique de projet pour créer un projet à l’aide du modèle Visual Studio. Le nouveau fichier Program.cs s’ouvre dans l’éditeur de code.  
  
8. Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions**, puis cliquez sur **Propriétés**. La boîte de dialogue **Pages de propriétés** s’affiche.  
  
   ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Test de la page de propriétés du projet  
 Vous pouvez maintenant tester si vous pouvez modifier et modifier les valeurs des propriétés.  
  
1. Dans la boîte de dialogue **pages de propriétés de MyConsoleApplication** , remplacez **DefaultNamespace** par **MyApplication**.  
  
2. Sélectionnez la propriété **OutputType** , puis sélectionnez **bibliothèque de classes**.  
  
3. Cliquez sur **Appliquer**, puis sur **OK**.  
  
4. Rouvrez la boîte de dialogue **pages de propriétés** et vérifiez que vos modifications ont été conservées.  
  
5. Fermez l’instance expérimentale de Visual Studio.  
  
6. Rouvrez l’instance expérimentale.  
  
7. Rouvrez la boîte de dialogue **pages de propriétés** et vérifiez que vos modifications ont été conservées.  
  
8. Fermez l’instance expérimentale de Visual Studio.  
  
   ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")
