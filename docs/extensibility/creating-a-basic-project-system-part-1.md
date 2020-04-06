---
title: Création d’un système de projet de base, Partie 1 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739725"
---
# <a name="create-a-basic-project-system-part-1"></a>Créer un système de projet de base, partie 1
Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser des fichiers de code source et d’autres actifs. Les projets apparaissent comme des enfants de solutions dans la **Solution Explorer**. Les projets vous permettent d’organiser, de construire, de déboiffer et de déployer du code source et de créer des références aux services Web, aux bases de données et à d’autres ressources.

 Les projets sont définis dans les fichiers de projet, par exemple un fichier *.csproj* pour un projet Visual C. Vous pouvez créer votre propre type de projet qui a votre propre extension de nom de fichier de projet. Pour plus d’informations sur les types de projets, voir [les types de projets](../extensibility/internals/project-types.md).

> [!NOTE]
> Si vous avez besoin d’étendre Visual Studio avec un type de projet personnalisé, nous vous recommandons fortement de tirer parti du [système de projet Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS) qui présente un certain nombre d’avantages par rapport à la construction d’un système de projet à partir de zéro :
>
> - Plus facile à bord.  Même un système de projet de base nécessite des dizaines de milliers de lignes de code.  L’effet de levier VSPS réduit le coût d’intégration à quelques clics avant d’être prêt à le personnaliser en fonction de vos besoins.
> - Entretien plus facile.  En tirant parti de VSPS, vous n’avez qu’à maintenir vos propres scénarios.  Nous nous occupons de l’entretien de toute l’infrastructure du système de projet.
>
>   Si vous avez besoin de cibler les versions de Visual Studio plus anciennes que Visual Studio 2013, vous ne serez pas en mesure de tirer parti de VSPS dans une extension Visual Studio.  Si c’est le cas, cette procédure pas à pas est un bon endroit pour commencer.

 Ce pas-là vous montre comment créer un type de projet qui a l’extension du nom de fichier de projet *.myproj*. Cette procédure pas à pas emprunte au système de projet Visual CMD existant.

