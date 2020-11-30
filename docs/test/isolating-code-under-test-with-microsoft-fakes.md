---
title: Isolation du code sous test avec Microsoft Fakes
description: Découvrez comment les substituts Microsoft vous aident à isoler le code que vous testez en remplaçant d’autres parties de l’application par des stubs ou des shims.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: aa1f0505d37059ce65da80fcf483473610cf2f6d
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329534"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Isoler du code testé avec Microsoft Fakes

Microsoft Fakes vous permet d’isoler le code que vous testez en remplaçant d’autres parties de l’application par des *stubs* ou des *shims*. Ce sont de petits segments de code qui sont sous le contrôle de vos tests. En isolant votre code pour les tests, vous savez que si le test échoue, la cause réside dans le code et pas ailleurs. Les stubs et les shims vous permettent également de tester votre code même si d'autres parties de votre application ne fonctionnent pas encore.

Microsoft Fakes est disponible en deux versions :

- Un [stub](#get-started-with-stubs) remplace une classe par un petit substitut qui implémente la même interface.  Pour utiliser les stubs, vous devez concevoir votre application afin que chaque composant dépende uniquement des interfaces, et non pas d'autres composants. (Par « composant » nous entendons une classe ou un groupe de classes conçues et mises à jour ensemble et généralement contenues dans un assembly.)

- Un [shim](#get-started-with-shims) modifie le code compilé de votre application au moment de l’exécution pour qu’elle exécute le code shim que votre test fournit au lieu de faire un appel de méthode spécifié. Les shims peuvent être utilisés pour remplacer les appels aux assemblys que vous ne pouvez pas modifier, par exemple les assemblys .NET.

![Fakes remplace les autres composants](../test/media/fakes-2.png)

**Configuration requise**

- Visual Studio Enterprise
- Un projet .NET Framework
::: moniker range=">=vs-2019"
- La prise en charge des projets de type .NET Core et SDK est prévisualisée dans Visual Studio 2019 Update 6, et est activée par défaut dans Update 8. Pour plus d’informations, consultez [Microsoft Resubstituts for .net Core and SDK-style Projects](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

> [!NOTE]
> - Le profilage avec Visual Studio n’est pas disponible pour les tests qui utilisent Microsoft Fakes.

## <a name="choose-between-stub-and-shim-types"></a>Choisir entre les types stub et shim
En général, vous considérez un projet Visual Studio comme un composant, car vous développez et mettez à jour ces classes simultanément. Vous pouvez envisager d'utiliser des stubs et des shims pour les appels que le projet effectue en direction d'autres projets de votre solution ou d'autres assemblys que le projet référence.

En règle générale, utilisez des stubs pour les appels dans votre solution Visual Studio et des shims pour les appels vers d'autres assemblys référencés. En effet, dans votre propre solution, il est conseillé de découpler les composants en définissant les interfaces de la façon requise par l'opération stub. Toutefois, les assemblys externes tels que les *System.dll* ne sont généralement pas fournis avec des définitions d’interface distinctes. vous devez donc utiliser des shims à la place.

Les autres éléments à prendre en compte sont :

**Niveau de performance.** Les shims s'exécutent plus lentement, car ils réécrivent votre code au moment de l'exécution. Les stubs ne subissent pas cette surcharge de performances et sont aussi rapides que les méthodes virtuelles.

**Méthodes statiques, types sealed.** Vous pouvez uniquement utiliser les stubs pour implémenter les interfaces. Par conséquent, les types stub ne peuvent pas être utilisés pour les méthodes statiques, les méthodes non virtuelles, les méthodes virtuelles sealed, les méthodes dans les types sealed, etc.

**Types internes.** Les stubs et les shims peuvent être utilisés avec les types internes qui sont rendus accessibles à l'aide de l'attribut d'assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.

**Méthodes privées.** Les shims peuvent remplacer les appels aux méthodes privées si tous les types dans la signature de méthode sont visibles. Les stubs peuvent uniquement remplacer des méthodes visibles.

**Interfaces et méthodes abstraites.** Les stubs fournissent des implémentations d'interfaces et de méthodes abstraites qui peuvent être utilisées lors du test. Les shims ne peuvent pas instrumenter les interfaces ni les méthodes abstraites, car ils n’ont pas de corps de méthode.

En général, nous vous conseillons d'utiliser des types stub pour isoler des dépendances dans votre base de code. Pour cela, masquez les composants derrière les interfaces. Les types shim peuvent être utilisés pour isoler des composants tiers qui ne fournissent pas d'API pouvant être testée.

## <a name="get-started-with-stubs"></a>Bien démarrer avec les stubs
Pour obtenir une description détaillée, consultez [Utilisation de stubs pour isoler des parties de votre application les unes des autres pour des tests unitaires](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Injecter des interfaces**

     Pour utiliser les stubs, vous devez écrire le code que vous souhaitez tester de telle sorte qu'il ne mentionne pas explicitement les classes d'un autre composant de votre application. Par « composant » nous entendons une ou plusieurs classes développées et mises à jour ensemble et généralement contenues dans un projet Visual Studio. Les variables et les paramètres doivent être déclarés à l'aide d'interfaces et les instances des autres composants doivent être passées ou créées à l'aide d'une fabrique. Par exemple, si StockFeed est une classe dans un autre composant de l'application, le résultat est incorrect :

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Au lieu de cela, définissez une interface qui peut être implémentée par l'autre composant, et qui peut également être implémentée par un stub à des fins de test :

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Ajouter un assembly Fakes**

   1. Dans **Explorateur de solutions**, 
       - Pour un projet de .NET Framework plus ancien (style non-SDK), développez le nœud **références** de votre projet de test unitaire.
       ::: moniker range=">=vs-2019"
       - Pour un projet de type SDK ciblant .NET Framework ou .NET Core, développez le nœud **dépendances** pour trouver l’assembly que vous souhaitez falsifier sous **assemblys**, **projets** ou **packages**.
       ::: moniker-end
       - Si vous utilisez Visual Basic, sélectionnez **Afficher tous les fichiers** dans la barre d’outils **Explorateur de solutions** pour afficher le nœud **références** .
   2. Sélectionnez l’assembly qui contient les définitions de classe pour lesquelles vous souhaitez créer des shims. Par exemple, si vous souhaitez shim **DateTime**, sélectionnez **System.dll**.

   3. Dans le menu contextuel, choisissez **Ajouter un assembly Fakes**.

3. Dans vos tests, construisez les instances du stub et fournissez le code pour ses méthodes :

    ```csharp
    [TestClass]
    class TestStockAnalyzer
    {
        [TestMethod]
        public void TestContosoStockPrice()
        {
          // Arrange:

            // Create the fake stockFeed:
            IStockFeed stockFeed =
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                     {
                         // Define each method:
                         // Name is original name + parameter types:
                         GetSharePriceString = (company) => { return 1234; }
                     };

            // In the completed application, stockFeed would be a real one:
            var componentUnderTest = new StockAnalyzer(stockFeed);

          // Act:
            int actualValue = componentUnderTest.GetContosoPrice();

          // Assert:
            Assert.AreEqual(1234, actualValue);
        }
        ...
    }
    ```

    ```vb
    <TestClass()> _
    Class TestStockAnalyzer

        <TestMethod()> _
        Public Sub TestContosoStockPrice()
            ' Arrange:
            ' Create the fake stockFeed:
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
            With stockFeed
                .GetSharePriceString = Function(company)
                                           Return 1234
                                       End Function
            End With
            ' In the completed application, stockFeed would be a real one:
            Dim componentUnderTest As New StockAnalyzer(stockFeed)
            ' Act:
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice
            ' Assert:
            Assert.AreEqual(1234, actualValue)
        End Sub
    End Class

    ```

    Ici, l'aspect le plus magique est la classe `StubIStockFeed`. Pour chaque interface de l'assembly référencé, le mécanisme Microsoft Fakes génère une classe stub. Le nom de la classe stub est dérivé du nom de l’interface, avec « `Fakes.Stub` » comme préfixe, et les noms des types de paramètres ajoutés.

    Les stubs sont également générés pour les accesseurs Get et les méthodes setter de propriétés, les événements et les méthodes génériques. Pour plus d’informations, consultez [Utilisation de stubs pour isoler des parties de votre application les unes des autres pour des tests unitaires](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Bien démarrer avec les shims
(Pour obtenir une description détaillée, consultez [Utilisation de shims pour isoler votre application des autres assemblys pour des tests unitaires](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md))

Supposons que votre composant contienne des appels à `DateTime.Now` :

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Pendant le test, placez un shim sur la propriété `Now`, car la vraie version retourne incommodément une valeur différente à chaque appel.

Pour utiliser des shims, vous ne devez pas modifier le code de l’application ni l’écrire d’une façon particulière.

1. **Ajouter un assembly Fakes**

     Dans **Explorateur de solutions**, ouvrez les références de votre projet de test unitaire et sélectionnez la référence à l’assembly qui contient la méthode que vous souhaitez falsifier. Dans cet exemple, la classe `DateTime` se trouve dans *System.dll*.  Pour afficher les références dans un projet Visual Basic, choisissez **Afficher tous les fichiers**.

     Choisissez **Ajouter un assembly Fakes**.

2. **Insérer un shim dans ShimsContext**

    ```csharp
    [TestClass]
    public class TestClass1
    {
            [TestMethod]
            public void TestCurrentYear()
            {
                int fixedYear = 2000;

                // Shims can be used only in a ShimsContext:
                using (ShimsContext.Create())
                {
                  // Arrange:
                    // Shim DateTime.Now to return a fixed date:
                    System.Fakes.ShimDateTime.NowGet =
                    () =>
                    { return new DateTime(fixedYear, 1, 1); };

                    // Instantiate the component under test:
                    var componentUnderTest = new MyComponent();

                  // Act:
                    int year = componentUnderTest.GetTheCurrentYear();

                  // Assert:
                    // This will always be true if the component is working:
                    Assert.AreEqual(fixedYear, year);
                }
            }
    }
    ```

    ```vb
    <TestClass()> _
    Public Class TestClass1
        <TestMethod()> _
        Public Sub TestCurrentYear()
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
                Dim fixedYear As Integer = 2000
                ' Arrange:
                ' Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet = _
                    Function() As DateTime
                        Return New DateTime(fixedYear, 1, 1)
                    End Function

                ' Instantiate the component under test:
                Dim componentUnderTest = New MyComponent()
                ' Act:
                Dim year As Integer = componentUnderTest.GetTheCurrentYear
                ' Assert:
                ' This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year)
            End Using
        End Sub
    End Class
    ```

    Les noms de classe de shim sont obtenus en ajoutant le préfixe `Fakes.Shim` au nom de type d'origine. Les noms de paramètres sont ajoutés au nom de la méthode. (Vous ne devez ajouter aucune référence d’assembly à System.Fakes)

L'exemple précédent utilise un shim pour une méthode statique. Pour utiliser un shim pour une méthode d'instance, écrivez `AllInstances` entre le nom du type et le nom de la méthode :

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Il n’existe aucun assembly « System.IO.Fakes » à référencer. L'espace de noms est généré par le processus de création de shim. Toutefois, vous pouvez utiliser « using » ou « Import » de la façon habituelle.)

Vous pouvez également créer des shims pour des instances spécifiques, des constructeurs et des propriétés. Pour plus d’informations, consultez [Utilisation de shims pour isoler votre application des autres assemblys pour des tests unitaires](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="using-microsoft-fakes-in-the-ci"></a>Utilisation de substituts Microsoft dans l’intégration continue

### <a name="microsoft-fakes-assembly-generation"></a>Microsoft simule la génération d’assembly
Étant donné que les substituts de Microsoft requièrent Visual Studio Enterprise, la génération d’assemblys substituts nécessite que vous génériez votre projet à l’aide de la [tâche de génération Visual Studio](/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops).

::: moniker range=">=vs-2019"
> [!NOTE]
> Une alternative à cela consiste à vérifier vos assemblys de simulation dans l’élément de configuration et à utiliser la [tâche MSBuild](../msbuild/msbuild-task.md?view=vs-2019). Dans ce cas, vous devez vous assurer que vous disposez d’une référence d’assembly à l’assembly substituts généré dans votre projet de test, similaire à l’extrait de code suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <ItemGroup>
        <Reference Include="FakesAssemblies\System.Fakes.dll">
    </ItemGroup>
</Project>
```

Cette référence doit être ajoutée dans des projets de type SDK spécifiques manuellement (.NET Core et .NET Framework), car nous avons déplacé vers des références d’assembly qui ajoutent implicitement à votre projet de test. Si vous suivez cette méthode, vous devez vous assurer que l’assembly de simulations est mis à jour lors de la modification de l’assembly parent.
::: moniker-end

### <a name="running-microsoft-fakes-tests"></a>Exécution de tests de simulation Microsoft
Tant que les assemblys simulés par Microsoft sont présents dans le `FakesAssemblies` répertoire configuré (valeur par défaut `$(ProjectDir)FakesAssemblies` ), vous pouvez exécuter des tests à l’aide de la [tâche VSTest](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops).

::: moniker range=">=vs-2019"
Tests distribués avec la [tâche VSTest](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops) les projets .net core à l’aide de Microsoft simulations nécessitent Visual Studio 2019 Update 9 preview `20201020-06` et versions ultérieures.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="transitioning-your-net-framework-test-projects-that-use-microsoft-fakes-to-sdk-style-net-framework-or-net-core-projects"></a>Transition de vos projets de test .NET Framework qui utilisent les substituts Microsoft aux projets .NET Framework ou .NET Core de type SDK
Vous aurez besoin de modifications minimes dans votre .NET Framework configurer les substituts Microsoft pour passer à .NET Core. Les cas que vous devez prendre en compte sont les suivants :
- Si vous utilisez un modèle de projet personnalisé, vous devez vous assurer qu’il s’agit d’un kit de développement logiciel (SDK) et qu’il est généré pour un Framework cible compatible.
- Certains types existent dans des assemblys différents dans .NET Framework et .net Core (par exemple, `System.DateTime` existe dans `System` / `mscorlib` dans .NET Framework et dans `System.Runtime` dans .net Core), et dans ces scénarios, vous devez modifier l’assembly qui est falsifié.
- Si vous disposez d’une référence d’assembly à un assembly et à un projet de test, vous pouvez voir un avertissement de génération concernant une référence manquante semblable à la suivante :
  ```
  (ResolveAssemblyReferences target) ->
  warning MSB3245: Could not resolve this reference. Could not locate the assembly "AssemblyName.Fakes". Check to make sure the assembly exists on disk.
  If this reference is required by your code, you may get compilation errors.
  ```
  Cet avertissement est dû au fait que les modifications nécessaires dans la génération de simulation peuvent être ignorées. Elle peut être évitée en supprimant la référence d’assembly du fichier projet, car nous les ajoutons à présent implicitement pendant la génération.
::: moniker-end

## <a name="microsoft-fakes-support"></a>Prise en charge des substituts Microsoft 
### <a name="microsoft-fakes-in-older-projects-targeting-net-framework-non-sdk-style"></a>Microsoft simule dans des projets plus anciens ciblant .NET Framework (style non-SDK).
- La génération d’assembly de simulation Microsoft est prise en charge dans Visual Studio Enterprise 2015 et versions ultérieures.
- Les tests de simulation Microsoft peuvent s’exécuter avec tous les packages NuGet Microsoft. TestPlatform disponibles.
- La couverture du code est prise en charge pour les projets de test utilisant des substituts Microsoft dans Visual Studio Enterprise 2015 et versions ultérieures.

### <a name="microsoft-fakes-in-sdk-style-net-framework-and-net-core-projects"></a>Microsoft simule dans les projets de .NET Framework de style SDK et .NET Core
- Microsoft simule la génération d’assembly prévisualisée dans Visual Studio Enterprise 2019 Update 6 et est activée par défaut dans Update 8.
- Microsoft simule des tests pour les projets qui ciblent .NET Framework peuvent s’exécuter avec tous les packages NuGet Microsoft. TestPlatform disponibles.
- Microsoft simule des tests pour les projets qui ciblent .NET Core peut s’exécuter avec les packages NuGet Microsoft. TestPlatform avec les versions [16.8.0-Preview-20200921-01](https://www.nuget.org/packages/Microsoft.TestPlatform/16.8.0-preview-20200921-01) et ultérieures.
- La couverture du code est prise en charge pour les projets de test ciblant .NET Framework à l’aide des substituts Microsoft dans Visual Studio Enterprise version 2015 et ultérieure.
- La prise en charge de la couverture du code pour les projets de test ciblant .NET Core à l’aide de Microsoft simulation est en cours de développement


## <a name="in-this-section"></a>Dans cette section
[Utiliser des stubs pour isoler des parties de votre application les unes des autres pour des tests unitaires](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Utiliser des shims pour isoler votre application des autres assemblys pour des tests unitaires](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Génération, compilation de code et conventions d’affectation de noms dans Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
