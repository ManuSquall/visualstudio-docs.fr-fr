---
title: Tests de couverture du code
ms.date: 09/18/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cd20de20279ea57bea4f829be03533bc43bfaa4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027062"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>Utiliser la couverture du code pour déterminer la quantité de code testé

Pour déterminer la proportion de code de votre projet qui sera réellement testée par des tests codés, par exemple des tests unitaires, recourez à la fonctionnalité de couverture du code de Visual Studio. Pour apporter une protection efficace contre les bogues, les tests doivent s'effectuer ou « couvrir » une proportion importante de votre code.

L'analyse de couverture du code peut être appliquée pour du code managé (CLI) et non managé (natif).

Vous pouvez avoir recours à la couverture du code lorsque vous exécutez des méthodes de test à l'aide de l'Explorateur de tests. La table des résultats affiche le pourcentage de code exécuté dans chaque assembly, classe et méthode. En outre, l'éditeur de code source vous indique quel code a été testé.

![Résultats de la couverture du code avec coloration](../test/media/codecoverage1.png)

## <a name="requirements"></a>Spécifications

La fonctionnalité de couverture du code n’est disponible que dans l’édition Visual Studio Enterprise.

## <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>Pour analyser la couverture du code sur les tests unitaires dans l'Explorateur de tests

1. Dans le menu **Test**, choisissez **Analyser la couverture du code**.

2. Pour voir les lignes qui ont été exécutées, choisissez ![Icône Afficher la coloration de la couverture du code](../test/media/codecoverage-showcoloringicon.png) **Afficher la coloration de la couverture du code**.

   Pour changer les couleurs ou utiliser des caractères gras, choisissez **Outils** > **Options** > **Environnement** > **Polices et couleurs** > **Afficher les paramètres de : Éditeur de texte**. Sous **Éléments affichés**, ajustez les éléments de couverture.

3. Si les résultats indiquent une couverture basse, recherchez les parties du code qui ne sont pas testées, puis élaborez d'autres tests pour les couvrir. Les équipes de développement visent généralement une couverture de code qui avoisine 80 %. Dans certaines situations, une couverture inférieure est acceptable. Par exemple, une couverture inférieure est acceptable lorsqu'un code est généré à partir d'un modèle standard.

> [!TIP]
> - Vérifiez que l’optimisation du compilateur est désactivée.
> - Si vous travaillez avec du code non managé (natif), utilisez une version Debug.
> - Vérifiez que vous générez des fichiers de symboles (.pdb) pour chaque assembly.

Si vous n’obtenez pas les résultats escomptés, consultez [Résoudre les problèmes liés à la couverture du code](../test/troubleshooting-code-coverage.md). N’oubliez pas de réexécuter la couverture du code après la mise à jour de votre code. Les résultats de couverture et la coloration du code ne sont pas automatiquement mis à jour après avoir la modification de votre code ou lorsque vous exécutez des tests.

## <a name="report-in-blocks-or-lines"></a>Rapport pour les blocs ou les lignes

La couverture du code est mesurée en *blocs*. Un bloc est un fragment de code avec un seul point d'entrée et de sortie.  Si le flux de contrôle du programme traverse un bloc pendant une série de tests, ce bloc est considéré comme couvert. Le nombre de fois où le bloc est utilisé n'a aucun effet sur le résultat.

Les résultats peuvent également être affichés en termes de lignes si vous choisissez **Ajouter/supprimer des colonnes** dans l’en-tête du tableau. Si la série de tests a testé tous les blocs de code dans n'importe quelle ligne de code, le résultat considère qu'il s'agit d'une ligne. Si une ligne contient des blocs de code qui ont été testés et d'autres blocs qui ne l'ont pas été, le résultat considère qu'il s'agit d'une ligne partielle.

Certains utilisateurs préfèrent un nombre de lignes, car les pourcentages correspondent mieux à la taille des fragments que vous voyez dans le code source. Un long bloc de calcul serait considéré comme un seul bloc même s'il occupe plusieurs lignes.

## <a name="manage-code-coverage-results"></a>Gérer les résultats de la couverture du code

