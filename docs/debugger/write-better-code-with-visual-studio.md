---
title: Techniques et outils de débogage
description: Écrivez un meilleur code avec moins de bogues en utilisant Visual Studio pour corriger les exceptions, corriger les erreurs et améliorer votre code
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302027"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Techniques et outils de débogage pour vous aider à écrire un meilleur code

La correction des bogues et des erreurs dans votre code peut prendre beaucoup de temps - et parfois frustrant - tâche. Il faut du temps pour apprendre à déboiser efficacement, mais un IDE puissant comme Visual Studio peut rendre votre travail beaucoup plus facile. Un IDE peut vous aider à corriger les erreurs et déboquer votre code plus rapidement, et pas seulement cela, mais il peut également vous aider à écrire un meilleur code avec moins de bugs. Notre but dans cet article est de vous donner une vue holistique du processus de "bug-fixing", de sorte que vous saurez quand utiliser l’analyseur de code, quand utiliser le débbugger, comment corriger les exceptions, et comment coder pour l’intention. Si vous savez déjà que vous avez besoin d’utiliser le débbugger, voir [d’abord regarder le débbugger](../debugger/debugger-feature-tour.md).

Dans cet article, nous parlons de tirer parti de l’IDE pour rendre vos sessions de codage plus productives. Nous abordons plusieurs tâches, telles que :

* Préparez votre code pour débogage en tirant parti de l’analyseur de code de l’IDE

* Comment corriger les exceptions (erreurs de temps d’exécution)

* Comment minimiser les bogues en codant pour l’intention (en utilisant assert)

* Quand utiliser le débbugger

Pour démontrer ces tâches, nous montrons quelques-uns des types les plus courants d’erreurs et de bogues que vous rencontrerez lorsque vous essayez de déboiffer vos applications. Bien que le code de l’échantillon soit C, les informations conceptuelles s’appliquent généralement aux langues C, Visual Basic, JavaScript et autres langues prises en charge par Visual Studio (sauf lorsqu’elles sont notées). Les captures d’écran sont en C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Créez une application d’échantillon avec quelques bogues et erreurs en elle

Le code suivant a quelques bogues que vous pouvez corriger à l’aide de l’IDE Visual Studio. L’application ici est une application simple qui simule l’obtention de données JSON à partir d’une opération, déséialiser les données à un objet, et la mise à jour d’une liste simple avec les nouvelles données.

Pour créer l’application :

