---
title: Création d’un système de projet de base, partie 1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97fee2a4480f3fe8e5439decfd4852a020a734ff
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232255"
---
# <a name="create-a-basic-project-system-part-1"></a>Créer un système de projet de base, partie 1
Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser les fichiers de code source et d’autres ressources. Les projets apparaissent en tant qu’enfants de solutions dans le **l’Explorateur de solutions**. Projets vous permettent d’organiser, générer, déboguer, déployer le code source et créer des références aux services Web, bases de données et d’autres ressources.  
  
 Projets sont définis dans les fichiers de projet, par exemple un *.csproj* fichier pour un projet Visual c#. Vous pouvez créer votre propre type de projet qui a votre propre extension de nom de fichier de projet. Pour plus d’informations sur les types de projets, consultez [types de projets](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Si vous avez besoin étendre Visual Studio avec un type de projet personnalisé, nous recommandons en exploitant la [système de projet Visual Studio](https://github.com/Microsoft/VSProjectSystem) (vsp) qui a un nombre d’avantages par rapport à la création d’un système de projet à partir de zéro :  
>   
>  -  Intégration plus facile.  Même un système de projet de base nécessite des dizaines de milliers de lignes de code.  En tirant parti de VSP permet de réduire le coût de l’intégration à quelques clics avant que vous êtes prêt à le personnaliser selon vos besoins.  
>  -  Maintenance plus facile.  En tirant parti de vsp, il vous suffit de mettre à jour vos propres scénarios.  Nous gérons l’entretien de toute l’infrastructure de système de projet.  
>   
>  Si vous avez besoin pour cibler des versions de Visual Studio antérieures à Visual Studio 2013, vous ne serez pas en mesure de tirer parti de vsp dans une extension Visual Studio.  Si tel est le cas, cette procédure pas à pas est un bon point de mise en route.  
  
 Cette procédure pas à pas vous montre comment créer un type de projet qui a l’extension de nom de fichier de projet *.myproj*. Cette procédure pas à pas utilise le système de projet Visual c# existant.  
  
> [!NOTE]
>  Pour plus d’exemples de projets d’extension, consultez [exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples).  
  
 Cette procédure pas à pas explique comment accomplir ces tâches :  
  
-   Créer un type de projet de base.  
  
-   Créer un modèle de projet de base.  
  
-   Enregistrez le modèle de projet avec Visual Studio.  
  
-   Créez une instance de projet en ouvrant le **nouveau projet** boîte de dialogue, puis en utilisant votre modèle.  
  
-   Créer une fabrique de projet pour votre système de projet.  
  
-   Créer un nœud de projet pour votre système de projet.  
  
-   Ajouter des icônes personnalisées pour le système de projet.  
  
