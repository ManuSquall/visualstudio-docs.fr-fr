---
title: Utilisation de .NET 4.x dans Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 9a53db2d7cb73fbbb8ea694386dbada3186957ee
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508975"
---
# <a name="using-net-4x-in-unity"></a>Utilisation de .NET 4.x dans Unity

C# et .NET, les technologies sur lesquelles reposent les scripts Unity, ont continué à être mises à jour depuis que Microsoft les a initialement lancées en 2002. Toutefois, les développeurs Unity ne sont peut-être pas conscients du flux constant des nouvelles fonctionnalités ajoutées au langage C# et au .NET Framework. En effet, avant Unity 2017.1, Unity utilisait un runtime de script qui correspondait à .NET 3.5. Il lui manquait donc plusieurs années de mises à jour.

Avec la sortie d’Unity 2017.1, Unity a introduit une version expérimentale de son runtime de script, mise à niveau vers une version compatible avec .NET 4.6, C# 6. Dans Unity 2018.1, le runtime équivalent à .NET 4.x n’est plus considéré comme expérimental, alors que l’ancien runtime équivalent à .NET 3.5 est désormais considéré comme la version héritée. Avec la sortie d’Unity 2018.3, Unity prévoit de faire du runtime de script mis à niveau la sélection par défaut, et d’aller même encore plus loin en proposant une mise à jour pour le rendre compatible avec C# 7. Pour plus d’informations et pour obtenir les dernières mises à jour sur cette feuille de route, lisez le [billet de blog](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) consacré à Unity, ou visitez le [forum des préversions de fonctionnalités de script expérimentales](https://forum.unity.com/forums/experimental-scripting-previews.107/). En attendant, consultez les sections ci-dessous pour en savoir plus sur les nouvelles fonctionnalités disponibles dès maintenant avec le runtime de script .NET 4.x.

## <a name="prerequisites"></a>Prérequis