> [!NOTE]
> Pour plus d’exemples de projets d’extension, voir [échantillons VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Ce pas-là enseigne comment accomplir ces tâches :

- Créez un type de projet de base.

- Créez un modèle de projet de base.

- Enregistrez le modèle de projet avec Visual Studio.

- Créez une instance de projet en ouvrant la boîte de dialogue **du nouveau projet,** puis en utilisant votre modèle.

- Créez une usine de projet pour votre système de projet.

- Créez un nœud de projet pour votre système de projet.

- Ajoutez des icônes personnalisées pour le système de projet.

- Implémentez la substitution de paramètres de base du modèle.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Vous devez également télécharger le code source pour le [cadre de paquet géré pour les projets](https://github.com/tunnelvisionlabs/MPFProj10). Extraire le fichier à un endroit accessible à la solution que vous allez créer.

## <a name="create-a-basic-project-type"></a>Créer un type de projet de base
 Créez un projet VSIX CMD nommé **SimpleProject**. (**Fichier** > **Nouveau** > **Projet,** puis Visual C **'Extensibility** >  **Visual C#** > **VSIX Project**). Ajoutez un modèle d’élément de projet Visual Studio Package (sur la **Solution Explorer**, cliquez à droite sur le nœud du projet et **sélectionnez Ajouter** > **un nouvel article,** puis allez à **Extensibility** > **Visual Studio Package**). Nommez le fichier *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Création d’un modèle de projet de base
 Maintenant, vous pouvez modifier ce VSPackage de base pour implémenter le nouveau type de projet *.myproj.* Pour créer un projet basé sur le type de projet *.myproj,* Visual Studio doit savoir quels fichiers, ressources et références à ajouter au nouveau projet. Pour fournir ces informations, placez les fichiers de projet dans un dossier de modèle de projet. Lorsqu’un utilisateur utilise le projet *.myproj* pour créer un projet, les fichiers sont copiés sur le nouveau projet.

### <a name="to-create-a-basic-project-template"></a>Créer un modèle de projet de base

1. Ajoutez trois dossiers au projet, l’un sous l’autre : *Templates-Projects-SimpleProject*. (Dans **Solution Explorer**, cliquez à droite sur le nœud du projet **SimpleProject,** pointez-le **vers Ajouter,** puis cliquez sur **New Folder**. Nommez le dossier *Templates*. Dans le dossier *Templates,* ajouter un dossier nommé *Projets*. Dans le dossier *Projets,* ajouter un dossier nommé *SimpleProject*.)

2. Dans le dossier *Templates-Projects-SimpleProject,* ajoutez un fichier Bitmap Image à utiliser comme icône appelée *SimpleProject.ico*. Lorsque vous cliquez sur **Ajouter**, l’éditeur d’icônes s’ouvre.

3. Distinguez l’icône. Cette icône apparaîtra dans la boîte de dialogue **Du nouveau projet** plus tard dans la procédure pas à pas.

    ![Icône de projet simple](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Enregistrer l’icône et fermer l’éditeur d’icône.

5. Dans le dossier *Templates-Projects-SimpleProject,* ajoutez un élément **de classe** nommé *Program.cs*.

6. Remplacez le code existant par les lignes suivantes.

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
   > Ce n’est pas la forme finale du code *Program.cs;* les paramètres de remplacement seront traités ultérieurement. Vous pouvez voir compiler des erreurs, mais tant que **buildAction** du fichier est **content,** vous devriez être en mesure de construire et d’exécuter le projet comme d’habitude.

7. Enregistrez le fichier .

8. Copiez le fichier *AssemblyInfo.cs* du dossier *Propriétés* au dossier *Projects-SimpleProject.*

9. Dans le dossier *Projects-SimpleProject* ajouter un fichier XML nommé *SimpleProject.myproj*.

   > [!NOTE]
   > L’extension de nom de fichier pour tous les projets de ce type est *.myproj*. Si vous voulez le changer, vous devez le changer partout où il est mentionné dans la procédure pas à pas.

10. Remplacez le contenu existant par les lignes suivantes.

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

11. Enregistrez le fichier .

12. Dans la fenêtre **Propriétés,** définir **l’action** de construction de *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico*, et *SimpleProject.myproj* à **contenu**, et définir leur inclure dans les propriétés **VSIX** à **True**.

    Ce modèle de projet décrit un projet visual de base de CMD qui a à la fois une configuration Debug et une configuration de version. Le projet comprend deux fichiers sources, *AssemblyInfo.cs* et *Program.cs,* et plusieurs références d’assemblage. Lorsqu’un projet est créé à partir du modèle, la valeur ProjectGuid est automatiquement remplacée par un nouveau GUID.

    Dans **Solution Explorer**, le dossier **Templates** élargi doit apparaître comme suit :

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Créer une usine de projet de base
 Vous devez indiquer à Visual Studio l’emplacement de votre dossier de modèle de projet. Pour ce faire, ajoutez un attribut à la classe VSPackage qui implémente l’usine de projet de sorte que l’emplacement du modèle est écrit au registre du système lorsque le VSPackage est construit. Commencez par créer une usine de projet de base qui est identifiée par une usine de projet GUID. Utilisez <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> l’attribut pour relier `SimpleProjectPackage` l’usine de projet à la classe.

### <a name="to-create-a-basic-project-factory"></a>Créer une usine de projet de base

1. Créez des GUIDs pour votre usine de projet (sur le menu **Tools,** cliquez sur **Create GUID),** ou utilisez celle dans l’exemple suivant. Ajouter les GUIDs `SimpleProjectPackage` à la classe près `PackageGuidString`de la section avec le déjà défini . Les GUID doivent être sous forme de GUID et sous forme de chaîne. Le code qui en résulte doit ressembler à l’exemple suivant.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Ajoutez une classe au dossier *SimpleProject* haut nommé *SimpleProjectFactory.cs*.

3. Ajoutez les directives using suivantes :

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Ajoutez un attribut GUID à la `SimpleProjectFactory` classe. La valeur de l’attribut est la nouvelle usine de projet GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Vous pouvez maintenant enregistrer votre modèle de projet.

### <a name="to-register-the-project-template"></a>Pour enregistrer le modèle de projet

1. En *SimpleProjectPackage.cs*, ajouter <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> un attribut `SimpleProjectPackage` à la classe, comme suit.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Reconstruire la solution et vérifier qu’elle se construit sans erreurs.

    La reconstruction enregistre le modèle de projet.

   Les paramètres `defaultProjectExtension` `possibleProjectExtensions` et sont réglés sur l’extension du nom du fichier du projet (*.myproj*). Le `projectTemplatesDirectory` paramètre est réglé sur la trajectoire relative du dossier *Templates.* Pendant la construction, ce chemin sera converti en une construction complète et ajouté au registre pour enregistrer le système de projet.

## <a name="test-the-template-registration"></a>Testez l’enregistrement du modèle
 L’enregistrement de modèle indique à Visual Studio l’emplacement de votre dossier de modèle de projet afin que Visual Studio puisse afficher le nom et l’icône du modèle dans la boîte de dialogue **du nouveau projet.**

### <a name="to-test-the-template-registration"></a>Pour tester l’enregistrement du modèle

1. Appuyez sur **F5** pour commencer à déboguer une instance expérimentale de Visual Studio.

2. Dans le cas expérimental, créez un nouveau projet de votre nouveau type de projet. Dans la boîte de dialogue **du nouveau projet,** vous devriez voir **SimpleProject** sous **les modèles installés**.

   Maintenant, vous avez une usine de projet qui est enregistrée. Cependant, il ne peut pas encore créer un projet. Le projet et l’usine de projet travaillent ensemble pour créer et initialiser un projet.

## <a name="add-the-managed-package-framework-code"></a>Ajouter le code-cadre du paquet géré
 Mettre en œuvre le lien entre le paquet de projet et l’usine du projet.

- Importer les fichiers de code source pour le cadre de paquet géré.

    1. Déchargez le projet SimpleProject (dans **Solution Explorer**, sélectionnez le nœud de projet et sur le menu contextuellez **sur Le projet De décharge .)** et ouvrez le fichier de projet dans l’éditeur XML.

    2. Ajoutez les blocs suivants au fichier \<du projet (juste au-dessus des blocs d’importation>). Rendez-vous `ProjectBasePath` à l’emplacement du fichier *ProjectBase.files* dans le code cadre de paquet géré que vous venez de télécharger. Vous devrez peut-être ajouter un contredise-fond au nom du chemin. Si vous ne le faites pas, le projet pourrait ne pas trouver le code source du cadre de paquet géré.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > N’oubliez pas la barre oblique inverse à la fin du chemin.

    3. Recharger le projet.

    4. Ajoutez des références aux assemblys suivants :

        - `Microsoft.VisualStudio.Designer.Interfaces`(dans * \<l’installation VSSDK>-VisualStudioIntegration-Common-AssembliesMD v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Pour initialiser l’usine de projet

1. Dans le dossier *SimpleProjectPackage.cs,* ajoutez `using` la directive suivante.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Dérivez `SimpleProjectPackage` la `Microsoft.VisualStudio.Package.ProjectPackage`classe de .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Enregistrez l’usine du projet. Ajouter la ligne `SimpleProjectPackage.Initialize` suivante à `base.Initialize`la méthode, juste après .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Mettre en `ProductUserContext`œuvre la propriété abstraite :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. En *SimpleProjectFactory.cs*, ajouter la `using` directive suivante `using` après les directives existantes.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Dérivez `SimpleProjectFactory` la `ProjectFactory`classe de .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Ajoutez la méthode factice `SimpleProjectFactory` suivante à la classe. Vous implémenterez cette méthode dans une section ultérieure.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Ajoutez le champ et le `SimpleProjectFactory` constructeur suivants à la classe. Cette `SimpleProjectPackage` référence est mise en cache dans un domaine privé afin qu’elle puisse être utilisée dans la configuration d’un site de fournisseur de services.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Reconstruire la solution et vérifier qu’elle se construit sans erreurs.

## <a name="test-the-project-factory-implementation"></a>Testez la mise en œuvre de l’usine du projet
 Testez si le constructeur de votre mise en œuvre d’usine de projet est appelé.

### <a name="to-test-the-project-factory-implementation"></a>Pour tester la mise en œuvre de l’usine du projet

1. Dans le fichier *SimpleProjectFactory.cs,* définissez un point d’arrêt sur la ligne suivante dans le `SimpleProjectFactory` constructeur.

    ```csharp
    this.package = package;
    ```

2. Appuyez sur **F5** pour commencer une instance expérimentale de Visual Studio.

3. Dans le cas expérimental, commencez à créer un nouveau projet. Dans la boîte de dialogue **du nouveau projet,** sélectionnez le type de projet **SimpleProject,** puis cliquez **sur OK**. L’exécution s’interrompt au point d’arrêt.

4. Effacer le point d’arrêt et arrêter de débogage. Comme nous n’avons pas encore créé de nœud de projet, le code de création de projet continue de faire des exceptions.

## <a name="extend-the-projectnode-class"></a>Étendre la classe ProjectNode
 Maintenant, vous `SimpleProjectNode` pouvez implémenter `ProjectNode` la classe, qui dérive de la classe. La `ProjectNode` classe de base s’occupe des tâches suivantes de création de projet :

- Copie du fichier modèle de projet, *SimpleProject.myproj*, au nouveau dossier de projet. La copie est rebaptisée selon le nom qui est inscrit dans la boîte de dialogue **du nouveau projet.** La `ProjectGuid` valeur de la propriété est remplacée par un nouveau GUID.

- Traverse les éléments MSBuild du fichier modèle de projet, *SimpleProject.myproj*, et recherche des `Compile` éléments. Pour `Compile` chaque fichier cible, copie le fichier au nouveau dossier de projet.

  La `SimpleProjectNode` classe dérivée s’occupe de ces tâches :

- Permet de créer ou de sélectionner des icônes pour les nœuds de projet et de fichier dans **Solution Explorer.**

- Permet de préciser d’autres remplacements de paramètres du modèle de projet.

### <a name="to-extend-the-projectnode-class"></a>Étendre la classe ProjectNode

1. Ajoutez une classe nommée `SimpleProjectNode.cs`.

2. Remplacez le code existant par le code ci-dessous.

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

   Cette `SimpleProjectNode` mise en œuvre de classe a ces méthodes primordiales :

- `ProjectGuid`, qui renvoie l’usine de projet GUID.

- `ProjectType`, qui renvoie le nom localisé du type de projet.

- `AddFileFromTemplate`, qui copie des fichiers sélectionnés du dossier de modèle au projet de destination. Cette méthode est ensuite mise en œuvre dans une section ultérieure.

  Le `SimpleProjectNode` constructeur, comme `SimpleProjectFactory` le constructeur, `SimpleProjectPackage` cache une référence dans un champ privé pour une utilisation ultérieure.

  Pour connecter `SimpleProjectFactory` la `SimpleProjectNode` classe à la classe, `SimpleProjectNode` vous `SimpleProjectFactory.CreateProject` devez instantané un nouveau dans la méthode et le mettre en cache dans un champ privé pour une utilisation ultérieure.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Pour connecter la classe d’usine de projet et la classe de nœud

1. Dans le dossier *SimpleProjectFactory.cs,* ajoutez `using` la directive suivante :

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Remplacez `SimpleProjectFactory.CreateProject` la méthode en utilisant le code suivant.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Reconstruire la solution et vérifier qu’elle se construit sans erreurs.

## <a name="test-the-projectnode-class"></a>Testez la classe ProjectNode
 Testez votre usine de projet pour voir si elle crée une hiérarchie de projet.

### <a name="to-test-the-projectnode-class"></a>Pour tester la classe ProjectNode

1. Appuyez sur **F5** pour démarrer le débogage. Dans le cas expérimental, créez un nouveau SimpleProject.

2. Visual Studio devrait appeler votre usine de projet pour créer un projet.

3. Fermez l’instance expérimentale de Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Ajouter une icône de nœud de projet personnalisée
 L’icône du nœud de projet dans la section précédente est une icône par défaut. Vous pouvez le changer en une icône personnalisée.

### <a name="to-add-a-custom-project-node-icon"></a>Pour ajouter une icône de nœud de projet personnalisée

1. Dans le dossier **Ressources,** ajouter un fichier bitmap nommé *SimpleProjectNode.bmp*.

2. Dans les fenêtres **Propriétés,** réduisez la bitmap à 16 par 16 pixels. Rendre la bitmap distinctive.

    ![Commande de projet simple](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Dans la fenêtre **Propriétés,** changer **l’action Build** de la bitmap à **Embedded Resource**.

4. Dans *SimpleProjectNode.cs*, ajouter les `using` directives suivantes:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Ajoutez le champ statique et `SimpleProjectNode` le constructeur suivants à la classe.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Ajoutez la propriété suivante au `SimpleProjectNode` début de la classe.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Remplacez le constructeur d’instance par le code suivant.

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

   Pendant la `SimpleProjectNode` construction statique, récupère le bitmap de nœud de projet des ressources manifestes d’assemblage et le cache dans un champ privé pour une utilisation ultérieure. Remarquez la syntaxe du chemin de l’image. <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> Pour voir les noms des ressources manifestes <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> intégrées dans un assemblage, utilisez la méthode. Lorsque cette méthode est `SimpleProject` appliquée à l’assemblage, les résultats doivent être les suivants :

- *SimpleProject.Resources.resources.resources*

- *VisualStudio.Project.ressources*

- *SimpleProject.VSPackage.ressources*

- *Resources.imagelis.bmp (en anglais)*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources Microsoft.VisualStudio.Project.SecurityWarningDialog.resources Microsoft.VisualStudio.Project.SecurityWarningDialog.resources Microsoft.*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Lors de la `ProjectNode` construction par exemple, la classe de base charge *Resources.imagelis.bmp*, dans lequel sont intégrés couramment utilisés 16 x 16 bitmaps de *Resources-imagelis.bmp*. Cette liste de bitmap `SimpleProjectNode` `ImageHandler.ImageList`est mis à la disposition de as . `SimpleProjectNode`joint le bitmap de nœud de projet à la liste. Le décalage du bitmap de nœud de projet dans la liste `ImageIndex` d’image est mis en cache pour une utilisation ultérieure comme valeur de la propriété publique. Visual Studio utilise cette propriété pour déterminer quelle bitmap afficher comme icône de nœud de projet.

## <a name="test-the-custom-project-node-icon"></a>Testez l’icône personnalisée du nœud de projet
 Testez votre usine de projet pour voir si elle crée une hiérarchie de projet qui a votre icône de nœud de projet personnalisé.

### <a name="to-test-the-custom-project-node-icon"></a>Pour tester l’icône du nœud de projet personnalisé

1. Commencez à débogage, et dans l’exemple expérimental créer un nouveau SimpleProject.

2. Dans le nouveau projet, notez que *SimpleProjectNode.bmp* est utilisé comme icône de nœud de projet.

     ![Nœud Projet simple - Nouveau projet](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjetNode")

3. Ouvrez *Program.cs* dans l’éditeur de code. Vous devriez voir le code source qui ressemble au code suivant.

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

     Notez que les paramètres du modèle $nameSpace$ et $className$ n’ont pas de nouvelles valeurs. Vous apprendrez à implémenter la substitution des paramètres du modèle dans la section suivante.

## <a name="substitute-template-parameters"></a>Paramètres de modèle de remplacement
 Dans une section antérieure, vous avez enregistré le `ProvideProjectFactory` modèle de projet avec Visual Studio en utilisant l’attribut. L’enregistrement du chemin d’un dossier de modèle de cette manière vous permet `ProjectNode.AddFileFromTemplate` d’activer la substitution de paramètres de modèle de base en dominant et en élargissant la classe. Pour plus d’informations, voir [Nouvelle génération de projet: Sous le capot, deuxième partie](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Maintenant, ajoutez du `AddFileFromTemplate` code de remplacement à la classe.

### <a name="to-substitute-template-parameters"></a>Pour remplacer les paramètres du modèle

1. Dans le dossier *SimpleProjectNode.cs,* ajoutez `using` la directive suivante.

   ```csharp
   using System.IO;
   ```

2. Remplacez `AddFileFromTemplate` la méthode en utilisant le code suivant.

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

3. Définissez un point d’arrêt `className` dans la méthode, juste après l’énoncé d’affectation.

   Les énoncés d’affectation déterminent les valeurs raisonnables d’un espace de nom et d’un nouveau nom de classe. Les `ProjectNode.FileTemplateProcessor.AddReplace` deux appels de méthode remplacent les valeurs de paramètres correspondantes en utilisant ces nouvelles valeurs.

## <a name="test-the-template-parameter-substitution"></a>Testez la substitution du paramètre du modèle
 Maintenant, vous pouvez tester la substitution de paramètres de modèle.

### <a name="to-test-the-template-parameter-substitution"></a>Pour tester la substitution de paramètre de modèle

1. Commencez à débogage, et dans l’exemple expérimental créer un nouveau SimpleProject.

2. L’exécution s’arrête `AddFileFromTemplate` au point d’arrêt de la méthode.

3. Examiner les valeurs `nameSpace` `className` et les paramètres.

   - `nameSpace`est donné la \<valeur de l’élément RootNamespace> dans le fichier de modèle de projet *'Templates’Projects’SimpleProject.myproj.* Dans ce cas, la valeur est `MyRootNamespace`.

   - `className`est donné la valeur du nom de fichier source de classe, sans l’extension du nom de fichier. Dans ce cas, le premier fichier à être copié au dossier de destination est *AssemblyInfo.cs*; par conséquent, la valeur `AssemblyInfo`de className est .

4. Retirez le point d’arrêt et appuyez sur **F5** pour continuer l’exécution.

    Visual Studio devrait terminer la création d’un projet.

5. Ouvrez *Program.cs* dans l’éditeur de code. Vous devriez voir le code source qui ressemble au code suivant.

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

    Notez que l’espace de nom est maintenant `MyRootNamespace` et le nom de classe est maintenant `Program`.

6. Démarrez le débogage du projet. Le nouveau projet devrait compiler, exécuter et afficher "Bonjour VSX!!!" dans la fenêtre de console.

    ![Commande de projet simple](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Félicitations ! Vous avez mis en place un système de projet géré de base.
