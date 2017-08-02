---
title: "Cr&#233;ation d’un syst&#232;me de projet de base, partie 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "écriture d’un système de projet"
  - "système de projet"
  - "didacticiel"
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 47
---
# Cr&#233;ation d’un syst&#232;me de projet de base, partie 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser les fichiers de code source et d’autres ressources. Les projets apparaissent en tant qu’enfants de solutions dans le **l’Explorateur de solutions**. Les projets vous permettent d’organiser, générer, déboguer et déployer le code source et créer des références aux services Web, bases de données et d’autres ressources.  
  
 Les projets sont définis dans les fichiers de projet, par exemple un fichier .csproj pour un projet Visual c\#. Vous pouvez créer votre propre type de projet qui comporte votre propre extension de fichier projet. Pour plus d’informations sur les types de projets, consultez [Types de projet](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Si vous avez besoin d’étendre Visual Studio avec un type de projet personnalisé, nous recommandons en exploitant la [système de projet Visual Studio](https://github.com/Microsoft/VSProjectSystem) qui a un nombre d’avantages par rapport à la création d’un système de projet à partir de zéro :  
>   
>  -   Intégration plus facile.  Même un système de projet de base nécessite des dizaines de milliers de lignes de code.  Tirant parti de CPS permet de réduire le coût de l’intégration à quelques clics avant que vous êtes prêt à personnaliser selon vos besoins.  
> -   Facilite la maintenance.  En tirant parti de CPS, il vous suffit de mettre à jour vos propres scénarios.  Nous gérons l’entretien de l’ensemble de l’infrastructure de système de projet.  
>   
>  Si vous avez besoin pour cibler des versions de Visual Studio antérieures à Visual Studio 2013, vous ne serez pas en mesure d’utiliser CPS dans une extension Visual Studio.  Si tel est le cas, cette procédure pas à pas est un bon emplacement pour commencer.  
  
 Cette procédure pas à pas vous montre comment créer un type de projet qui a le .myproj d’extension de nom de fichier projet. Cette procédure pas à pas emprunte du système de projet Visual c\# existant.  
  