* [Unity 2017.1 ou version ultérieure](https://unity3d.com/) (2018.2 recommandé)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Activation du runtime de script .NET 4.x dans Unity

Pour activer le runtime de script .NET 4.x, effectuez les étapes suivantes :

1. Ouvrez PlayerSettings dans l’inspecteur Unity en sélectionnant **Edit (Edition) > Project Settings (Paramètres du projet) > Player (Lecteur)**.

1. Sous le titre **Configuration**, cliquez sur la liste déroulante **Scripting Runtime Version (Version du runtime de script)**, puis sélectionnez **.NET 4.x Equivalent** (Équivalent .NET 4.x). Vous êtes invité à redémarrer Unity.

![Sélectionner l’équivalent .NET 4.x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Choix entre les profils .NET 4.x et .NET Standard 2.0

Une fois que vous êtes passé au runtime de script équivalent à .NET 4.x, vous pouvez spécifier le **niveau de compatibilité d’API** dans le menu déroulant de PlayerSettings (**Edit (Edition) > Project Settings (Paramètres du projet) > Player (Lecteur)**). Nous avons deux options :

* **.NET Standard 2,0**. Ce profil correspond au [profil .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) publié par .NET Foundation. Unity recommande .NET Standard 2.0 pour les nouveaux projets. Il est plus petit que .NET 4.x, ce qui est avantageux pour les plateformes limitées en taille. De plus, Unity s’est engagé à prendre en charge ce profil sur toutes les plateformes prises en charge par Unity.

* **.Net 4. x**. Ce profil permet d’accéder à la dernière API .NET 4. Il inclut tout le code disponible dans les bibliothèques de classes .NET Framework et prend également en charge les profils .NET Standard 2.0. Utilisez le profil .NET 4.x si votre projet nécessite une partie de l’API non incluse dans le profil .NET Standard 2.0. Toutefois, certaines parties de cette API ne sont peut-être pas prises en charge sur toutes les plateformes d’Unity.

Pour en savoir plus sur ces options dans Unity, lisez le [billet de blog](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/).

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Ajout de références d’assembly en cas d’utilisation du niveau de compatibilité d’API .NET 4.x

Quand vous utilisez le paramètre .NET Standard 2.0 de la liste déroulante **API Compatibility Level** (Niveau de compatibilité d’API), tous les assemblys du profil d’API sont référencés et utilisables. Toutefois, quand vous utilisez le profil .NET 4.x, qui est plus conséquent, certains des assemblys avec lesquels Unity est livré ne sont pas référencés par défaut. Pour utiliser ces API, vous devez ajouter manuellement une référence d’assembly. Vous pouvez voir quels sont les assemblys avec lesquels Unity est livré dans le répertoire **MonoBleedingEdge/lib/mono** de votre installation de l’éditeur Unity :

![Répertoire MonoBleedingEdge](media/vstu_monobleedingedge.png)

Par exemple, si vous utilisez le profil .NET 4.x et si vous souhaitez utiliser `HttpClient`, vous devez ajouter une référence d’assembly pour System.Net.Http.dll. Sinon, le compilateur signale l’absence d’une référence d’assembly :

![référence d’assembly manquante](media/vstu_missing-reference.png)

Visual Studio regénère les fichiers .csproj et .sln des projets Unity chaque fois qu’ils sont ouverts. Ainsi, vous ne pouvez pas ajouter de références d’assembly directement dans Visual Studio, car elles sont perdues à la réouverture du projet. À la place, vous devez utiliser un fichier texte spécial nommé **mcs.rsp** :

1. Créez un fichier texte nommé **mcs.rsp** dans le répertoire **Assets** racine de votre projet Unity.

1. Sur la première ligne du fichier texte vide, entrez `-r:System.Net.Http.dll`, puis enregistrez le fichier. Vous pouvez remplacer « System.Net.Http.dll » par n’importe quel assembly inclus auquel il peut manquer une référence.

1. Redémarrez l’éditeur Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Tirer parti de la compatibilité .NET

En plus des nouvelles fonctionnalités de syntaxe et de langage C#, le runtime de script .NET 4.x permet aux utilisateurs d’Unity d’accéder à une vaste bibliothèque de packages .NET incompatibles avec le runtime de script .NET 3.5 existant.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Ajouter des packages NuGet à un projet Unity

[NuGet](https://www.nuget.org/) est le gestionnaire de package pour .NET. NuGet est intégré à Visual Studio. Toutefois, les projets Unity nécessitent un processus spécial pour permettre l’ajout de packages NuGet. En effet, quand vous ouvrez un projet dans Unity, ses fichiers projet Visual Studio sont regénérés, ce qui entraîne l’annulation des configurations nécessaires. Pour ajouter un package NuGet à votre projet Unity, effectuez ce qui suit :

1. Parcourez NuGet pour localiser un package compatible à ajouter (.NET Standard 2.0 ou .NET 4.x). Cet exemple montre comment ajouter [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/) (package souvent utilisé avec JSON) à un projet .NET Standard 2.0.

1. Cliquez sur le bouton **Télécharger** :

    ![bouton de téléchargement](media/vstu_nuget-download.png)

1. Localisez le fichier téléchargé, puis remplacez l’extension **.nupkg** par **.zip**.

1. Dans le fichier zip, accédez au répertoire **lib/netstandard2.0**, puis copiez le fichier **Newtonsoft.Json.dll**.

1. Dans le dossier **Assets** racine de votre projet Unity, créez un dossier nommé **Plugins**. Plugins est un nom de dossier spécial dans Unity. Pour plus d’informations, consultez la [documentation Unity](https://docs.unity3d.com/Manual/Plugins.html).

1. Collez le fichier **Newtonsoft.Json.dll** dans le répertoire **Plugins** de votre projet Unity.

1. Créez un fichier nommé **link.xml** dans le répertoire **Assets** de votre projet Unity, puis ajoutez le code XML suivant.  Ainsi, le processus de suppression du bytecode d’Unity n’entraîne pas la suppression des données nécessaires au moment de l’exportation vers une plateforme IL2CPP.  Bien que cette étape soit spécifique à cette bibliothèque, vous pouvez rencontrer des problèmes avec d’autres bibliothèques qui utilisent Reflection de manière similaire.  Pour plus d’informations, consultez la [documentation d’Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) sur ce sujet.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Tout étant en place, vous pouvez désormais utiliser le package Json.NET.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Ceci est un exemple simple d’utilisation d’une bibliothèque qui n’a aucune dépendance. Quand les packages NuGet reposent sur d’autres packages NuGet, vous devez télécharger ces dépendances manuellement et les ajouter au projet de la même manière.

## <a name="new-syntax-and-language-features"></a>Nouvelles fonctionnalités de syntaxe et de langage

L’utilisation du runtime de script mis à jour permet aux développeurs Unity d’accéder à C# 6 et à une multitude de nouvelles fonctionnalités de syntaxe et de langage.

### <a name="auto-property-initializers"></a>Initialiseurs de propriétés automatiques

Dans le runtime de script .NET 3.5 d’Unity, la syntaxe des propriétés automatiques permet de définir facilement et rapidement les propriétés non initialisées. Toutefois, l’initialisation doit avoir lieu ailleurs dans votre script. Désormais, avec le runtime .NET 4.x, il est possible d’initialiser les propriétés automatiques sur la même ligne :

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolation de chaîne

Avec l’ancien runtime .NET 3.5, la concaténation de chaînes nécessitait une syntaxe compliquée. Désormais, avec le Runtime .NET 4. x, la fonctionnalité d' [ `$` interpolation de chaîne](/dotnet/csharp/language-reference/tokens/interpolated) permet d’insérer des expressions dans des chaînes dans une syntaxe plus directe et lisible :

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Membres expression-bodied

Avec la nouvelle syntaxe C# disponible dans le runtime .NET 4.x, les [expressions lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) peuvent remplacer le corps des fonctions pour les rendre plus succinctes :

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Vous pouvez également utiliser des membres expression-bodied dans des propriétés en lecture seule :

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)

La [programmation asynchrone](/dotnet/csharp/async) permet d’effectuer des opérations longues sans entraîner d’absence de réponse de la part de votre application. Cette fonctionnalité permet également à votre code d’attendre la fin des opérations longues avant de poursuivre l’exécution de tout autre code dépendant des résultats de ces opérations. Par exemple, vous pouvez attendre la fin du chargement d’un fichier ou d’une opération réseau.

Dans Unity, vous effectuez généralement la programmation asynchrone à l’aide de [coroutines](https://docs.unity3d.com/Manual/Coroutines.html). Toutefois, depuis C# 5, la méthode de programmation asynchrone préférée pour le développement .NET est le [modèle TAP (modèle asynchrone basé sur les tâches)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) à l’aide des mots clés `async` et `await` avec [System.Threading.Task](/dotnet/api/system.threading.tasks.task). En résumé, dans une fonction `async`, vous pouvez appliquer `await` à l’exécution d’une tâche sans bloquer la mise à jour du reste de votre application :

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP est un sujet complexe, avec des nuances spécifiques à Unity dont les développeurs doivent tenir compte. TAP n’est donc pas un remplacement universel des coroutines dans Unity. Toutefois, il s’agit d’un outil parmi d’autres à exploiter. La portée de cette fonctionnalité dépasse le cadre de cet article, mais certaines bonnes pratiques et astuces générales sont fournies ci-dessous.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Informations de référence pour bien démarrer avec TAP dans Unity

Ces conseils peuvent vous aider à bien démarrer avec TAP dans Unity :

* Les fonctions asynchrones destinées à être attendues doivent avoir le type de retour [`Task`](/dotnet/api/system.threading.tasks.task) ou [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1) .
* Les fonctions asynchrones qui retournent une tâche doivent avoir le suffixe **« Async »** accolé à leurs noms. Le suffixe « Async » permet d’indiquer qu’une fonction doit toujours être attendue.
* Utilisez uniquement le type de retour `async void` pour les fonctions qui déclenchent des fonctions asynchrones à partir du code synchrone classique. De telles fonctions ne peuvent pas être attendues et ne doivent pas comporter le suffixe « Async » dans leurs noms.
* Unity utilise UnitySynchronizationContext pour garantir l’exécution des fonctions asynchrones sur le thread principal par défaut. L’API Unity n’est pas accessible en dehors du thread principal.
* Il est possible d’exécuter des tâches sur des threads d’arrière-plan avec des méthodes telles que [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) et [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait) . Cette technique permet de décharger les opérations coûteuses du thread principal pour améliorer les performances. Toutefois, l’utilisation de threads d’arrière-plan peut entraîner des problèmes difficiles à déboguer, par exemple les [conditions de concurrence](https://wikipedia.org/wiki/Race_condition).
* L’API Unity n’est pas accessible en dehors du thread principal.
* Les tâches qui utilisent des threads ne sont pas prises en charge sur les builds Unity WebGL.

#### <a name="differences-between-coroutines-and-tap"></a>Différences entre coroutines et TAP

Il existe des différences importantes entre les coroutines et TAP/async-await :

* Les coroutines ne peuvent pas retourner de valeurs, contrairement à `Task<TResult>`.
* Vous ne pouvez pas mettre `yield` dans une instruction try-catch, ce qui complique la gestion des erreurs avec les coroutines. Toutefois, try-catch fonctionne avec TAP.
* La fonctionnalité de coroutine d’Unity n’est pas disponible dans les classes qui ne dérivent pas de MonoBehaviour. TAP est idéal pour la programmation asynchrone dans de telles classes.
* À ce stade, Unity ne suggère pas d’utiliser TAP en tant que remplacement systématique des coroutines. Le profilage est le seul moyen de connaître les résultats spécifiques d’une approche par rapport à l’autre pour un projet donné.

> [!NOTE]
> Depuis Unity 2018.2, le débogage des méthodes asynchrones à l’aide de points d’arrêt n’est pas entièrement pris en charge. Toutefois, [cette fonctionnalité est attendue dans Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>opérateur nameof

L’opérateur `nameof` obtient le nom de chaîne d’une variable, d’un type ou d’un membre. Dans certains cas, `nameof` est utile, par exemple pour journaliser les erreurs et obtenir le nom de chaîne d’un enum :

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Attributs d’informations de l’appelant

Les [attributs d’informations de l’appelant](/dotnet/csharp/programming-guide/concepts/caller-information) fournissent des informations sur l’appelant d’une méthode. Vous devez fournir une valeur par défaut pour chaque paramètre à utiliser avec un attribut d’informations de l’appelant :

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>Using static

[Using static](/dotnet/csharp/language-reference/keywords/using-static) vous permet d’utiliser des fonctions statiques sans taper leur nom de classe. Avec using static, vous pouvez gagner de la place et du temps si vous devez utiliser plusieurs fonctions statiques provenant de la même classe :

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Considérations relatives à IL2CPP

Quand vous exportez votre jeu sur des plateformes comme iOS, Unity utilise son moteur IL2CPP pour « transpiler » le code IL en code C++, lequel est ensuite compilé à l’aide du compilateur natif de la plateforme cible. Dans ce scénario, plusieurs fonctionnalités .NET ne sont pas prises en charge, par exemple certaines parties de Reflection et l’utilisation du mot clé `dynamic`. Bien que vous puissiez contrôler l’utilisation de ces fonctionnalités dans votre propre code, vous pouvez rencontrer des problèmes dans les DLL et kits SDK tiers qui n’ont pas été écrits en tenant compte des spécificités d’Unity et d’IL2CPP. Pour plus d’informations sur ce sujet, consultez la documentation sur les [restrictions relatives aux scripts](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) sur le site d’Unity.

De plus, comme indiqué dans l’exemple Json.NET ci-dessus, Unity tente de supprimer le code inutilisé durant le processus d’exportation IL2CPP.  Bien que cela ne soit généralement pas un problème, avec les bibliothèques qui utilisent la réflexion, il peut accidentellement supprimer les propriétés ou les méthodes qui seront appelées au moment de l’exécution et qui ne peuvent pas être déterminées au moment de l’exportation.  Pour résoudre ces problèmes, ajoutez un fichier **link.xml** au projet qui contient une liste d’assemblys et d’espaces de noms sur lesquels le processus de suppression ne doit pas s’exécuter.  Pour plus d’informations, consultez la [documentation d’Unity sur la suppression du bytecode](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Exemple de projet Unity .NET 4.x

Il s’agit d’exemples d’utilisation de plusieurs fonctionnalités .NET 4.x. Vous pouvez télécharger le projet ou voir le code source sur [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Ressources supplémentaires

* [Blog Unity - Améliorations du runtime de script dans Unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [Historique de C#](/dotnet/csharp/whats-new/csharp-version-history)
* [Nouveautés de C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Programmation asynchrone dans Unity, utilisation de coroutines et de TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Utilisation de Async-Await à la place de coroutines dans Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Forum Unity - Préversions de fonctionnalités de script expérimentales](https://forum.unity.com/forums/experimental-scripting-previews.107/)