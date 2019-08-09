---
title: Exécuter des tests unitaires sur des extensions UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5aeeb8bf9ec70a7288316c8b4c6baa337c232621
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871725"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Exécuter des tests unitaires sur des extensions UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour préserver la stabilité de votre code au fil des modifications successives, nous vous recommandons d’écrire des tests unitaires et de les exécuter dans le cadre d’un processus de génération normal. Pour plus d’informations, consultez [Tests unitaires sur votre code](../test/unit-test-your-code.md). Pour configurer des tests pour les extensions de modélisation Visual Studio, vous avez besoin de certaines informations clés. En résumé :

- [Configuration d’un test unitaire pour les extensions VSIX](#Host)

   Exécutez les tests avec l’adaptateur hôte IDE VS. Faites précéder chaque méthode de test du préfixe `[HostType("VS IDE")]`. Cet adaptateur hôte démarre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pendant l’exécution de vos tests.

- [Accès à DTE et ModelStore](#DTE)

   En principe, vous serez amené à ouvrir un modèle et ses diagrammes et à accéder à `IModelStore` dans l’initialisation du test.

- [Ouverture d’un diagramme de modèle](#Opening)

   Vous pouvez effectuer un cast de `EnvDTE.ProjectItem` vers et à partir de `IDiagramContext`.

- [Exécution des modifications dans le thread d’interface utilisateur](#UiThread)

   Les tests qui apportent des modifications au magasin de modèles doivent être exécutés dans le thread d’interface utilisateur. Pour cela, vous pouvez utiliser `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` .

- [Test de commandes, de mouvements et d’autres composants MEF](#MEF)

   Pour tester des composants MEF, vous devez connecter explicitement leurs propriétés importées à des valeurs.

  Ces points sont développés dans les sections suivantes.

  Vous trouverez un exemple d’extension UML ayant fait l’objet de tests unitaires dans la galerie d’exemples de code à la page [UML – Entrée rapide avec du texte](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a).

## <a name="requirements"></a>Configuration requise
 Consultez [Spécifications](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="Host"></a>Configuration d’un test unitaire pour les extensions VSIX
 Les méthodes contenues dans vos extensions de modélisation fonctionnent généralement avec un diagramme déjà ouvert. Les méthodes utilisent des importations MEF telles que **IDiagramContext** et **ILinkedUndoContext**. Votre environnement de test doit configurer ce contexte avant d’entreprendre l’exécution des tests.

#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Pour configurer un test unitaire qui s’exécute dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Créez le projet d’extension UML et le projet de test unitaire.

    1. **Projet d’extension UML.** En règle générale, vous le créez à l’aide des modèles de projet de commande, de mouvement ou de validation. Par exemple, consultez [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

    2. **Projet de test unitaire.** Pour plus d’informations, consultez [Tests unitaires sur votre code](../test/unit-test-your-code.md).

2. Créez une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui contient un projet de modélisation UML. Vous utiliserez cette solution comme état initial de vos tests. Elle doit être distincte de la solution dans laquelle vous écrivez l’extension UML et ses tests unitaires. Pour plus d’informations, consultez [créer des projets et des diagrammes de modélisation UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

3. **Dans le projet d’extension UML**, modifiez le fichier .csproj en mode texte et assurez-vous que les lignes suivantes indiquent `true`:

    ```
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>
    ```

     Pour modifier le fichier .csproj en mode texte, choisissez **Décharger le projet** dans le menu contextuel du projet dans l’Explorateur de solutions. Choisissez ensuite **Modifier ….csproj**. Une fois le texte modifié, choisissez **Recharger le projet**.

4. Dans votre projet d’extension UML, ajoutez la ligne suivante à **Properties\AssemblyInfo.cs**. Cela permet aux tests unitaires d’accéder aux méthodes que vous voulez tester :

    ```csharp
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
    ```

5. **Dans le projet de test unitaire**, ajoutez les références d’assembly suivantes :

    - *Votre projet d’extension UML*

    - **EnvDTE.dll**

    - **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**

    - **Microsoft.VisualStudio.ComponentModelHost.dll**

    - **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**

    - **Microsoft.VisualStudio.Uml.Interfaces.dll**

    - **Microsoft.VSSDK.TestHostFramework.dll**

6. Préfixez l’attribut `[HostType("VS IDE")]` à chaque méthode de test, y compris les méthodes d’initialisation.

     Le test s’exécutera ainsi dans une instance expérimentale de Visual Studio.

## <a name="DTE"></a>Accès à DTE et ModelStore
 Écrivez une méthode pour ouvrir un projet de modélisation dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En règle générale, vous ouvrez une solution une seule fois dans chaque série de tests. Pour exécuter la méthode une seule fois, préfixez la méthode avec l’attribut `[AssemblyInitialize]` . N’oubliez pas que vous avez aussi besoin de l’attribut [HostType("VS IDE")] dans chaque méthode de test.  Par exemple :

```csharp
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;

namespace UnitTests
{
  [TestClass]
  public static class TestSetup
  {

    // Location of a VS Solution that defines an initial state for your tests:
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";
    // Name of a modeling project within the test solution:
    private const string testModelingProjectName = "MyTestModel";

    // Make Solution and IModelStore available to test methods:
    public static Solution ModelSolution = null;
    public static IModelingProject ModelingProject = null;
    public static IModelStore ModelStore = null;

    // This method will be performed once to initialize tests for this assembly:
    [AssemblyInitialize]
    [HostType("VS IDE")]
    public static void OpenTestModelingProject(TestContext testContext)
    {
      // To make sure that we always start the tests in the same state,
      // copy the test solution from a read-only directory:
      // TODO: copy test solution folder.

      // Open a solution that is the initial state for your tests:
      ModelSolution = VsIdeTestHostContext.Dte.Solution;
      ModelSolution.Open(testSolutionFilePath);

      // Find the ModelingProject and IModelStore:
      foreach (Project project in ModelSolution.Projects)
      {
        // https://msdn.microsoft.com/library/ee791691.aspx
        ModelingProject = project as IModelingProject;
        if (ModelingProject != null)
        {
          // This is a modeling project.
          ModelStore = ModelingProject.Store;
          break;
        }
        // else this is another kind of project.
      }

      Assert.IsNotNull(ModelSolution, "VS solution not found");
      Assert.IsNotNull(ModelStore, "Modeling store not found");
    }
    [AssemblyCleanup]
    public static void RemoveTestSolution ()
    {
      // TODO: Remove copied test solution directory.
    }
  }
}

```

 Si une instance de <xref:EnvDTE.Project?displayProperty=fullName> représente un projet de modélisation, vous pouvez effectuer un cast vers et à partir de [IModelingProject](/previous-versions/ee789474(v=vs.140)).

## <a name="Opening"></a>Ouverture d’un diagramme de modèle
 Pour chaque test ou classe de tests, vous pouvez généralement travailler avec un diagramme ouvert. L’exemple suivant utilise l’attribut `[ClassInitialize]` , qui exécute cette méthode avant les autres méthodes de cette classe de tests. Encore une fois, n’oubliez pas que l’attribut [HostType("VS IDE")] est également nécessaire dans chaque méthode de test :

```csharp
//
private IDiagram diagram;
// This class contains unit tests:
[TestClass]
public class MyTestClass
{
  // Map filenames to open diagram files:
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();

  // This method will be called once for this test class:
  [ClassInitialize]
  [HostType("VS IDE")]
  public static void TestClassInitialize(TestContext testContext)
  {
    // Open all the diagrams in the model:
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)
    {
      // Get the filename of the principal file (not the .layout subsidiary):
      string fileName = item.FileNames[0];
      // If this is a model diagram file, it can be cast to IDiagramContext:
      IDiagramContext modelingItem = item as IDiagramContext;
      if (modelingItem != null)
      {
        IDiagram diagram = modelingItem.CurrentDiagram;
        if (diagram == null)
        {
          // Diagram is closed. Open it:
          item.Open().Activate();
          diagram = modelingItem.CurrentDiagram;
        }
        diagrams[fileName] = diagram;
      }
      // else item is not a model diagram.
    }
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");
  }
// Insert test methods here ...
}

```

## <a name="UiThread"></a>Effectuer des modifications de modèle dans le thread d’interface utilisateur
 Si vos tests ou les méthodes testées apportent des modifications au magasin de modèles, vous devez les exécuter dans le thread d’interface utilisateur. À défaut, vous risquez d’obtenir une exception `AccessViolationException`. Incorporez le code de la méthode de test dans un appel à Invoke :

```
using System.Windows.Forms;
using Microsoft.VSSDK.Tools.VsIdeTesting;
 ...
    [TestMethod]
    [HostType("VS IDE")]
    public void MyTest1()
    {
      // Store operations must run in the UI thread:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        SetupTestState(TestSetup.ModelStore, diagram);
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);
      });
    }
```

## <a name="MEF"></a>Test de commande, de mouvement et d’autres composants MEF
 Les composants MEF utilisent des déclarations de propriétés qui contiennent l’attribut `[Import]` et dont les valeurs sont définies par leurs hôtes. Parmi ces propriétés figurent généralement IDiagramContext, SVsServiceProvider et ILinkedUndoContext. Quand vous testez une méthode qui utilise l’une de ces propriétés, vous devez définir leurs valeurs avant d’exécuter la méthode en question. Par exemple, si vous avez écrit une extension de commande qui ressemble à ce code :

```

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class MyCommand : ICommandExtension
  {
    [Import] IDiagramContext context { get; set; }
    [Import]
Microsoft.VisualStudio.Shell.SVsServiceProvider
serviceProvider {get;set;}
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      DoCommand();
    }
    private void DoCommand()
    {
      IDiagram diagram = context.CurrentDiagram;
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))
      { ... }}}

```

 Vous pouvez alors définir les propriétés importées comme suit :

```

using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ComponentModelHost;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;
...
    [TestMethod]
    [HostType("VS IDE")]
    public void Test1()
    {
      // Create an instance of the class under test:
      MyCommand myCommand = new MyCommand();
      // Get the components service:
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
        .GetService(typeof(SComponentModel)) as IComponentModel;
      // Set the imported properties of the instance under test:
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);
      // Call method(s) under test:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        myCommand.DoCommand();
      });
...}
```

 Si vous voulez tester une méthode qui prend une propriété importée comme paramètre, vous pouvez importer la propriété dans votre classe de test et appliquer `SatisfyImportsOnce` à l’instance de test. Par exemple :

```

using System.ComponentModel.Composition;
...
  [TestClass]
  public class MyTestClass
  {
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }

    // Called before each test method:
    [TestInitialize, HostType("VS IDE")]
    public void TestInitializer()
    {
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
            .GetService(typeof(SComponentModel)) as IComponentModel;
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(this);
    }
    [TestMethod, HostType("VS IDE")]
    public void Test2()
    {
     UIThreadInvoker.Invoke((System.Action)delegate()
      {
      // Pass context items to class under test:
      Class1 item1 = new Class1(this.linkedUndoContext);
      item1.Method1(); // Can use linkedUndoContext
     });
   }
}

```

 Dans cet exemple, les deux attributs de chaque méthode de test sont combinés en une seule ligne pour des raisons pratiques.

## <a name="access-from-tests-to-private-methods-and-variables"></a>Accès à des méthodes et variables privées à partir de tests
 Vous pouvez parfois être amené à tester une méthode privée ou à vérifier l’état d’un champ privé avant et après l’exécution d’une méthode testée. Cela pose problème dans la mesure où les tests se trouvent dans un assembly distinct par rapport aux classes testées. Plusieurs tactiques sont envisageables, notamment celles-ci :

 Testez uniquement à l’aide d’éléments publics et internes écrivez vos tests afin qu’ils utilisent uniquement des classes et des membres publics (ou internes). Il s’agit de la meilleure approche. Vos tests continueront de fonctionner même si vous refactorisez l’implémentation interne de l’assembly testé. En appliquant les mêmes tests avant et après les modifications, vous êtes assuré que vos modifications n’altéreront pas le comportement de l’assembly.

 Pour que cela soit possible, vous serez peut-être amené à restructurer votre code. Par exemple, vous devrez peut-être séparer certaines méthodes dans une autre classe.

 En vous penchant sérieusement sur cette approche, vous trouverez souvent que votre code est plus facile à lire et à modifier et moins sujet aux erreurs quand des modifications s’avèrent nécessaires.

 Vous pouvez permettre à l’assembly de test d’accéder aux éléments internes en ajoutant un attribut dans **Properties\AssemblyInfo.cs** dans le projet à tester :

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Définir une interface de test définissez une interface qui comprend à la fois les membres publics d’une classe à tester et les propriétés et méthodes supplémentaires pour les membres privés que vous souhaitez que les tests puissent utiliser. Ajoutez cette interface au projet à tester. Par exemple :

```csharp
internal interface MyClassTestInterface {
  void PublicMethod1();
  string PublicProperty1 { get; }
  string privateField1_Accessor { get; }
  int privateMethod1_Accessor (string p1);
 }
```

 Ajoutez les méthodes à la classe à tester pour implémenter les méthodes d’accesseur explicitement. Conservez ces méthodes supplémentaires en dehors de la classe principale en les écrivant dans une définition de classe partielle dans un fichier distinct. Par exemple :

```csharp
partial public class MyClass
{
  string MyClassTestInterface.privateField1_Accessor
  { get { return privateField1; } }
  int MyClassTestInterface.privateMethod1_Accessor (string p1)
  { return privateMethod1(p1); }
}

```

 Autorisez l’assembly de test à utiliser les interfaces de test en ajoutant cet attribut à l’assembly que vous testez :

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Dans les méthodes de test unitaire, utilisez l’interface de test. Par exemple :

```csharp
MyClassTestInterface testInstance = new MyClass();
testInstance.PublicMethod1();
Assert.AreEqual("hello", testInstance.privateField1_Accessor);
```

 Définir des accesseurs à l’aide de la réflexion il s’agit de la méthode la moins recommandée. Les anciennes versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proposaient un utilitaire qui créait automatiquement une méthode d’accesseur pour chaque méthode privée. Malgré son caractère pratique, l’expérience nous a démontré qu’il avait tendance à aboutir à des tests unitaires très fortement couplés à la structure interne de l’application qu’ils testent. Cela conduit à du travail supplémentaire quand les exigences ou l’architecture évoluent, les tests devant être modifiés en même temps que l’implémentation. De même, les hypothèses erronées dans la conception de l’implémentation sont également intégrées aux tests, si bien que les tests ne trouvent pas d’erreurs.

## <a name="see-also"></a>Voir aussi
 [Anatomie d’un test unitaire](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [UML – entrée rapide à l’aide de texte](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)