La fenêtre **Résultats de la couverture du code** affiche généralement le résultat de la série la plus récente. Les résultats varient si vous modifiez les données de test ou si vous exécutez uniquement certains de vos tests chaque fois.

La fenêtre de couverture du code peut également être utilisée pour afficher les résultats précédents ou des résultats obtenus sur d'autres ordinateurs.

Vous pouvez fusionner les résultats de plusieurs séries, par exemple les résultats de séries qui utilisent des données de test différentes.

- **Pour afficher un ensemble de résultats antérieur**, sélectionnez-le dans le menu déroulant. Le menu affiche une liste temporaire qui est supprimée lorsque vous ouvrez une nouvelle solution.

- **Pour afficher les résultats d’une session antérieure**, choisissez **Importer les résultats de la couverture du code**, accédez au dossier **TestResults** dans votre solution, puis importez un fichier *.coverage*.

   La coloration de couverture peut être incorrecte si le code source a été modifié depuis que le fichier *.coverage* a été généré.

- **Pour afficher les résultats sous forme de texte**, choisissez **Exporter les résultats de la couverture du code**. Un fichier *.coveragexml* lisible est généré. Vous pouvez le traiter avec d’autres outils ou l’envoyer facilement par courrier électronique.

- **Pour envoyer les résultats à une autre personne**, envoyez un fichier *.coverage* ou un fichier *.coveragexml* exporté. Cela permet ensuite à la personne d'importer le fichier. Si la personne a la même version de code source, elle a accès à la coloration de couverture.

## <a name="merge-results-from-different-runs"></a>Fusionner les résultats de différentes exécutions

Dans certains cas, différents blocs de votre code seront utilisés, en fonction des données de test. Par conséquent, vous pouvez souhaiter combiner les résultats des plusieurs séries de tests.

Supposons par exemple que, lorsque vous exécutez un test avec l'entrée « 2 », vous constatez que 50 % d'une fonction spécifique est couvert. Si vous exécutez le test une deuxième fois avec l'entrée « -2 », la deuxième moitié de la fonction apparaît couverte dans la vue avec coloration de la couverture. Fusionnez maintenant les résultats des deux séries de tests. Le rapport et la vue de coloration de couverture indiquent que la fonction a été couverte à 100 %.

Pour cela, utilisez ![Icône du bouton Fusionner dans la fenêtre Couverture du code](../test/media/codecoverage-mergeicon.png) **Fusionner les résultats de la couverture du code**. Vous pouvez choisir n'importe quelle combinaison de séries récentes ou de résultats importés. Si vous souhaitez combiner des résultats exportés, vous devez d'abord les importer.

Utilisez **Exporter les résultats de la couverture du code** pour enregistrer les résultats d’une opération de fusion.

### <a name="limitations-in-merging"></a>Limitations lors de la fusion

- Si vous fusionnez des données de couverture de différentes versions du code, les résultats s'affichent séparément, mais ils ne sont pas combinés. Pour obtenir des résultats entièrement combinés, utilisez la même version du code et modifiez uniquement les données de test.

- Si vous fusionnez un fichier de résultats qui a été exporté puis importé, vous pouvez uniquement consulter les résultats par lignes, et non pas par blocs. Utilisez la commande **Ajouter/supprimer des colonnes** pour afficher les données des lignes.

- Si vous fusionnez les résultats des tests d’un projet ASP .NET, les résultats des tests distincts sont affichés, mais ils ne sont pas combinés. Cela s'applique uniquement aux artefacts ASP .NET eux-mêmes : les résultats de tous les autres assemblys sont combinés.

## <a name="exclude-elements-from-the-code-coverage-results"></a>Exclure des éléments des résultats de la couverture du code

Vous pouvez exclure des éléments spécifiques dans votre code à partir des notes de couverture, par exemple si le code est généré à partir d'un modèle de texte. Ajoutez l'attribut <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> aux éléments de code suivants : classe, struct, méthode, propriété, setter ou getter de propriété, événement.