-   Implémenter la substitution de paramètre de modèle de base.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Vous devez également télécharger le code source pour le [Managed Package Framework pour les projets](http://mpfproj12.codeplex.com/). Extrayez le fichier vers un emplacement accessible à la solution que vous vous apprêtez à créer.  
  
## <a name="create-a-basic-project-type"></a>Créer un type de projet de base  
 Créez un projet VSIX c# nommé **SimpleProject**. (**Fichier** > **nouveau** > **projet** , puis **Visual C#**  >   **Extensibilité** > **projet VSIX**). Ajouter un modèle d’élément de projet Package Visual Studio (sur le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément**, puis accédez à **Extensibilité** > **Package Visual Studio**). Nommez le fichier *SimpleProjectPackage*.  
  
## <a name="creating-a-basic-project-template"></a>Création d’un modèle de projet de base  
 Maintenant, vous pouvez modifier ce VSPackage de base pour implémenter la nouvelle *.myproj* type de projet. Pour créer un projet basé sur le *.myproj* type de projet, Visual Studio doit savoir quels fichiers, les ressources et les références à ajouter au nouveau projet. Pour fournir ces informations, placez les fichiers de projet dans un dossier de modèle de projet. Lorsqu’un utilisateur utilise le *.myproj* de projet pour créer un projet, les fichiers sont copiés dans le nouveau projet.  
  
### <a name="to-create-a-basic-project-template"></a>Pour créer un modèle de projet de base  
  
1.  Ajoutez trois dossiers au projet, un à l’autre : *Templates\Projects\SimpleProject*. (Dans **l’Explorateur de solutions**, avec le bouton droit le **SimpleProject** nœud de projet, pointez sur **ajouter**, puis cliquez sur **nouveau dossier**. Nommez le dossier *modèles*. Dans le *modèles* dossier, ajoutez un dossier nommé *projets*. Dans le *projets* dossier, ajoutez un dossier nommé *SimpleProject*.)  
  
2.  Dans le *Templates\Projects\SimpleProject* dossier, ajoutez un fichier Image Bitmap à utiliser comme icône nommé *SimpleProject.ico*. Lorsque vous cliquez sur **ajouter**, l’éditeur d’icônes s’ouvre.  
  
3.  Vérifiez l’icône distinctive. Cette icône s’affiche dans le **nouveau projet** boîte de dialogue plus loin dans la procédure pas à pas.  
  
     ![Icône de projet simple](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  L’icône Enregistrer et fermer l’éditeur d’icônes.  
  
5.  Dans le *Templates\Projects\SimpleProject* dossier, ajouter un **classe** élément nommé *Program.cs*.  
  
6.  Remplacez le code existant par les lignes suivantes.  
  
    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
  
    namespace $nameSpace$
    {  
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```
  
    > [!IMPORTANT]
    >  Ce n’est pas le format final de la *Program.cs* code ; le remplacement de paramètres seront traités dans une étape ultérieure. Vous pouvez voir erreurs de compilation, mais tant que le fichier **BuildAction** est **contenu**, vous devez être en mesure de générer et exécuter le projet comme d’habitude.  
  
1.  Enregistrez le fichier.  
  
2.  Copie le *AssemblyInfo.cs* de fichiers à partir de la *propriétés* dossier pour le *Projects\SimpleProject* dossier.  
  
3.  Dans le *Projects\SimpleProject* dossier ajouter un fichier XML nommé *SimpleProject.myproj*.  
  
    > [!NOTE]
    >  L’extension de nom de fichier pour tous les projets de ce type est *.myproj*. Si vous souhaitez le modifier, vous devez le modifier partout où qu'il est mentionné dans la procédure pas à pas.  
  
4.  Remplacez le contenu existant par les lignes suivantes.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
5.  Enregistrez le fichier.  
  
6.  Dans le **propriétés** fenêtre, définissez la **Action de génération** de *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* , et *SimpleProject.myproj* à **contenu**et définissez leurs **inclure dans VSIX** propriétés à **True**.  
  
 Ce modèle de projet décrit un projet Visual C# base ayant une configuration Debug et une configuration Release. Le projet comprend deux fichiers sources, *AssemblyInfo.cs* et *Program.cs*et plusieurs références d’assembly. Lorsqu’un projet est créé à partir du modèle, la valeur ProjectGuid est automatiquement remplacée par un nouveau GUID.  
  
 Dans **l’Explorateur de solutions**, développé **modèles** dossier doit apparaître comme suit :

```
Templates  
   Projects  
      SimpleProject  
         AssemblyInfo.cs  
         Program.cs  
         SimpleProject.ico  
         SimpleProject.myproj  
```

## <a name="create-a-basic-project-factory"></a>Créer une fabrique de projet de base  
 Vous devez indiquer à Visual Studio l’emplacement du dossier de modèles de projet. Pour ce faire, ajoutez un attribut à la classe VSPackage qui implémente la fabrique de projets afin que l’emplacement du modèle est écrite dans le Registre système lorsque le VSPackage est généré. Commencez par créer une fabrique de projet de base qui est identifiée par un GUID de fabrique de projet. Utilisez le <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut pour se connecter à la fabrique de projets à la `SimpleProjectPackage` classe.  
  
### <a name="to-create-a-basic-project-factory"></a>Pour créer une fabrique de projet de base  
  
1.  Créer des GUID de votre fabrique de projet (sur le **outils** menu, cliquez sur **créer un GUID**), ou utiliser celui de l’exemple suivant. Ajoutez les GUID pour le `SimpleProjectPackage` classe près de la section avec déjà défini `PackageGuidString`. Les GUID doivent être sous forme GUID et sous forme de chaîne. Le code résultant doit ressembler à l’exemple suivant.  
  
    ```csharp  
        public sealed class SimpleProjectPackage : Package
        {  
            ...
            public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
            public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
    
            public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);  
        }  
    ```  
  
3.  Ajoutez une classe au début *SimpleProject* dossier nommé *SimpleProjectFactory.cs*.  
  
4.  Ajoutez le code suivant à l’aide d’instructions :  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Ajoutez un attribut GUID à la `SimpleProjectFactory` classe. La valeur de l’attribut est la nouvelle fabrique de projet GUID.  
  
    ```csharp  
    [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Vous pouvez maintenant enregistrer votre modèle de projet.  
  
### <a name="to-register-the-project-template"></a>Pour inscrire le modèle de projet  
  
1.  Dans *SimpleProjectPackage.cs*, ajoutez un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut le `SimpleProjectPackage` de classe, comme suit.  
  
    ```csharp  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectPackage.PackageGuidString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Régénérez la solution et vérifiez qu’il se génère sans erreur.  
  
     La reconstruction enregistre le modèle de projet.  
  
 Les paramètres `defaultProjectExtension` et `possibleProjectExtensions` sont définies à l’extension de nom de fichier de projet (*.myproj*). Le `projectTemplatesDirectory` paramètre est défini sur le chemin d’accès relatif de la *modèles* dossier. Pendant la génération, ce chemin d’accès est convertie en une génération complète et ajouté au Registre pour inscrire le système de projet.  
  
## <a name="test-the-template-registration"></a>L’inscription du modèle de test  
 Inscription de modèle indique à Visual Studio l’emplacement du dossier de modèles de projet afin que Visual Studio peut afficher le nom du modèle et l’icône dans le **nouveau projet** boîte de dialogue.  
  
### <a name="to-test-the-template-registration"></a>Pour tester le modèle d’inscription  
  
1.  Appuyez sur **F5** pour démarrer le débogage d’une instance expérimentale de Visual Studio.  
  
2.  Dans l’instance expérimentale, créez un nouveau projet de votre type de projet nouvellement créé. Dans le **nouveau projet** boîte de dialogue, vous devez voir **SimpleProject** sous **modèles installés**.  
  
 Vous disposez maintenant d’une fabrique de projet qui est inscrit. Toutefois, il ne peut pas encore créer un projet. Le package de projet et de la fabrique de projet fonctionnent ensemble pour créer et initialiser un projet.  
  
## <a name="add-the-managed-package-framework-code"></a>Ajoutez le code de Managed Package Framework  
 Implémenter la connexion entre le package de projet et de la fabrique de projets.  
  
-   Importez les fichiers de code source de Managed Package Framework.  
  
    1.  Décharger le projet SimpleProject (dans **l’Explorateur de solutions**, sélectionnez le nœud du projet et dans le menu contextuel, cliquez sur **décharger le projet**.) et ouvrez le fichier projet dans l’éditeur XML.  
  
    2.  Ajoutez les blocs suivants au fichier projet (juste au-dessus du \<importation > blocs). Définissez `ProjectBasePath` à l’emplacement de la *ProjectBase.files* fichier dans le code de Managed Package Framework que vous venez de télécharger. Vous devrez peut-être ajouter une barre oblique inverse pour le chemin d’accès. Si vous ne le faites pas, le projet peut ne pas trouver le code source de Managed Package Framework.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  N’oubliez pas la barre oblique inverse à la fin du chemin d’accès.  
  
    3.  Recharger le projet.  
  
    4.  Ajoutez des références aux assemblys suivants :  
  
        -   `Microsoft.VisualStudio.Designer.Interfaces` (dans  *\<installation de l’extensibilité Visual Studio > \VisualStudioIntegration\Common\Assemblies\v2.0*)  
  
        -   `WindowsBase`  
  
        -   `Microsoft.Build.Tasks.v4.0`  
  
### <a name="to-initialize-the-project-factory"></a>Pour initialiser la fabrique de projets  
  
1.  Dans le *SimpleProjectPackage.cs* de fichier, ajoutez le code suivant `using` instruction.  
  
    ```csharp  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Dériver les `SimpleProjectPackage` classe `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```csharp  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Inscrire la fabrique de projets. Ajoutez la ligne suivante à la `SimpleProjectPackage.Initialize` (méthode), juste après `base.Initialize`.  
  
    ```csharp  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implémente la propriété abstraite `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  Dans *SimpleProjectFactory.cs*, ajoutez le code suivant `using` instruction après existant `using` instructions.  
  
    ```csharp  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Dériver les `SimpleProjectFactory` classe `ProjectFactory`.  
  
    ```csharp  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Ajoutez la méthode suivante factice à le `SimpleProjectFactory` classe. Vous implémentez cette méthode dans une section ultérieure.  
  
    ```csharp  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Ajoutez le champ et le constructeur suivant la `SimpleProjectFactory` classe. Cela `SimpleProjectPackage` référence est mis en cache dans un champ privé afin qu’il peut être utilisé lors de la définition d’un site de fournisseur de service.  
  
    ```csharp  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Régénérez la solution et vérifiez qu’il se génère sans erreur.  
  
## <a name="test-the-project-factory-implementation"></a>Tester l’implémentation de fabrique de projet  
 Teste si le constructeur pour votre implémentation de fabrique de projet est appelé.  
  
### <a name="to-test-the-project-factory-implementation"></a>Pour tester l’implémentation de fabrique de projet  
  
1.  Dans le *SimpleProjectFactory.cs* de fichier, définir un point d’arrêt sur la ligne suivante dans le `SimpleProjectFactory` constructeur.  
  
    ```csharp  
    this.package = package;  
    ```  
  
2.  Appuyez sur **F5** pour démarrer une instance expérimentale de Visual Studio.  
  
3.  Dans l’instance expérimentale, commencer à créer un nouveau projet. Dans le **nouveau projet** boîte de dialogue, sélectionnez le **SimpleProject** type de projet, puis cliquez sur **OK**. L'exécution s'arrête au point d'arrêt.  
  
4.  Désactivez le point d’arrêt et arrêter le débogage. Étant donné que nous n’avons pas encore créé un nœud de projet, le code de création de projet toujours lève des exceptions.  
  
## <a name="extend-the-projectnode-class"></a>Étendre la classe ProjectNode  
 Maintenant que vous pouvez implémenter la `SimpleProjectNode` classe qui dérive de la `ProjectNode` classe. Le `ProjectNode` classe de base gère les tâches suivantes de création du projet :  
  
-   Copie le fichier de modèle de projet, *SimpleProject.myproj*, vers le nouveau dossier de projet. La copie est renommée en fonction du nom est entré dans le **nouveau projet** boîte de dialogue. Le `ProjectGuid` valeur de propriété est remplacée par un nouveau GUID.  
  
-   Parcourt les éléments MSBuild du fichier de modèle de projet, *SimpleProject.myproj*et recherche `Compile` éléments. Pour chaque `Compile` fichier cible, copie le fichier dans le nouveau dossier de projet.  
  
 La dérivée `SimpleProjectNode` classe gère ces tâches :  
  
-   Permet des icônes pour les nœuds de projet et fichier dans **l’Explorateur de solutions** à être créé ou sélectionné.  
  
-   Permet les substitutions de paramètre de modèle de projet supplémentaire être spécifié.  
  
### <a name="to-extend-the-projectnode-class"></a>Pour étendre la classe ProjectNode  
  
1.  Ajoutez une classe nommée `SimpleProjectNode.cs`.  
  
2.  Remplacez le code existant par le code ci-dessous.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Project;  
  
    namespace SimpleProject  
    {  
        public class SimpleProjectNode : ProjectNode  
        {  
            private SimpleProjectPackage package;  
  
            public SimpleProjectNode(SimpleProjectPackage package)  
            {  
                this.package = package;  
            }  
            public override Guid ProjectGuid  
            {  
                get { return SimpleProjectPackage.guidSimpleProjectFactory; }  
            }  
            public override string ProjectType  
            {  
                get { return "SimpleProjectType"; }  
            }  
  
            public override void AddFileFromTemplate(  
                string source, string target)  
            {  
                this.FileTemplateProcessor.UntokenFile(source, target);  
                this.FileTemplateProcessor.Reset();  
            }  
        }  
    }  
    ```  
  
 Cela `SimpleProjectNode` implémentation de la classe a les méthodes substituées :  
  
-   `ProjectGuid`, qui retourne le GUID de la fabrique de projets.  
  
-   `ProjectType`, qui retourne le nom localisé du type de projet.  
  
-   `AddFileFromTemplate`, qui copie les fichiers sélectionnés à partir du dossier de modèle pour le projet de destination. Cette méthode est plus implémentée dans une section ultérieure.  
  
 Le `SimpleProjectNode` constructeur, comme le `SimpleProjectFactory` met en cache du constructeur, un `SimpleProjectPackage` référence dans un champ privé pour une utilisation ultérieure.  
  
 Pour vous connecter la `SimpleProjectFactory` classe à la `SimpleProjectNode` (classe), vous devez instancier un nouveau `SimpleProjectNode` dans le `SimpleProjectFactory.CreateProject` (méthode) et le met en cache dans un champ privé pour une utilisation ultérieure.  
  
### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Pour connecter la classe de fabrique de projet et de la classe de nœud  
  
1.  Dans le *SimpleProjectFactory.cs* de fichier, ajoutez le code suivant `using` instruction :  
  
    ```csharp  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Remplacez le `SimpleProjectFactory.CreateProject` méthode en utilisant le code suivant.  
  
    ```csharp  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Régénérez la solution et vérifiez qu’il se génère sans erreur.  
  
## <a name="test-the-projectnode-class"></a>Tester la classe ProjectNode  
 Tester votre fabrique de projet pour voir si elle crée une hiérarchie de projet.  
  
### <a name="to-test-the-projectnode-class"></a>Pour tester la classe ProjectNode  
  
1.  Appuyez sur **F5** pour démarrer le débogage. Dans l’instance expérimentale, créez un nouveau SimpleProject.  
  
2.  Visual Studio doit appeler votre fabrique de projet pour créer un projet.  
  
3.  Fermez l’instance expérimentale de Visual Studio.  
  
## <a name="add-a-custom-project-node-icon"></a>Ajouter une icône de nœud de projet personnalisé  
 L’icône du nœud de projet dans la section précédente est une icône par défaut. Vous pouvez le modifier pour une icône personnalisée.  
  
### <a name="to-add-a-custom-project-node-icon"></a>Pour ajouter une icône de nœud de projet personnalisé  
  
1.  Dans le **ressources** dossier, ajoutez un fichier bitmap nommé *SimpleProjectNode.bmp*.  
  
2.  Dans le **propriétés** windows, réduire la bitmap de 16 par 16 pixels. Rendre le bitmap distinctive.  
  
     ![Commande de projet simple](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  Dans le **propriétés** fenêtre, de modifier le **action de génération** de la bitmap à **ressource incorporée**.  
  
4.  Dans *SimpleProjectNode.cs*, ajoutez le code suivant `using` instructions :  
  
    ```csharp  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Ajoutez le champ statique suivant et le constructeur pour la `SimpleProjectNode` classe.  
  
    ```csharp  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Ajoutez la propriété suivante au début de la `SimpleProjectNode` classe.  
  
    ```csharp  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Remplacez le constructeur d’instance avec le code suivant.  
  
    ```csharp  
    public SimpleProjectNode(SimpleProjectPackage package)  
    {  
        this.package = package;  
  
        imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
        foreach (Image img in imageList.Images)  
        {  
            this.ImageHandler.AddImage(img);  
        }  
    }  
    ```  
  
 Pendant la construction statique, `SimpleProjectNode` récupère la bitmap de nœud de projet à partir des ressources de manifeste d’assembly et met en cache dans un champ privé pour une utilisation ultérieure. Notez la syntaxe de la <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> chemin d’accès de l’image. Pour afficher les noms des ressources de manifeste incorporés dans un assembly, utilisez le <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> (méthode). Lorsque cette méthode est appliquée à la `SimpleProject` assembly, les résultats doivent être comme suit :  
  
-   *SimpleProject.Resources.resources*  
  
-   *VisualStudio.Project.resources*  
  
-   *SimpleProject.VSPackage.resources*  
  
-   *Resources.imagelis.bmp*  
  
-   *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*  
  
-   *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*  
  
-   *SimpleProject.Resources.SimpleProjectNode.bmp*  
  
 Pendant la construction de l’instance, le `ProjectNode` chargements de classe de base *Resources.imagelis.bmp*, dans qui sont incorporé couramment utilisé des bitmaps de 16 x 16 de *Resources\imagelis.bmp*. Cette liste de bitmap est mises à disposition `SimpleProjectNode` comme `ImageHandler.ImageList`. `SimpleProjectNode` Ajoute la bitmap de nœud de projet à la liste. Le décalage de la bitmap de nœud de projet dans la liste d’images est mis en cache pour une utilisation ultérieure en tant que la valeur du public `ImageIndex` propriété. Visual Studio utilise cette propriété pour déterminer quelle bitmap à afficher en tant que l’icône de nœud de projet.  
  
## <a name="test-the-custom-project-node-icon"></a>Tester l’icône de nœud de projet personnalisé  
 Tester votre fabrique de projet pour voir si elle crée une hiérarchie de projet qui possède l’icône de nœud de projet personnalisé.  
  
### <a name="to-test-the-custom-project-node-icon"></a>Pour tester l’icône de nœud de projet personnalisé  
  
1.  Démarrer le débogage et dans l’instance expérimentale, créez un nouveau SimpleProject.  
  
2.  Dans le projet nouvellement créé, notez que *SimpleProjectNode.bmp* est utilisé en tant que l’icône de nœud de projet.  
  
     ![Nœud de projet simple nouveau projet](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Ouvrez *Program.cs* dans l’éditeur de code. Vous devez voir le code source qui ressemble au code suivant.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Notez que les paramètres du modèle $nameSpace$ et $ de $className n’ont pas de nouvelles valeurs. Vous allez apprendre à implémenter la substitution de paramètre de modèle dans la section suivante.  
  
## <a name="substitute-template-parameters"></a>Substituer des paramètres de modèle  
 Dans la section précédente, vous inscrit le modèle de projet avec Visual Studio à l’aide de la `ProvideProjectFactory` attribut. Inscrire le chemin d’accès d’un dossier de modèle de cette manière vous permet d’activer la substitution de paramètre de modèle de base en remplaçant et en développant la `ProjectNode.AddFileFromTemplate` classe. Pour plus d’informations, consultez [nouvelle génération de projet : sous le capot, deuxième partie](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Ajoutez maintenant le code de remplacement pour le `AddFileFromTemplate` classe.  
  
### <a name="to-substitute-template-parameters"></a>Pour substituer des paramètres de modèle  
  
1.  Dans le *SimpleProjectNode.cs* de fichier, ajoutez le code suivant `using` instruction.  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Remplacez le `AddFileFromTemplate` méthode en utilisant le code suivant.  
  
    ```csharp  
    public override void AddFileFromTemplate(  
        string source, string target)  
    {  
        string nameSpace =   
            this.FileTemplateProcessor.GetFileNamespace(target, this);  
        string className = Path.GetFileNameWithoutExtension(target);  
  
        this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
        this.FileTemplateProcessor.AddReplace("$className$", className);  
  
        this.FileTemplateProcessor.UntokenFile(source, target);  
        this.FileTemplateProcessor.Reset();  
    }  
    ```  
  
3.  Définir un point d’arrêt dans la méthode, juste après la `className` instruction d’assignation.  
  
 Les instructions d’assignation déterminent des valeurs raisonnables pour un espace de noms et un nouveau nom de classe. Les deux `ProjectNode.FileTemplateProcessor.AddReplace` appels de méthode remplacement les valeurs de paramètre de modèle correspondant à l’aide de ces nouvelles valeurs.  
  
## <a name="test-the-template-parameter-substitution"></a>Tester la substitution de paramètre de modèle  
 Vous pouvez maintenant tester la substitution de paramètre de modèle.  
  
### <a name="to-test-the-template-parameter-substitution"></a>Pour tester la substitution de paramètre de modèle  
  
1.  Démarrer le débogage et dans l’instance expérimentale, créez un nouveau SimpleProject.  
  
2.  L’exécution s’arrête au point d’arrêt dans le `AddFileFromTemplate` (méthode).  
  
3.  Examiner les valeurs pour le `nameSpace` et `className` paramètres.  
  
    -   `nameSpace` se voit attribuer la valeur de la \<RootNamespace > élément dans le *\Templates\Projects\SimpleProject\SimpleProject.myproj* fichier de modèle de projet. Dans ce cas, la valeur est `MyRootNamespace`.  
  
    -   `className` reçoit la valeur du nom de fichier source de classe, sans l’extension de nom de fichier. Dans ce cas, le premier fichier à copier vers le dossier de destination est *AssemblyInfo.cs*; par conséquent, la valeur de nom de classe est `AssemblyInfo`.  
  
4.  Supprimer le point d’arrêt et appuyez sur **F5** pour continuer l’exécution.  
  
     Visual Studio doit se terminer la création d’un projet.  
  
5.  Ouvrez *Program.cs* dans l’éditeur de code. Vous devez voir le code source qui ressemble au code suivant.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace MyRootNamespace  
    {  
        public class Program  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Notez que l’espace de noms est désormais `MyRootNamespace` et le nom de classe est désormais `Program`.  
  
6.  Commencez à déboguer le projet. Le nouveau projet doit compiler, exécuter et afficher « Hello VSX !!! » dans la fenêtre de console.  
  
     ![Commande de projet simple](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Félicitations ! Vous avez implémenté un système de base du projet managé.