> [!NOTE]
>  Pour un exemple de bout en bout pour un langage complet du système de projet, consultez la présentation approfondie du exemple IronPython dans [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
 Cette procédure pas à pas explique comment effectuer ces tâches :  
  
-   Créer un type de projet de base.  
  
-   Créer un modèle de projet de base.  
  
-   Enregistrez le modèle de projet avec Visual Studio.  
  
-   Créez une instance de projet en ouvrant le **Nouveau projet** boîte de dialogue, puis en utilisant votre modèle.  
  
-   Créer une fabrique de projet pour votre système de projet.  
  
-   Créer un nœud de projet pour votre système de projet.  
  
-   Ajouter des icônes personnalisées pour le système de projet.  
  
-   Implémenter la substitution de paramètres de modèle de base.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Vous devez également télécharger le code source pour le [Managed Package Framework pour les projets](http://mpfproj12.codeplex.com/). Extrayez le fichier dans un emplacement accessible à la solution que vous vous apprêtez à créer.  
  
## Création d’un Type de projet de base  
 Créez un projet VSIX c\# nommé **SimpleProject**. \(**Fichier, nouveau, projet** puis **Package Visual Studio c\#, d’extensibilité,**\). Ajouter un modèle de projet de Package Visual Studio \(dans l’Explorateur de solutions, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**, puis accédez à **extensibilité \/ Package Visual Studio**\). Nommez le fichier **SimpleProjectPackage**.  
  
## Création d’un modèle de projet de base  
 À présent, vous pouvez modifier ce package VS de base pour implémenter le nouveau type de projet .myproj. Pour créer un projet basé sur le type de projet .myproj, Visual Studio doit connaître les fichiers, les ressources et les références à ajouter au nouveau projet. Pour fournir ces informations, placez les fichiers de projet dans un dossier de modèle de projet. Lorsqu’un utilisateur utilise le projet .myproj pour créer un projet, les fichiers sont copiés vers le nouveau projet.  
  
#### Pour créer un modèle de projet de base  
  
1.  Ajouter au projet, un sous l’autre trois dossiers : **Templates\\Projects\\SimpleProject**. \(Dans **l’Explorateur de solutions**, avec le bouton droit le **SimpleProject** nœud de projet, pointez sur **Ajouter**, puis cliquez sur **Nouveau dossier**. Nom du dossier `Templates`. Dans le **modèles** dossier, ajoutez un dossier nommé `Projects`. Dans le **projets** dossier, ajoutez un dossier nommé `SimpleProject`.\)  
  
2.  Dans le **Projects\\SimpleProject** dossier ajouter un fichier d’icône nommé `SimpleProject.ico`. Lorsque vous cliquez sur **Ajouter**, l’icône de l’éditeur s’ouvre.  
  
3.  Rendre l’icône distinctive. Cette icône s’affiche dans le **Nouveau projet** boîte de dialogue plus loin dans la procédure pas à pas.  
  
     ![Icône de projet simple](~/docs/extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  L’icône Enregistrer et fermer l’éditeur d’icônes.  
  
5.  Dans le **Projects\\SimpleProject** dossier, ajouter une **classe** élément nommé `Program.cs`.  
  
6.  Remplacez le code existant par les lignes suivantes.  
  
    ```c#  
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
    >  Ce n’est pas le format final de code Program.cs ; les paramètres de remplacement seront traités dans une étape ultérieure. Vous pouvez voir erreurs de compilation, mais tant que du fichier **BuildAction** est **contenu**, vous devez être en mesure de générer et exécuter le projet comme d’habitude.  
  
1.  Enregistrez le fichier.  
  
2.  Copiez le fichier AssemblyInfo.cs du **propriétés** dossier pour le **Projects\\SimpleProject** dossier.  
  
3.  Dans le **Projects\\SimpleProject** dossier ajouter un fichier XML nommé `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  L’extension de nom de fichier pour tous les projets de ce type est .myproj. Si vous souhaitez modifier, vous devez le modifier partout où qu'il est indiqué dans la procédure pas à pas.  
  
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
  
6.  Dans le **propriétés** configurez le **Action de génération** de AssemblyInfo.cs, Program.cs, SimpleProject.ico et SimpleProject.myproj à **contenu**, et définissez leurs **inclure dans VSIX** propriétés **True**.  
  
 Ce modèle de projet décrit un projet Visual c\# base ayant une configuration Debug et une configuration Release. Le projet inclut deux fichiers sources, AssemblyInfo.cs et Program.cs et assembly plusieurs références. Lorsqu’un projet est créé à partir du modèle, la valeur ProjectGuid est automatiquement remplacée par un nouveau GUID.  
  
 Dans **l’Explorateur de solutions**, développé **modèles** dossier doit apparaître comme suit :  
  
 Modèles  
  
 Projets  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## Création d’une fabrique de projet de base  
 Vous devez indiquer l’emplacement de votre dossier de modèles de projet à Visual Studio. Pour ce faire, ajoutez un attribut à la classe VSPackage qui implémente la fabrique de projets afin que l’emplacement du modèle est écrite dans le Registre système lorsque le VSPackage est généré. Commencez par créer une fabrique de projet de base qui est identifiée par une GUID de fabrique de projets. Utilisez le <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut pour se connecter de la fabrique de projets à la classe SimpleProjectPackage.  
  
#### Pour créer une fabrique de projet de base  
  
1.  Ouvrez SimpleProjectPackageGuids.cs dans l’éditeur de code.  
  
2.  Créer un GUID de votre fabrique de projet \(sur le **outils** menu, cliquez sur **créer un GUID**\), ou utilisez celui de l’exemple suivant. Ajoutez le GUID pour la classe SimpleProjectPackageGuids. Le GUID doit être sous forme GUID et sous forme de chaîne. Le code obtenu doit ressembler à l’exemple suivant.  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  Ajoutez une classe en haut **SimpleProject** dossier nommé `SimpleProjectFactory.cs`.  
  
4.  Ajoutez le code suivant à l’aide des instructions :  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Ajoutez un attribut de Guid pour la classe SimpleProjectFactory. La valeur de l’attribut est un nouveau factory de projet GUID.  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 Vous pouvez maintenant enregistrer votre modèle de projet.  
  
#### Pour enregistrer le modèle de projet  
  
1.  Dans SimpleProjectPackage.cs, ajoutez une <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> d’attribut à la classe SimpleProjectPackage, comme suit.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Régénérez la solution et vérifiez qu’il est généré sans erreur.  
  
     La reconstruction enregistre le modèle de projet.  
  
 Les paramètres `defaultProjectExtension` et `possibleProjectExtensions` sont définies sur l’extension de nom de fichier de projet \(.myproj\). Le `projectTemplatesDirectory` paramètre est défini sur le chemin d’accès relatif du dossier Modèles. Pendant la génération, ce chemin d’accès est convertie en une version complète et ajouté au Registre pour enregistrer le système de projet.  
  
## Test de l’inscription du modèle  
 Inscription de modèle indique à Visual Studio l’emplacement de votre dossier de modèles de projet afin que Visual Studio puisse afficher le nom du modèle et l’icône dans le **Nouveau projet** boîte de dialogue.  
  
#### Pour tester l’inscription du modèle  
  
1.  Appuyez sur F5 pour démarrer le débogage d’une instance expérimentale de Visual Studio.  
  
2.  Dans l’instance expérimentale, créez un nouveau projet de votre type de projet nouvellement créé. Dans le **Nouveau projet** boîte de dialogue, vous devez voir **SimpleProject** sous **modèles installés**.  
  
 Vous disposez maintenant d’une fabrique de projet est enregistrée. Toutefois, il ne peut pas encore créer un projet. Le package de projet et de la fabrique de projets collaborent pour créer et initialiser un projet.  
  
## Ajoutez le code de l’infrastructure du Package managé  
 Implémenter la connexion entre le package du projet et de la fabrique de projets.  
  
-   Importez les fichiers de code source pour l’infrastructure du Package managé.  
  
    1.  Décharger le projet SimpleProject \(dans **l’Explorateur de solutions**, sélectionnez le nœud du projet et dans le menu contextuel, cliquez sur **Décharger le projet**.\) et ouvrez le fichier projet dans l’éditeur XML.  
  
    2.  Ajoutez les blocs suivants au fichier de projet \(juste au\-dessus les blocs \< Import \>\). Définissez ProjectBasePath à l’emplacement du fichier ProjectBase.files dans le code de Managed Package Framework que vous venez de télécharger. Vous devrez peut\-être ajouter une barre oblique inverse pour le chemin d’accès. Si vous ne le faites pas, le projet peut ne pas trouver le code de l’infrastructure du Package managé.  
  
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
  
        -   Microsoft.VisualStudio.Designer.Interfaces \(dans \< installation VSSDK \> \\VisualStudioIntegration\\Common\\Assemblies\\v2.0\)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### Pour initialiser la fabrique de projets  
  
1.  Dans le fichier SimpleProjectPackage.cs, ajoutez le code suivant `using` instruction.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Dérivez la `SimpleProjectPackage` classe `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Inscription de la fabrique de projets. Ajoutez la ligne suivante à la `SimpleProjectPackage.Initialize` \(méthode\), juste après `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implémentez la propriété abstraite `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  Dans SimpleProjectFactory.cs, ajoutez le code suivant `using` instruction après le `using` instructions.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Dérivez la `SimpleProjectFactory` classe `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Ajoutez la méthode suivante factice pour le `SimpleProjectFactory` classe. Vous implémentez cette méthode dans une section ultérieure.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Ajoutez le champ et le constructeur suivant la `SimpleProjectFactory` classe. Cela `SimpleProjectPackage` référence est mise en cache dans un champ privé afin qu’il peut être utilisé lors de la définition d’un site de fournisseur de service.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Régénérez la solution et vérifiez qu’il est généré sans erreur.  
  
## L’implémentation de fabrique du projet de test  
 Teste si le constructeur pour votre implémentation de la fabrique projet est appelé.  
  
#### Pour tester l’implémentation de fabrication du projet  
  
1.  Dans le fichier SimpleProjectFactory.cs, définissez un point d’arrêt sur la ligne suivante dans le `SimpleProjectFactory` constructeur.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Appuyez sur F5 pour démarrer une instance expérimentale de Visual Studio.  
  
3.  Dans l’instance expérimentale, commencer à créer un nouveau projet. Dans le **Nouveau projet** boîte de dialogue, sélectionnez le SimpleProject type de projet, puis cliquez sur **OK**. L'exécution s'arrête au point d'arrêt.  
  
4.  Désactivez le point d’arrêt et arrêter le débogage. Étant donné que nous n’avons pas encore créé un nœud de projet, le code de création de projet encore lève des exceptions.  
  
## Extension de la classe de nœud de projet  
 Maintenant que vous pouvez implémenter la `SimpleProjectNode` classe qui dérive de la `ProjectNode` classe. La `ProjectNode` classe de base gère les tâches suivantes de la création du projet :  
  
-   Copie le fichier de modèle de projet, SimpleProject.myproj, vers le nouveau dossier de projet. La copie est renommée en fonction du nom est entré dans le **Nouveau projet** boîte de dialogue. Le `ProjectGuid` valeur de propriété est remplacée par un nouveau GUID.  
  
-   Parcourt les éléments MSBuild du fichier de modèle de projet, SimpleProject.myproj et de recherche `Compile` éléments. Pour chaque `Compile` fichier cible, copie le fichier dans le nouveau dossier de projet.  
  
 Dérivé `SimpleProjectNode` classe gère ces tâches :  
  
-   Permet des icônes pour les nœuds de projet et le fichier dans **l’Explorateur de solutions** pour être créé ou sélectionné.  
  
-   Permet de substitutions de paramètre de modèle supplémentaire à être spécifié.  
  
#### Pour étendre la classe nœud de projet  
  
1.  
  
2.  Ajoutez une classe nommée `SimpleProjectNode.cs`.  
  
3.  Remplacez le code existant par le code suivant.  
  
    ```  
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
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
-   `AddFileFromTemplate`, qui copie des fichiers sélectionnés à partir du dossier de modèle pour le projet de destination. Cette méthode est plus implémentée dans une section ultérieure.  
  
 Le `SimpleProjectNode` constructeur, comme le `SimpleProjectFactory` met en cache le constructeur, une `SimpleProjectPackage` référence dans un champ privé pour une utilisation ultérieure.  
  
 Pour vous connecter la `SimpleProjectFactory` classe le `SimpleProjectNode` \(classe\), vous devez instancier un nouveau `SimpleProjectNode` dans les `SimpleProjectFactory.CreateProject` \(méthode\) et mettre en cache dans un champ privé pour une utilisation ultérieure.  
  
#### Pour connecter la classe de fabrique du projet et la classe de nœud  
  
1.  Dans le fichier SimpleProjectFactory.cs, ajoutez le code suivant `using` instruction :  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Remplacez le `SimpleProjectFactory.CreateProject` méthode en utilisant le code suivant.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Régénérez la solution et vérifiez qu’il est généré sans erreur.  
  
## La classe du nœud du projet de test  
 Tester votre fabrique de projet pour voir si elle crée une hiérarchie de projet.  
  
#### Pour tester la classe nœud de projet  
  
1.  Appuyez sur F5 pour démarrer le débogage. Dans l’instance expérimentale, créez un nouveau SimpleProject.  
  
2.  Visual Studio doit appeler votre fabrique de projet pour créer un projet.  
  
3.  Fermez l’instance expérimentale de Visual Studio.  
  
## Ajout d’une icône de nœud de projet personnalisé  
 L’icône de nœud de projet dans la section précédente est une icône par défaut. Vous pouvez la modifier et une icône personnalisée.  
  
#### Pour ajouter une icône de nœud de projet personnalisé  
  
1.  Dans le **ressources** dossier, ajoutez un fichier bitmap nommé SimpleProjectNode.bmp.  
  
2.  Dans le **propriétés** windows, réduire la bitmap de 16 par 16 pixels. Rendre le bitmap distinctive.  
  
     ![Commande de projet simple](~/docs/extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  Dans le **propriétés** fenêtre, de modifier le **action de génération** de la bitmap à **ressource incorporée**.  
  
4.  Dans SimpleProjectNode.cs, ajoutez le code suivant `using` instructions :  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Ajoutez le champ statique suivant et le constructeur pour la `SimpleProjectNode` classe.  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Ajoutez la propriété suivante au début de la `SimpleProjectNode` classe.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Remplacez le constructeur d’instance par le code suivant.  
  
    ```  
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
  
 Pendant la construction statique, `SimpleProjectNode` extrait la bitmap de nœud de projet à partir des ressources de manifeste d’assembly et met en cache dans un champ privé pour une utilisation ultérieure. Notez que la syntaxe de la <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> chemin d’accès de l’image. Pour afficher les noms des ressources du manifestes incorporés dans un assembly, utilisez la <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> méthode. Lorsque cette méthode est appliquée à la `SimpleProject` assembly, les résultats doivent être comme suit :  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Pendant la construction de l’instance, la `ProjectNode` classe base charge Resources.imagelis.bmp, dans lequel sont incorporés bitmaps 16 x 16 couramment utilisés à partir de Resources\\imagelis.bmp. Cette liste de bitmap est mises à disposition `SimpleProjectNode` comme ImageHandler.ImageList.`SimpleProjectNode` Ajoute le bitmap de nœud de projet à la liste. Le décalage de la bitmap de nœud de projet dans la liste d’images est mis en cache pour une utilisation ultérieure en tant que la valeur public `ImageIndex` propriété. Visual Studio utilise cette propriété pour déterminer quelle image bitmap à afficher en tant que l’icône de nœud de projet.  
  
## Test de l’icône de nœud de projet personnalisé  
 Tester votre fabrique de projet pour voir si elle crée une hiérarchie de projet qui possède l’icône de nœud de votre projet personnalisé.  
  
#### Pour tester l’icône de nœud de projet personnalisé  
  
1.  Démarrer le débogage et dans l’instance expérimentale, créez un nouveau SimpleProject.  
  
2.  Dans le projet nouvellement créé, notez que SimpleProjectNode.bmp est utilisé en tant que l’icône de nœud de projet.  
  
     ![Nœud Projet simple &#45; Nouveau projet](~/docs/extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Ouvrez le fichier Program.cs dans l’éditeur de code. Vous devez voir le code source qui ressemble au code suivant.  
  
    ```  
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
  
     Notez que les paramètres du modèle $nameSpace$ et $ de $className n’ont pas de nouvelles valeurs. Vous allez apprendre à implémenter la substitution de paramètres de modèle dans la section suivante.  
  
## En substituant les paramètres de modèle  
 Dans une section précédente, vous avez inscrit le modèle de projet avec Visual Studio à l’aide de la `ProvideProjectFactory` attribut. L’enregistrement du chemin d’accès d’un dossier de modèle de cette manière vous permet d’activer la substitution de paramètres de modèle de base en substituant et en développant la `ProjectNode.AddFileFromTemplate` classe. Pour plus d'informations, consultez [Nouvelle génération de projet : Dans les coulisses, deuxième partie](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md).  
  
 Maintenant ajouter le code de remplacement pour la `AddFileFromTemplate` classe.  
  
#### Pour remplacer les paramètres de modèle  
  
1.  Dans le fichier SimpleProjectNode.cs, ajoutez le code suivant `using` instruction.  
  
    ```  
    using System.IO;  
    ```  
  
2.  Remplacez le `AddFileFromTemplate` méthode en utilisant le code suivant.  
  
    ```  
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
  
3.  Définissez un point d’arrêt dans la méthode, juste après la `className` instruction d’assignation.  
  
 Les instructions d’assignation déterminent des valeurs raisonnables pour un espace de noms et un nouveau nom de classe. Les deux `ProjectNode.FileTemplateProcessor.AddReplace` les appels de méthode remplacement les valeurs de paramètre de modèle correspondant à l’aide de ces nouvelles valeurs.  
  
## Test de la Substitution de paramètre de modèle  
 Vous pouvez maintenant tester la substitution de paramètres de modèle.  
  
#### Pour tester la substitution de paramètre de modèle  
  
1.  Démarrer le débogage et dans l’instance expérimentale, créez un nouveau SimpleProject.  
  
2.  L’exécution s’arrête au point d’arrêt dans le `AddFileFromTemplate` \(méthode\).  
  
3.  Examinez les valeurs de la `nameSpace` et `className` paramètres.  
  
    -   `nameSpace` reçoit la valeur de l’élément \< RootNamespace \> dans le fichier de modèle de projet \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj. Dans ce cas, la valeur est « MyRootNamespace ».  
  
    -   `className` reçoit la valeur du nom de fichier source de classe, sans l’extension de nom de fichier. Dans ce cas, le premier fichier à copier dans le dossier de destination est AssemblyInfo.cs ; Par conséquent, la valeur de nom de classe est « AssemblyInfo ».  
  
4.  Supprimez le point d’arrêt et appuyez sur F5 pour poursuivre l’exécution.  
  
     Visual Studio doit se terminer la création d’un projet.  
  
5.  Ouvrez le fichier Program.cs dans l’éditeur de code. Vous devez voir le code source qui ressemble au code suivant.  
  
    ```  
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
  
     Notez que l’espace de noms est désormais « MyRootNamespace » et le nom de classe est désormais « Program ».  
  
6.  Démarrer le débogage du projet. Le nouveau projet doit compiler, exécuter et afficher « Hello VSX \!\!\! » dans la fenêtre de console.  
  
     ![Commande de projet simple](~/docs/extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 Félicitations \! Vous avez implémenté un système de base du projet managé.