> [!TIP]
> Le fait d’exclure une classe n'a pas pour effet d’exclure ses classes dérivées.

Par exemple :

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>Exclure des éléments du code C++ natif

Pour exclure les éléments non managés (natifs) du code C++ :

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

Utilisez les macros suivante :

`ExcludeFromCodeCoverage(` *NomExclusion* `, L"` *NomFonction* `");`

`ExcludeSourceFromCodeCoverage(` *NomExclusion* `, L"` *CheminFichierSource* `");`

- *NomExclusion* est un nom unique.

- *NomFonction* est un nom qualifié complet de fonction. Il peut contenir des caractères génériques. Par exemple, pour exclure toutes les fonctions d'une classe, écrivez `MyNamespace::MyClass::*`

- *CheminFichierSource* est le chemin local ou UNC d’un fichier .cpp. Il peut contenir des caractères génériques. L'exemple suivant exclut tous les fichiers d'un répertoire particulier : `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- Placez les appels aux macros d'exclusion dans l'espace de noms global, et non dans un espace de noms ou dans une classe.

- Vous pouvez placer les exclusions dans le fichier de code de test unitaire ou dans le fichier de code de l'application.

- Les exclusions doivent être compilées en tant que code non managé (natif), en définissant l'option du compilateur ou à l'aide de `#pragma managed(off)`.

> [!NOTE]
> Pour exclure des fonctions dans le code C++/CLI, appliquez l'attribut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` à la fonction. La procédure est la même que pour C#.

### <a name="include-or-exclude-additional-elements"></a>Inclure ou exclure des éléments supplémentaires

L’analyse de la couverture du code est exécutée uniquement sur les assemblys chargés et pour lesquels un fichier *.pdb* est disponible dans le même répertoire que le fichier *.dll* ou *.exe*. Par conséquent, dans certains cas, vous pouvez étendre le jeu d’assemblys inclus par l’obtention des copies des fichiers *.pdb* appropriés.

Vous pouvez mieux contrôler les assemblys et les éléments qui sont sélectionnés pour l’analyse de la couverture du code en écrivant un fichier *.runsettings*. Par exemple, vous pouvez exclure des assemblys de type particulier sans devoir ajouter des attributs à leurs classes. Pour plus d’informations, consultez [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md).

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Analyse de la couverture du code dans Azure Pipelines

Lorsque vous archivez votre code, vos tests s’exécutent sur le serveur de builds, avec les tests des autres membres de l’équipe. Il est utile d’analyser la couverture du code dans Azure Pipelines, car cela permet d’obtenir l’image la plus récente et la plus complète possible de la couverture sur la totalité du projet. Cette analyse comporte également des tests système automatisés et d’autres tests codés qui ne sont généralement pas exécutés sur les ordinateurs de développement. Pour plus d’informations, voir [Exécuter des tests unitaires avec des builds](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts).

## <a name="analyze-code-coverage-from-the-command-line"></a>Analyser la couverture du code depuis la ligne de commande

Pour exécuter des tests à partir de la ligne de commande, utilisez *vstest.console.exe*. La couverture du code est une option de l’utilitaire *vstest.console.exe*.

1. Lancez l’Invite de commandes développeur pour Visual Studio :

   Dans le menu **Démarrer** de Windows, choisissez **Visual Studio 2017** > **Invite de commandes développeur pour Visual Studio 2017**.

2. À l'invite de commandes, exécutez la commande suivante :

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

Pour plus d’informations, consultez [Options de ligne de commande VSTest.Console.exe](vstest-console-options.md).

## <a name="troubleshoot"></a>Résoudre les problèmes

Si vous ne voyez pas les résultats de la couverture du code, consultez l’article [Résoudre les problèmes liés à la couverture du code](../test/troubleshooting-code-coverage.md).

## <a name="see-also"></a>Voir aussi

- [Personnaliser l’analyse de la couverture du code](../test/customizing-code-coverage-analysis.md)
- [Résoudre les problèmes liés à la couverture du code](../test/troubleshooting-code-coverage.md)
- [Tests unitaires sur votre code](../test/unit-test-your-code.md)