1. Vous devez avoir Visual Studio installé et soit le développement de la **plate-forme cross .NET Core** ou la charge de travail **de développement de bureau .NET** installé, selon le type d’application que vous souhaitez créer.

    Si vous n’avez pas encore installé Visual Studio, rendez-vous sur la page [de téléchargements](https://visualstudio.microsoft.com/downloads/) Visual Studio pour l’installer gratuitement.

    Si vous avez besoin d’installer la charge de travail, mais ont déjà Visual Studio, cliquez sur **Outils** > **Obtenez des outils et des fonctionnalités**. Visual Studio Installer est lancé. Choisissez le **développement de la plate-forme transversale .NET Core** ou la charge de travail de développement de bureau **.NET,** puis choisissez **Modifier**.

1. Ouvrez Visual Studio.

    ::: moniker range=">=vs-2019"
    Sur la fenêtre de départ, choisissez **Créer un nouveau projet**. Type **console** dans la boîte de recherche, puis choisissez soit **Console App (.NET Core)** ou **Console App (.NET Framework)**. Choisissez **La prochaine**. Tapez un nom de projet comme **Console_Parse_JSON** et cliquez sur **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    De la barre de menu haut, choisissez **File** > **New** > **Project**. Dans le volet gauche de la nouvelle boîte de dialogue **de projet,** sous **Visual C ,** choisissez Console **App**, puis dans le volet moyen choisir soit Console **App (.NET Core)** ou **Console App (.NET Framework)**. Tapez un nom comme **Console_Parse_JSON** et cliquez **sur OK**.
    ::: moniker-end

    Si vous ne voyez pas le modèle de projet **Console App (.NET Core)** ou **Console App (.NET Framework),** rendez-vous sur **Tools** > **Get Tools and Features**, qui ouvre l’installateur visual Studio. Choisissez soit le **développement de la plate-forme transversale .NET Core** ou la charge de travail de développement de bureau **.NET,** puis choisissez **Modifier**.

    Visual Studio crée le projet de console, qui apparaît dans l’Explorateur de solutions dans le volet droit.

1. Remplacez le code par défaut dans le fichier *Program.cs* du projet avec le code de l’échantillon ci-dessous.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Trouvez les gribouillis rouges et verts!

Avant d’essayer de démarrer l’application d’échantillon et d’exécuter le débbugger, vérifiez le code dans l’éditeur de code pour les gribouillis rouges et verts. Il s’agit d’erreurs et d’avertissements identifiés par l’analyseur de code de l’IDE. Les gribouillis rouges sont des erreurs de compilation- temps, que vous devez corriger avant que vous puissiez exécuter le code. Les gribouillis verts sont des avertissements. Bien que vous puissiez souvent exécuter votre application sans corriger les avertissements, ils peuvent être une source de bugs et vous économisez souvent du temps et des ennuis en enquêtant sur eux. Ces avertissements et erreurs apparaissent également dans la fenêtre **Error List,** si vous préférez une vue de liste.

Dans l’application d’échantillon, vous voyez plusieurs gribouillis rouges que vous devez fixer, et un vert que vous regarderez. Voici la première erreur.

![Erreur montrant comme un calmar rouge](../debugger/media/write-better-code-red-squiggle.png)

Pour corriger cette erreur, vous examinerez une autre fonctionnalité de l’IDE, représentée par l’icône de l’ampoule.

## <a name="check-the-light-bulb"></a>Vérifie l’ampoule !

Le premier calmar rouge représente une erreur de compilation. Planer au-dessus et ```The name `Encoding` does not exist in the current context```vous voyez le message .

Notez que cette erreur montre une icône d’ampoule en bas à gauche. Avec l’icône ![tournevis icône](../ide/media/screwdriver-icon.png)tournevis icône ![, l’icône](../ide/media/light-bulb-icon.png) de l’ampoule d’ampoule représente actions rapides qui peuvent vous aider à fixer ou refactor code en ligne. L’ampoule représente les problèmes que vous *devez* résoudre. Le tournevis est pour les problèmes que vous pourriez choisir de fixer. Utilisez le premier correctif suggéré pour résoudre cette erreur en cliquant sur **l’utilisation de System.Text** sur la gauche.

![Utilisez l’ampoule pour corriger le code](../debugger/media/write-better-code-missing-include.png)

Lorsque vous cliquez sur cet `using System.Text` élément, Visual Studio ajoute la déclaration en haut du fichier *Program.cs,* et le calmar rouge disparaît. (Lorsque vous n’êtes pas sûr de ce qu’un correctif suggéré fera, choisissez le lien **de modifications Aperçu** sur la droite avant d’appliquer le correctif.)

L’erreur précédente est courante que vous corrigez habituellement en ajoutant une nouvelle `using` déclaration à votre code. Il existe plusieurs erreurs courantes et ```The type or namespace `Name` cannot be found.``` similaires à celle-ci, comme ces types d’erreurs, peuvent indiquer une référence d’assemblage manquante (clic droit du projet, choisissez **Add** > **Reference**), un nom mal orthographié, ou une bibliothèque manquante que vous devez ajouter (pour C, clic droit du projet et choisissez **Manage NuGet Packages**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Corriger les erreurs et avertissements restants

Il ya un peu plus de gribouillis à regarder dans ce code. Ici, vous voyez une erreur de conversion de type commun. Lorsque vous planez au-dessus de l’échiquage, vous voyez que le code essaie de convertir une chaîne en une int, qui n’est pas pris en charge à moins que vous ajoutez du code explicite pour faire la conversion.

![Erreur de conversion de type](../debugger/media/write-better-code-conversion-error.png)

Parce que l’analyseur de code ne peut pas deviner votre intention, il n’y a pas d’ampoules pour vous aider cette fois. Pour corriger cette erreur, vous devez connaître l’intention du code. Dans cet exemple, il n’est `points` pas trop difficile de voir que devrait être une `points` `totalpoints`valeur numérique (integer), puisque vous essayez d’ajouter à .

Pour corriger cette erreur, changez le `points` membre de la `User` classe de ceci :

```csharp
[DataMember]
internal string points;
```

par ceci :

```csharp
[DataMember]
internal int points;
```

Les lignes rouges squiggly dans l’éditeur de code disparaissent.

Ensuite, planez au-dessus de l’échiquage vert dans la déclaration du membre des `points` données. L’analyseur de code vous indique que la variable n’est jamais attribuée à une valeur.

![Message d’avertissement pour la variable non assignée](../debugger/media/write-better-code-warning-message.png)

En règle générale, cela représente un problème qui doit être résolu. Toutefois, dans l’application d’échantillon, `points` vous stockez en fait des données dans la `totalpoints` variable pendant le processus de désétérialisation, puis ajoutez cette valeur au membre des données. Dans cet exemple, vous connaissez l’intention du code et pouvez ignorer l’avertissement en toute sécurité. Toutefois, si vous souhaitez éliminer l’avertissement, vous pouvez remplacer le code suivant :

```csharp
item.totalpoints = users[i].points;
```

par le code :

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Le calmar vert s’en va.

## <a name="fix-an-exception"></a>Fixer une exception

Lorsque vous avez réparé tous les gribouillis rouges et résolu - ou du moins étudié - tous les gribouillis verts, vous êtes prêt à démarrer le débbugger et exécuter l’application.

Appuyez sur **F5** (**Debug > Start Debugging**) ou le bouton **Start Debugging** ![Démarrer Debugging](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage") dans la barre d’outils Debug.

À ce stade, l’application `SerializationException` d’échantillon jette une exception (une erreur de temps d’exécution). Autrement dit, l’application s’étouffe sur les données qu’elle essaie de sérialiser. Parce que vous avez commencé l’application en mode débogé (débbugger attaché), l’aide d’exception du débbuggeur vous emmène droit au code qui a jeté l’exception et vous donne un message d’erreur utile.

![Une sérialisationException se produit](../debugger/media/write-better-code-serialization-exception.png)

Le message d’erreur vous `4o` indique que la valeur ne peut pas être analysée comme un intégrant. Donc, dans cet exemple, vous savez `4o` que `40`les données sont mauvaises: devrait être . Cependant, si vous n’êtes pas en contrôle des données dans un scénario réel (disons que vous les obtenez à partir d’un service Web), que faites-vous à ce sujet? Comment pouvez-vous résoudre ce problème?

Lorsque vous atteignez une exception, vous devez poser (et répondre) à quelques questions :

* Cette exception n’est-elle qu’un bug que vous pouvez corriger ? Ou,

* Cette exception est-elle quelque chose que vos utilisateurs pourraient rencontrer ?

Si c’est le premier, répare le bogue. (Dans l’application d’échantillon, cela signifie fixer les mauvaises données.) Si c’est ce dernier, vous devrez peut-être `try/catch` gérer l’exception dans votre code à l’aide d’un bloc (nous examinons d’autres stratégies possibles dans la section suivante). Dans l’application d’échantillon, remplacez le code suivant :

```csharp
users = ser.ReadObject(ms) as User[];
```

par ce code :

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Un `try/catch` bloc a un certain coût de performance, de sorte que vous ne voudrez les utiliser quand vous en avez vraiment besoin, c’est-à-dire, où (a) ils pourraient se produire dans la version de sortie de l’application, et où (b) la documentation pour la méthode indique que vous devriez vérifier l’exception (en supposant que la documentation est complète!). Dans de nombreux cas, vous pouvez gérer une exception de manière appropriée et l’utilisateur n’aura jamais besoin de le savoir.

Voici quelques conseils importants pour la gestion des exceptions :

* Évitez d’utiliser un `catch (Exception) {}`bloc de capture vide, comme, qui ne prend pas les mesures appropriées pour exposer ou gérer une erreur. Un bloc de capture vide ou non informatif peut masquer des exceptions et peut rendre votre code plus difficile à déboiffer au lieu de plus facile.

* Utilisez `try/catch` le bloc autour de la fonction`ReadObject`spécifique qui jette l’exception (, dans l’application échantillon). Si vous l’utilisez autour d’un plus grand morceau de code, vous finissez par cacher l’emplacement de l’erreur. Par exemple, n’utilisez `try/catch` pas le bloc autour `ReadToObject`de l’appel à la fonction parent, montré ici, ou vous ne saurez pas exactement où l’exception s’est produite.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* Pour les fonctions inconnues que vous incluez dans votre application, en particulier celles qui interagissent avec des données externes (comme une demande Web), vérifiez la documentation pour voir quelles exceptions la fonction est susceptible de jeter. Cela peut être des informations critiques pour le traitement des erreurs appropriées et pour débogage de votre application.

Pour l’application d’échantillon, `SerializationException` fixer la méthode dans la `GetJsonData` méthode en changeant `4o` de `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Clarifiez votre intention de code en utilisant assert

Cliquez sur le bouton **Redémarrer** ![l’application](../debugger/media/dbg-tour-restart.png "RedémarrerApp") de redémarrage dans la barre d’outils Debug (**Ctrl** + **Shift** + **F5**). Cela redémarre l’application en moins d’étapes. Vous voyez la sortie suivante dans la fenêtre de la console.

![Valeur nulle dans la sortie](../debugger/media/write-better-code-using-assert-null-output.png)

Vous pouvez voir quelque chose dans cette sortie qui n’est pas tout à fait raison. **nom** et **nom de famille** pour le troisième album sont vides!

C’est le bon moment pour parler d’une pratique de codage `assert` utile, souvent sous-utilisée, qui est d’utiliser des instructions dans vos fonctions. En ajoutant le code suivant, vous incluez `firstname` une `lastname` vérification `null`du temps d’exécution pour vous assurer que et ne sont pas . Remplacer le code `UpdateRecords` suivant dans la méthode :

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

par le code :

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

En `assert` ajoutant des instructions comme celle-ci à vos fonctions pendant le processus de développement, vous pouvez vous aider à spécifier l’intention de votre code. Dans l’exemple précédent, nous spécifions ce qui suit :

* Une chaîne valide est requise pour le prénom
* Une chaîne valide est requise pour le nom de famille

En spécifiant l’intention de cette façon, vous appliquez vos exigences. Il s’agit d’une méthode simple et pratique que vous pouvez utiliser pour les bogues de surface pendant le développement. (`assert` les énoncés sont également utilisés comme élément principal dans les tests unitaires.)

Cliquez sur le bouton **Redémarrer** ![l’application](../debugger/media/dbg-tour-restart.png "RedémarrerApp") de redémarrage dans la barre d’outils Debug (**Ctrl** + **Shift** + **F5**).

> [!NOTE]
> Le `assert` code n’est actif que dans une version Debug.

Lorsque vous redémarrez, le débbuggeur s’arrête sur `assert` la déclaration, parce que l’expression `users[i].firstname != null` évalue au `false` lieu de `true`.

![Assert se résout au faux](../debugger/media/write-better-code-using-assert.png)

L’erreur `assert` vous indique qu’il y a un problème que vous devez étudier. `assert`peut couvrir de nombreux scénarios où vous ne voyez pas nécessairement une exception. Dans cet exemple, l’utilisateur ne verra `null` pas d’exception, et une valeur est ajoutée comme `firstname` dans votre liste d’enregistrements. Cela peut causer des problèmes plus tard (comme vous le voyez dans la sortie de la console) et pourrait être plus difficile à déboiffer.

> [!NOTE]
> Dans les scénarios où vous `null` appelez `NullReferenceException` une méthode sur la valeur, un résultat. Vous voulez normalement éviter `try/catch` d’utiliser un bloc pour une exception générale, c’est-à-dire une exception qui n’est pas liée à la fonction spécifique de la bibliothèque. N’importe quel `NullReferenceException`objet peut jeter un . Vérifiez la documentation pour la fonction de bibliothèque si vous n’êtes pas sûr.

Pendant le processus de débogage, il `assert` est bon de garder une instruction particulière jusqu’à ce que vous savez que vous devez le remplacer par un correctif de code réel. Supposons que vous décidiez que l’utilisateur pourrait rencontrer l’exception dans une version de l’application. Dans ce cas, vous devez refactor code pour s’assurer que votre application ne jette pas une exception fatale ou entraîner une autre erreur. Donc, pour corriger ce code, remplacez le code suivant :

```csharp
if (existingUser == false)
{
    User user = new User();
```

par ce code :

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

En utilisant ce code, vous répondez à vos `firstname` exigences `lastname` en `null` matière de code et assurez-vous qu’un enregistrement avec une ou une valeur de n’est pas ajouté aux données.

Dans cet exemple, nous `assert` avons ajouté les deux déclarations à l’intérieur d’une boucle. Typiquement, lors `assert`de l’utilisation `assert` , il est préférable d’ajouter des déclarations au point d’entrée (début) d’une fonction ou une méthode. Vous êtes actuellement `UpdateRecords` à la recherche de la méthode dans l’application échantillon. Dans cette méthode, vous savez que vous êtes `null`en difficulté si l’un des arguments de la méthode est , alors vérifiez-les tous les deux avec une déclaration au point d’entrée `assert` de la fonction.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Pour les instructions précédentes, votre intention`db`est que vous`users`chargez les données existantes ( ) et de récupérer de nouvelles données ( ) avant de mettre à jour quoi que ce soit.

Vous pouvez `assert` utiliser avec n’importe `true` quel `false`type d’expression qui se résout à ou . Ainsi, par exemple, vous `assert` pouvez ajouter une déclaration comme celle-ci.

```csharp
Debug.Assert(users[0].points > 0);
```

Le code précédent est utile si vous souhaitez spécifier l’intention suivante : une nouvelle valeur de point supérieure à zéro (0) est nécessaire pour mettre à jour l’enregistrement de l’utilisateur.

## <a name="inspect-your-code-in-the-debugger"></a>Inspectez votre code dans le débbuggeur

OK, maintenant que vous avez réparé tout ce qui est critique qui ne va pas avec l’application échantillon, vous pouvez passer à d’autres choses importantes!

Nous vous avons montré l’aide d’exception du débbugger, mais le débbugger est un outil beaucoup plus puissant qui vous permet également de faire d’autres choses comme passer à travers votre code et inspecter ses variables. Ces capacités plus puissantes sont utiles dans de nombreux scénarios, en particulier les suivants:

* Vous essayez d’isoler un bogue de temps d’exécution dans votre code, mais êtes incapable de le faire en utilisant des méthodes et des outils précédemment discutés.

* Vous voulez valider votre code, c’est-à-dire le regarder pendant qu’il s’exécute pour vous assurer qu’il se comporte comme vous vous y attendez et faire ce que vous voulez.

    Il est instructif de regarder votre code pendant qu’il s’exécute. Vous pouvez en apprendre davantage sur votre code de cette façon et peut souvent identifier les bogues avant qu’ils ne manifestent des symptômes évidents.

Pour apprendre à utiliser les caractéristiques essentielles du débogage, voir [Debugging pour les débutants absolus](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Résoudre les problèmes de performances

Les bogues d’un autre type incluent le code inefficace qui fait fonctionner votre application lentement ou pour employer trop de mémoire. En général, l’optimisation des performances est quelque chose que vous faites plus tard dans le développement de votre application. Cependant, vous pouvez rencontrer des problèmes de performances tôt (par exemple, vous voyez qu’une partie de votre application est en cours d’exécution lente), et vous devrez peut-être tester votre application avec les outils de profilage dès le début. Pour plus d’informations sur les outils de profilage tels que l’outil d’utilisation du processeur et l’analyseur de mémoire, voir [d’abord les outils de profilage](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez appris à éviter et à corriger de nombreux bogues courants dans votre code et quand utiliser le débbugger. Ensuite, en savoir plus sur l’utilisation du débbuggeur Visual Studio pour corriger les bogues.

> [!div class="nextstepaction"]
> [Débogage pour grands débutants](../debugger/debugging-absolute-beginners.md)
