---
title: Création d’un système de projet de base, partie 1 | Microsoft Docs
description: Découvrez comment créer un type de projet nommé extension. MyProj. Dans Visual Studio, les projets sont des conteneurs utilisés pour organiser les fichiers de code source et d’autres éléments multimédias.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 15d28ff154629d07c643430b210d6106ac99978c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089431"
---
# <a name="create-a-basic-project-system-part-1"></a>Créer un système de projet de base, partie 1
Dans Visual Studio, les projets sont les conteneurs que les développeurs utilisent pour organiser les fichiers de code source et d’autres ressources. Les projets apparaissent en tant qu’enfants des solutions dans le **Explorateur de solutions**. Les projets vous permettent d’organiser, de générer, de déboguer et de déployer du code source et de créer des références à des services Web, des bases de données et d’autres ressources.

 Les projets sont définis dans les fichiers projet, par exemple un fichier *. csproj* pour un projet Visual C#. Vous pouvez créer votre propre type de projet avec votre propre extension de nom de fichier projet. Pour plus d’informations sur les types de projets, consultez [types de projets](../extensibility/internals/project-types.md).

> [!NOTE]
> Si vous devez étendre Visual Studio avec un type de projet personnalisé, nous vous recommandons vivement de tirer parti du [système de projet Visual Studio](https://github.com/Microsoft/VSProjectSystem) (vsps) qui offre un certain nombre d’avantages par rapport à la création d’un système de projet à partir de zéro :
>
> - Intégration plus facile.  Même un système de projet de base nécessite des dizaines de milliers de lignes de code.  L’utilisation de vsp réduit le coût d’intégration à quelques clics avant que vous ne soyez prêt à le personnaliser à vos besoins.
> - Facilité de maintenance.  En tirant parti de VSPS, vous devez uniquement gérer vos propres scénarios.  Nous prenons en charge l’entretien de l’ensemble de l’infrastructure du système de projet.
>
>   Si vous avez besoin de cibler des versions de Visual Studio antérieures à Visual Studio 2013, vous ne pourrez pas utiliser les éléments VSPS dans une extension Visual Studio.  Si tel est le cas, cette procédure pas à pas est un bon point de départ.

 Cette procédure pas à pas vous montre comment créer un type de projet avec l’extension de nom de fichier projet *. MyProj*. Cette procédure pas à pas emprunte le système de projet Visual C# existant.

> [!NOTE]
> Pour obtenir plus d’exemples de projets d’extension, consultez [exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 Cette procédure pas à pas explique comment accomplir ces tâches :

- Créez un type de projet de base.

- Créez un modèle de projet de base.

- Inscrivez le modèle de projet dans Visual Studio.

- Créez une instance de projet en ouvrant la boîte de dialogue **nouveau projet** , puis en utilisant votre modèle.

- Créez une fabrique de projets pour votre système de projet.

- Créez un nœud de projet pour votre système de projet.

- Ajoutez des icônes personnalisées pour le système de projet.

- Implémentez la substitution de paramètre de modèle de base.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

 Vous devez également télécharger le code source de l' [infrastructure de package managée pour les projets](https://github.com/tunnelvisionlabs/MPFProj10). Extrayez le fichier vers un emplacement accessible à la solution que vous allez créer.

## <a name="create-a-basic-project-type"></a>Créer un type de projet de base
 Créez un projet VSIX C# nommé **SimpleProject**. (**Fichier**  >  **Nouveau**  >  **Projet** , puis projet VSIX d’extensibilité **Visual C#**  >    >  ). Ajoutez un modèle d’élément de projet de package Visual Studio (sur le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter** un  >  **nouvel élément**, puis accédez à **extensibilité**  >  **package Visual Studio**). Nommez le fichier *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Création d’un modèle de projet de base
 À présent, vous pouvez modifier ce VSPackage de base pour implémenter le nouveau type de projet *. MyProj* . Pour créer un projet basé sur le type de projet *. MyProj* , Visual Studio doit connaître les fichiers, les ressources et les références à ajouter au nouveau projet. Pour fournir ces informations, placez les fichiers projet dans un dossier de modèle de projet. Quand un utilisateur utilise le projet *. MyProj* pour créer un projet, les fichiers sont copiés dans le nouveau projet.

### <a name="to-create-a-basic-project-template"></a>Pour créer un modèle de projet de base

1. Ajoutez trois dossiers au projet, l’un dans l’autre : *Templates\Projects\SimpleProject*. (Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **SimpleProject** , pointez sur **Ajouter**, puis cliquez sur **nouveau dossier**. Nommez le dossier *modèles*. Dans le dossier *modèles* , ajoutez un dossier nommé *projets*. Dans le dossier *projets* , ajoutez un dossier nommé *SimpleProject*.)

2. Dans le dossier *Templates\Projects\SimpleProject* , ajoutez un fichier image bitmap à utiliser comme icône nommée *SimpleProject. ico*. Lorsque vous cliquez sur **Ajouter**, l’éditeur d’icône s’ouvre.

3. Rendez l’icône différente. Cette icône s’affiche dans la boîte de dialogue **nouveau projet** plus loin dans la procédure pas à pas.

    ![Icône de projet simple](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Enregistrez l’icône et fermez l’éditeur d’icône.

5. Dans le dossier *Templates\Projects\SimpleProject* , ajoutez un élément de **classe** nommé *Program. cs*.

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
   > Il ne s’agit pas de la forme finale du code *Program. cs* . les paramètres de remplacement seront traités dans une étape ultérieure. Vous pouvez voir des erreurs de compilation, mais tant que le **BuildAction** du fichier est de type **contenu**, vous devez être en mesure de générer et d’exécuter le projet comme d’habitude.

7. Enregistrez le fichier .

8. Copiez le fichier *AssemblyInfo. cs* du dossier *Properties* dans le dossier *Projects\SimpleProject* .

9. Dans le dossier *Projects\SimpleProject* , ajoutez un fichier XML nommé *SimpleProject. MyProj*.

   > [!NOTE]
   > L’extension de nom de fichier pour tous les projets de ce type est *. MyProj*. Si vous souhaitez le modifier, vous devez le modifier partout où il est mentionné dans la procédure pas à pas.

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

12. Dans la fenêtre **Propriétés** , affectez à l' **action de génération** *AssemblyInfo. cs*, *Program. cs*, *SimpleProject. ico* et *SimpleProject. MyProj* la valeur **contenu**, puis affectez à la propriété **inclure dans VSIX** la **valeur true**.

    Ce modèle de projet décrit un projet Visual C# de base qui a à la fois une configuration de débogage et une configuration Release. Le projet comprend deux fichiers sources, *AssemblyInfo. cs* et *Program. cs*, et plusieurs références d’assembly. Lorsqu’un projet est créé à partir du modèle, la valeur ProjectGuid est automatiquement remplacée par un nouveau GUID.

    Dans **Explorateur de solutions**, le dossier de **modèles** développé doit se présenter comme suit :

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
 Vous devez indiquer à Visual Studio l’emplacement de votre dossier de modèles de projet. Pour ce faire, ajoutez un attribut à la classe VSPackage qui implémente la fabrique de projet afin que l’emplacement du modèle soit écrit dans le registre système lors de la génération du VSPackage. Commencez par créer une fabrique de projet de base qui est identifiée par un GUID de la fabrique de projet. Utilisez l' <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut pour connecter la fabrique de projet à la `SimpleProjectPackage` classe.

### <a name="to-create-a-basic-project-factory"></a>Pour créer une fabrique de projet de base

1. Créez des GUID pour votre fabrique de projets (dans le menu **Outils** , cliquez sur **créer un GUID**) ou utilisez celui de l’exemple suivant. Ajoutez les GUID à la `SimpleProjectPackage` classe près de la section avec le déjà défini `PackageGuidString` . Les GUID doivent être à la fois sous forme de GUID et sous forme de chaîne. Le code obtenu doit ressembler à l’exemple suivant.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Ajoutez une classe au dossier Top *SimpleProject* nommé *SimpleProjectFactory. cs*.

3. Ajoutez les directives using suivantes :

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Ajoutez un attribut GUID à la `SimpleProjectFactory` classe. La valeur de l’attribut est le nouveau GUID de la fabrique de projet.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Vous pouvez maintenant inscrire votre modèle de projet.

### <a name="to-register-the-project-template"></a>Pour inscrire le modèle de projet

1. Dans *SimpleProjectPackage. cs*, ajoutez un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attribut à la `SimpleProjectPackage` classe, comme suit.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Régénérez la solution et vérifiez qu’elle se génère sans erreur.

    La reconstruction inscrit le modèle de projet.

   Les paramètres `defaultProjectExtension` et `possibleProjectExtensions` sont définis sur l’extension de nom de fichier projet (*. MyProj*). Le `projectTemplatesDirectory` paramètre est défini sur le chemin d’accès relatif du dossier de *modèles* . Pendant la génération, ce chemin d’accès est converti en une version complète et ajouté au registre pour inscrire le système de projet.

## <a name="test-the-template-registration"></a>Tester l’inscription du modèle
 L’inscription du modèle indique à Visual Studio l’emplacement de votre dossier de modèles de projet afin que Visual Studio puisse afficher le nom et l’icône du modèle dans la boîte de dialogue **nouveau projet** .

### <a name="to-test-the-template-registration"></a>Pour tester l’inscription du modèle

1. Appuyez sur **F5** pour démarrer le débogage d’une instance expérimentale de Visual Studio.

2. Dans l’instance expérimentale, créez un nouveau projet de type de projet nouvellement créé. Dans la boîte de dialogue **nouveau projet** , vous devriez voir **SimpleProject** sous **modèles installés**.

   Vous avez maintenant une fabrique de projets inscrite. Toutefois, il ne peut pas encore créer un projet. Le package de projet et la fabrique de projets fonctionnent ensemble pour créer et initialiser un projet.

## <a name="add-the-managed-package-framework-code"></a>Ajouter le code Managed package Framework
 Implémentez la connexion entre le package de projet et la fabrique de projet.

- Importez les fichiers de code source de l’infrastructure de package managée.

    1. Déchargez le projet SimpleProject (dans **Explorateur de solutions**, sélectionnez le nœud du projet et, dans le menu contextuel, cliquez sur **décharger le projet**.) et ouvrez le fichier projet dans l’éditeur XML.

    2. Ajoutez les blocs suivants au fichier projet (juste au-dessus des \<Import> blocs). Définissez `ProjectBasePath` sur l’emplacement du fichier *ProjectBase. Files* dans le code de l’infrastructure de package managé que vous venez de télécharger. Vous devrez peut-être ajouter une barre oblique inverse au nom du chemin. Si ce n’est pas le cas, le projet peut ne pas trouver le code source de l’infrastructure de package managé.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > N’oubliez pas la barre oblique inverse à la fin du chemin d’accès.

    3. Rechargez le projet.

    4. Ajoutez des références aux assemblys suivants :

        - `Microsoft.VisualStudio.Designer.Interfaces`(dans *\<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Pour initialiser la fabrique de projet

1. Dans le fichier *SimpleProjectPackage. cs* , ajoutez la `using` directive suivante.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Dérivez la `SimpleProjectPackage` classe de `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Inscrire la fabrique de projets. Ajoutez la ligne suivante à la `SimpleProjectPackage.Initialize` méthode, juste après `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Implémentez la propriété abstract `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. Dans *SimpleProjectFactory. cs*, ajoutez la `using` directive suivante après les `using` directives existantes.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Dérivez la `SimpleProjectFactory` classe de `ProjectFactory` .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Ajoutez la méthode factice suivante à la `SimpleProjectFactory` classe. Vous allez implémenter cette méthode dans une section ultérieure.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Ajoutez le champ et le constructeur suivants à la `SimpleProjectFactory` classe. Cette `SimpleProjectPackage` référence est mise en cache dans un champ privé pour pouvoir être utilisée dans la définition d’un site de fournisseur de services.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Régénérez la solution et vérifiez qu’elle se génère sans erreur.

## <a name="test-the-project-factory-implementation"></a>Tester l’implémentation de la fabrique de projets
 Testez si le constructeur de votre implémentation de la fabrique de projet est appelé.

### <a name="to-test-the-project-factory-implementation"></a>Pour tester l’implémentation de la fabrique de projets

1. Dans le fichier *SimpleProjectFactory. cs* , définissez un point d’arrêt sur la ligne suivante dans le `SimpleProjectFactory` constructeur.

    ```csharp
    this.package = package;
    ```

2. Appuyez sur **F5** pour démarrer une instance expérimentale de Visual Studio.

3. Dans l’instance expérimentale, commencez à créer un nouveau projet. Dans la boîte de dialogue **nouveau projet** , sélectionnez le type de projet **SimpleProject** , puis cliquez sur **OK**. L’exécution s’interrompt au point d’arrêt.

4. Effacez le point d’arrêt et arrêtez le débogage. Étant donné que nous n’avons pas encore créé de nœud de projet, le code de création du projet lève toujours des exceptions.

## <a name="extend-the-projectnode-class"></a>Étendre la classe ProjectNode
 Vous pouvez désormais implémenter la `SimpleProjectNode` classe, qui dérive de la `ProjectNode` classe. La `ProjectNode` classe de base gère les tâches suivantes de création de projet :

- Copie le fichier de modèle de projet, *SimpleProject. MyProj*, dans le dossier du nouveau projet. La copie est renommée en fonction du nom entré dans la boîte de dialogue **nouveau projet** . La `ProjectGuid` valeur de la propriété est remplacée par un nouveau GUID.

- Parcourt les éléments MSBuild du fichier de modèle de projet, *SimpleProject. MyProj*, et recherche des `Compile` éléments. Pour chaque `Compile` fichier cible, copie le fichier dans le dossier du nouveau projet.

  La classe dérivée `SimpleProjectNode` gère ces tâches :

- Permet de créer ou de sélectionner des icônes pour les nœuds de projet et de fichier dans **Explorateur de solutions** .

- Permet de spécifier des substitutions de paramètre de modèle de projet supplémentaires.

### <a name="to-extend-the-projectnode-class"></a>Pour étendre la classe ProjectNode

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

   Cette `SimpleProjectNode` implémentation de classe a ces méthodes substituées :

- `ProjectGuid`, qui retourne le GUID de la fabrique de projet.

- `ProjectType`, qui retourne le nom localisé du type de projet.

- `AddFileFromTemplate`, qui copie les fichiers sélectionnés à partir du dossier de modèles dans le projet de destination. Cette méthode est également implémentée dans une section ultérieure.

  Le `SimpleProjectNode` constructeur, comme le `SimpleProjectFactory` constructeur, met en cache une `SimpleProjectPackage` référence dans un champ privé en vue d’une utilisation ultérieure.

  Pour connecter la `SimpleProjectFactory` classe à la `SimpleProjectNode` classe, vous devez instancier un nouveau `SimpleProjectNode` dans la `SimpleProjectFactory.CreateProject` méthode et le mettre en cache dans un champ privé en vue d’une utilisation ultérieure.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Pour connecter la classe de fabrique de projets et la classe de nœud

1. Dans le fichier *SimpleProjectFactory. cs* , ajoutez la `using` directive suivante :

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Remplacez la `SimpleProjectFactory.CreateProject` méthode en utilisant le code suivant.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Régénérez la solution et vérifiez qu’elle se génère sans erreur.

## <a name="test-the-projectnode-class"></a>Test de la classe ProjectNode
 Testez votre fabrique de projet pour voir si elle crée une hiérarchie de projet.

### <a name="to-test-the-projectnode-class"></a>Pour tester la classe ProjectNode

1. Appuyez sur **F5** pour démarrer le débogage. Dans l’instance expérimentale, créez un nouveau SimpleProject.

2. Visual Studio doit appeler votre fabrique de projet pour créer un projet.

3. Fermez l’instance expérimentale de Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Icône Ajouter un nœud de projet personnalisé
 L’icône du nœud de projet dans la section précédente est une icône par défaut. Vous pouvez le remplacer par une icône personnalisée.

### <a name="to-add-a-custom-project-node-icon"></a>Pour ajouter une icône de nœud de projet personnalisé

1. Dans le dossier **ressources** , ajoutez un fichier bitmap nommé *SimpleProjectNode.bmp*.

2. Dans les fenêtres **Propriétés** , réduisez l’image bitmap à 16 par 16 pixels. Rendez la bitmap distincte.

    ![Commande de projet simple](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. Dans la fenêtre **Propriétés** , remplacez l' **action de génération** de l’image bitmap par **ressource incorporée**.

4. Dans *SimpleProjectNode. cs*, ajoutez les `using` directives suivantes :

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Ajoutez le champ et le constructeur statiques suivants à la `SimpleProjectNode` classe.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Ajoutez la propriété suivante au début de la `SimpleProjectNode` classe.

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

   Pendant la construction statique, `SimpleProjectNode` récupère la bitmap du nœud de projet à partir des ressources de manifeste de l’assembly et la met en cache dans un champ privé en vue d’une utilisation ultérieure. Notez la syntaxe du chemin d’accès de l' <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> image. Pour afficher les noms des ressources de manifeste incorporées dans un assembly, utilisez la <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> méthode. Lorsque cette méthode est appliquée à l' `SimpleProject` assembly, les résultats doivent être les suivants :

- *SimpleProject. resources. Resources*

- *VisualStudio. Project. Resources*

- *SimpleProject. VSPackage. Resources*

- *Resources.imagelis.bmp*

- *Microsoft. VisualStudio. Project. DontShowAgainDialog. Resources*

- *Microsoft. VisualStudio. Project. SecurityWarningDialog. Resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Pendant la construction de l’instance, la `ProjectNode` classe de base charge *Resources.imagelis.bmp*, dans lesquelles sont incorporées des bitmaps 16 x 16 couramment utilisées à partir de *Resources\imagelis.bmp*. Cette liste de bitmaps est mise à la disposition de `SimpleProjectNode` sous `ImageHandler.ImageList` . `SimpleProjectNode` Ajoute la bitmap de nœud de projet à la liste. Le décalage de la bitmap du nœud de projet dans la liste d’images est mis en cache pour une utilisation ultérieure comme valeur de la `ImageIndex` propriété publique. Visual Studio utilise cette propriété pour déterminer l’image bitmap à afficher en tant qu’icône de nœud de projet.

## <a name="test-the-custom-project-node-icon"></a>Icône de test du nœud de projet personnalisé
 Testez votre fabrique de projet pour voir si elle crée une hiérarchie de projet qui a votre icône de nœud de projet personnalisé.

### <a name="to-test-the-custom-project-node-icon"></a>Pour tester l’icône du nœud de projet personnalisé

1. Démarrez le débogage et, dans l’instance expérimentale, créez un nouveau SimpleProject.

2. Dans le projet qui vient d’être créé, remarquez que *SimpleProjectNode.bmp* est utilisé comme icône de nœud de projet.

     ![Nœud Projet simple - Nouveau projet](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Ouvrez *Program.cs* dans l’éditeur de code. Vous devez voir le code source qui ressemble au code suivant.

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

     Notez que les paramètres de modèle $nameSpace $ et $className $ n’ont pas de nouvelles valeurs. Vous allez apprendre à implémenter la substitution de paramètre de modèle dans la section suivante.

## <a name="substitute-template-parameters"></a>Remplacer les paramètres du modèle
 Dans une section précédente, vous avez inscrit le modèle de projet avec Visual Studio à l’aide de l' `ProvideProjectFactory` attribut. L’inscription du chemin d’accès d’un dossier de modèle de cette manière vous permet d’activer la substitution de paramètre de modèle de base en substituant et en développant la `ProjectNode.AddFileFromTemplate` classe. Pour plus d’informations, consultez [nouvelle génération de projet : sous le capot, deuxième partie](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Ajoutez maintenant le code de remplacement à la `AddFileFromTemplate` classe.

### <a name="to-substitute-template-parameters"></a>Pour remplacer les paramètres de modèle

1. Dans le fichier *SimpleProjectNode. cs* , ajoutez la `using` directive suivante.

   ```csharp
   using System.IO;
   ```

2. Remplacez la `AddFileFromTemplate` méthode en utilisant le code suivant.

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

3. Définissez un point d’arrêt dans la méthode, juste après l' `className` instruction d’assignation.

   Les instructions d’assignation déterminent les valeurs raisonnables pour un espace de noms et un nouveau nom de classe. Les deux `ProjectNode.FileTemplateProcessor.AddReplace` appels de méthode remplacent les valeurs de paramètre de modèle correspondantes à l’aide de ces nouvelles valeurs.

## <a name="test-the-template-parameter-substitution"></a>Tester la substitution de paramètre de modèle
 Vous pouvez maintenant tester la substitution de paramètre de modèle.

### <a name="to-test-the-template-parameter-substitution"></a>Pour tester la substitution de paramètre de modèle

1. Démarrez le débogage et, dans l’instance expérimentale, créez un nouveau SimpleProject.

2. L’exécution s’arrête au point d’arrêt dans la `AddFileFromTemplate` méthode.

3. Examinez les valeurs des `nameSpace` `className` paramètres et.

   - `nameSpace` reçoit la valeur de l' \<RootNamespace> élément dans le fichier de modèle de projet *\Templates\Projects\SimpleProject\SimpleProject.MyProj* . Dans ce cas, la valeur est `MyRootNamespace`.

   - `className` reçoit la valeur du nom de fichier source de la classe, sans l’extension de nom de fichier. Dans ce cas, le premier fichier à copier dans le dossier de destination est *AssemblyInfo. cs*; par conséquent, la valeur de className est `AssemblyInfo` .

4. Supprimez le point d’arrêt et appuyez sur **F5** pour continuer l’exécution.

    Visual Studio doit terminer la création d’un projet.

5. Ouvrez *Program.cs* dans l’éditeur de code. Vous devez voir le code source qui ressemble au code suivant.

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

    Notez que l’espace de noms est maintenant `MyRootNamespace` et que le nom de la classe est maintenant `Program` .

6. Démarrez le débogage du projet. Le nouveau projet doit compiler, exécuter et afficher « Hello VSX !!! » dans la fenêtre de console.

    ![Commande de projet simple](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Félicitations ! Vous avez implémenté un système de projet managé de base.
