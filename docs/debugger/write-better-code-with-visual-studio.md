---
title: Techniques et outils de débogage
description: Écrire du code de meilleure qualité avec moins de bogues à l’aide de Visual Studio pour résoudre les exceptions, corriger les erreurs et améliorer votre code
ms.custom:
- debug-experiment
- seodec18
ms.date: 01/24/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bfbcf9a63a01d391cbbc65067793d75d42899c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901294"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Outils pour vous aider à écrire du code de meilleure qualité et des techniques de débogage

Résolution des bogues et les erreurs dans votre code peut prendre du temps--et parfois frustrante--la tâche. De temps pour apprendre à déboguer efficacement, mais un puissant IDE comme Visual Studio votre travail beaucoup plus facile. Un IDE peut aider à corriger les erreurs et de déboguer votre code plus rapidement et pas seulement ça, mais il peut également aider à écrire de code de meilleure qualité avec moins de bogues. Notre objectif dans cet article est de vous donner une vue holistique du processus de « correction des bogues », afin de savoir quand utiliser l’Analyseur de code, quand utiliser le débogueur, comment résoudre les exceptions et comment coder dans un but. Si vous connaissez déjà vous devez utiliser le débogueur, consultez [tout d’abord examiner le débogueur](../debugger/debugger-feature-tour.md).

Dans cet article, nous parler en tirant parti de l’IDE pour améliorer la productivité de vos sessions de codage. Nous abordons le thème sur plusieurs tâches, telles que :

* Préparer votre code pour le débogage en tirant parti d’analyseur de code de l’IDE

* Comment résoudre les exceptions (erreurs)

* Comment réduire les bogues en codant dans un but (à l’aide d’assert)

* Quand utiliser le débogueur

Pour illustrer ces tâches, nous montrons quelques-uns des types plus courants des erreurs et des bogues que vous allez rencontrer lorsque vous tentez de déboguer vos applications. Bien que l’exemple de code est C#, les informations conceptuelles sont généralement applicables à C++, Visual Basic, JavaScript et autres langages pris en charge par Visual Studio (sauf indication contraire). Les captures d’écran sont en C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Créer un exemple d’application avec certains bogues et les erreurs qu’il contient

Le code suivant a des bogues que vous pouvez corriger à l’aide de l’IDE Visual Studio. L’application ici est une application simple qui simule l’obtention de données JSON à partir d’une opération, la désérialisation des données à un objet et la mise à jour d’une liste simple avec les nouvelles données.

Pour créer l’application :

1. Ouvrez Visual Studio et choisissez **fichier** > **New** > **projet**. Sous **Visual C#** , choisissez **Windows Desktop** ou **.NET Core**, puis, dans le volet central, choisissez un **application Console**.

    > [!NOTE]
    > Si vous ne voyez pas le modèle de projet **Application console**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop** ou **Développement multiplateforme .NET Core**, puis **Modifier**.

2. Dans le **nom** , tapez **Console_Parse_JSON** et cliquez sur **OK**. Visual Studio crée le projet.

3. Remplacez le code par défaut dans le projet *Program.cs* fichier avec l’exemple de code ci-dessous.

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

## <a name="find-the-red-and-green-squiggles"></a>Rechercher les tildes rouges et vertes !

Avant d’essayer de démarrer l’exemple d’application et exécutez le débogueur, vérifiez le code dans l’éditeur de code pour les tildes rouges et vertes. Ils représentent des erreurs et avertissements sont identifiés par l’Analyseur de code de l’IDE. Les tildes rouges sont des erreurs de compilation, qui vous devez corriger avant de peut exécuter le code. Les tildes verts sont des avertissements. Bien que vous pouvez souvent exécuter votre application sans résoudre les avertissements, ils peuvent être une source de bogues et vous souvent gagnez du temps et des problèmes en étudiant les. Ces avertissements et erreurs apparaissent également dans le **liste d’erreurs** fenêtre, si vous préférez un affichage de liste.

Dans l’exemple d’application, vous voyez plusieurs tildes rouges dont vous avez besoin pour résoudre et une seule verte qui vous explorerez. Voici la première erreur.

![Comme une ligne ondulée rouge s’affiche](../debugger/media/write-better-code-red-squiggle.png)

Pour corriger cette erreur, vous allez examiner une autre fonctionnalité de l’IDE, représenté par l’icône d’ampoule.

## <a name="check-the-light-bulb"></a>Vérifier l’ampoule !

La première ligne ondulée rouge représente une erreur de compilation. Pointez dessus et vous voyez le message ```The name `Encoding` does not exist in the current context```.

Notez que cette erreur affiche une icône d’ampoule à l’angle inférieur gauche. Avec l’icône de tournevis ![icône de tournevis](../ide/media/screwdriver-icon.png), l’icône d’ampoule ![icône d’ampoule](../ide/media/light-bulb-icon.png) représente des Actions rapides qui peuvent vous aider à corriger ou refactoriser du code inline. Ampoule représente les problèmes que vous avez *doit* corriger. Le tournevis concerne les problèmes que vous pouvez choisir de corriger. Utiliser la première correction suggérée pour résoudre cette erreur en cliquant sur **à l’aide de System.Text** sur la gauche.

![Utiliser l’ampoule pour corriger le code](../debugger/media/write-better-code-missing-include.png)

Lorsque vous cliquez sur cet élément, Visual Studio ajoute le `using System.Text` instruction en haut de la *Program.cs* fichier et le trait de soulignement ondulé rouge disparaît. (Lorsque vous n’êtes pas sûr de ce que peut faire un correctif suggéré, choisissez le **aperçu des modifications** lien sur la droite avant d’appliquer le correctif.)

L’erreur précédente est courant que vous généralement corriger en ajoutant une nouvelle `using` instruction à votre code. Il existe plusieurs erreurs courantes, similaire à celui-ci comme ```The type or namespace `Name` cannot be found.``` ces types d’erreurs peuvent indiquer une référence d’assembly manquant (cliquez sur le projet, choisissez **ajouter** > **référence**), un nom mal orthographié ou une bibliothèque manquante que vous devez ajouter (pour C#, cliquez sur le projet et choisissez **gérer les Packages NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Corriger les erreurs et avertissements restants

Il existe quelques tildes plus à examiner dans ce code. Vous voyez ici une erreur de conversion de type commun. Lorsque vous pointez sur la ligne ondulée, vous voyez que le code tente de convertir une chaîne en entier, ce qui n’est pas pris en charge sauf si vous ajoutez un code explicite pour effectuer la conversion.

![Erreur de conversion de type](../debugger/media/write-better-code-conversion-error.png)

Étant donné que l’Analyseur de code ne peuvent pas deviner votre intention, il n’existe aucune des ampoules pour vous aider tout au long de ce moment. Pour corriger cette erreur, vous devez connaître l’intention du code. Dans cet exemple, il n’est pas trop difficile de voir que `points` doit être une valeur numérique (entier), étant donné que vous essayez d’ajouter `points` à `totalpoints`.

Pour corriger cette erreur, modifiez le `points` membre de la `User` classe à partir de ce :

```csharp
[DataMember]
internal string points;
```

en ceci :

```csharp
[DataMember]
internal int points;
```

Les lignes ondulées rouges dans l’éditeur de code disparaissent.

Ensuite, placez le curseur sur la verte ondulée dans la déclaration de la `points` membre de données. L’Analyseur de code vous indique que la variable n’est jamais assignée une valeur.

![Message d’avertissement pour la variable non assignée](../debugger/media/write-better-code-warning-message.png)

En règle générale, cela représente un problème qui doit être corrigé. Toutefois, dans l’exemple d’application vous sont en fait stocker des données dans le `points` variable pendant le processus de désérialisation et en ajoutant ensuite cette valeur à la `totalpoints` membre de données. Dans cet exemple, vous connaissez l’objectif du code et pouvez ignorer l’avertissement. Toutefois, si vous souhaitez éliminer l’avertissement, vous pouvez remplacer le code suivant :

```csharp
item.totalpoints = users[i].points;
```

par le code :

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

La ligne verte ondulée disparaît.

## <a name="fix-an-exception"></a>Résoudre une exception

Lorsque vous avez résolu tous les tildes rouges et résolu--ou au moins examiné--les tildes verts, vous êtes prêt à démarrer le débogueur et exécuter l’application.

Appuyez sur **F5** (**Déboguer > Démarrer le débogage**) ou sur le bouton **Démarrer le débogage** ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage ") dans la barre d’outils Débogage.

À ce stade, l’exemple d’application lève une `SerializationException` exception (une erreur d’exécution). Autrement dit, l’application amaigrit sur les données qu’il tente de sérialiser. Étant donné que vous avez démarré l’application en mode débogage (débogueur attaché), assistance de l’Exception du débogueur ouvre directement le code qui a levé l’exception et vous donne un message d’erreur utiles.

![Se produit une exception SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Le message d’erreur vous indique que la valeur `4o` ne peut pas être analysée en tant qu’entier. Par conséquent, dans cet exemple, vous connaissez les données sont incorrectes : `4o` doit être `40`. Toutefois, si vous n’êtes pas dans le contrôle des données dans un scénario réel (par exemple, bénéficient d’un service web), que faire à ce sujet ? Comment résoudre ce problème ?

Lorsque vous atteignez une exception, vous devez (et réponses) quelques questions :

* Cette exception n’est simplement un bogue que vous pouvez corriger ? Ou

* Est cette exception quelque chose que vos utilisateurs peuvent rencontrer ?

Si elle est la première, corriger le bogue. (Dans l’exemple d’application, cela signifie que corriger les données incorrectes.) Dans le cas ce dernier, vous devrez peut-être gérer l’exception dans votre code en utilisant un `try/catch` bloc (Examinons autres stratégies possibles dans la section suivante). Dans l’exemple d’application, remplacez le code suivant :

```csharp
users = ser.ReadObject(ms) as User[];
```

par le code suivant :

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

Un `try/catch` bloc a un impact sur les performances, vous devez donc uniquement pour les utiliser lorsque vous avez vraiment besoin les, autrement dit, où (a), ils peuvent se produire dans la version release de l’application et où (b) la documentation pour la méthode indique que vous devez rechercher le exception (en supposant que la documentation est terminée !). Dans de nombreux cas, vous pouvez gérer une exception de manière appropriée et l’utilisateur ne devra jamais à le savoir.

Voici quelques conseils importants pour la gestion des exceptions :

* Évitez d’utiliser un bloc catch vide, comme `catch (Exception) {}`, qui n’accepte pas les mesures nécessaires pour exposer ou gérer une erreur. Un bloc catch vide ou non informatives peut masquer des exceptions et peut rendre votre code plus difficile à déboguer au lieu de plus facile.

* Utilisez le `try/catch` bloc autour de la fonction spécifique qui lève l’exception (`ReadObject`, dans l’exemple d’application). Si vous l’utilisez autour d’un plus grand bloc de code, vous retrouver de masquage de l’emplacement de l’erreur. Par exemple, n’utilisez pas le `try/catch` bloc autour de l’appel à la fonction parent `ReadToObject`, illustré ici, ou vous ne savez pas exactement où l’exception s’est produite.

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

* Pour les fonctions non connues que vous incluez dans votre application, spécialement ceux interagir avec des données externes (par exemple, une requête web), consultez la documentation pour voir quelles exceptions la fonction est susceptible de lever. Il peut s’agir des informations critiques pour la gestion correcte des erreurs et pour déboguer votre application.

Pour l’exemple d’application, vous devez corriger le `SerializationException` dans le `GetJsonData` méthode en modifiant `4o` à `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Clarifier votre intention du code à l’aide d’assert

Cliquez sur le bouton **Redémarrer** ![Redémarrer l’application](../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils Débogage (**Ctrl** + **Maj** + **F5**). Cette commande redémarre l’application dans moins d’étapes. Affiche la sortie suivante dans la fenêtre de console.

![Valeur null en sortie](../debugger/media/write-better-code-using-assert-null-output.png)

Vous pouvez voir quelque chose dans cette sortie n’est pas tout à fait. **nom** et **lastname** pour le troisième enregistrement sont vides !

Il s’agit d’un bon moment pour parler de pratiques de codage utile, souvent sous-utilisées, qui consiste à utiliser `assert` instructions dans vos fonctions. En ajoutant le code suivant, vous incluez une vérification à l’exécution pour vous assurer que `firstname` et `lastname` ne sont pas `null`. Remplacez le code suivant dans le `UpdateRecords` méthode :

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

En ajoutant `assert` instructions telles que pour vos fonctions pendant le processus de développement, vous pouvez aider à spécifier l’intention de votre code. Dans l’exemple précédent, nous spécifions les éléments suivants :

* Une chaîne valide est requise pour le prénom
* Une chaîne valide est requise pour le nom de famille

En spécifiant l’intention de cette façon, vous appliquez vos besoins. Il s’agit d’une méthode simple et pratique que vous pouvez utiliser à la surface d’exposition des bogues au cours du développement. (`assert` instructions sont également utilisées comme l’élément principal dans les tests unitaires.)

Cliquez sur le bouton **Redémarrer** ![Redémarrer l’application](../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils Débogage (**Ctrl** + **Maj** + **F5**).

> [!NOTE]
> Le `assert` code est actif uniquement dans une version Debug.

Lorsque vous redémarrez, le débogueur s’arrête à la `assert` instruction, car l’expression `users[i].firstname != null` prend la valeur `false` au lieu de `true`.

![Assert résout sur false](../debugger/media/write-better-code-using-assert.png)

Le `assert` erreur vous indique qu’il existe un problème que vous devez examiner. `assert` peut couvrir de nombreux scénarios où vous ne voyez pas nécessairement une exception. Dans cet exemple, l’utilisateur ne voit une exception et un `null` valeur est ajoutée en tant que `firstname` dans votre liste d’enregistrements. Cela peut entraîner des problèmes par la suite (telles que vous voyez dans la sortie de console) et peut être plus difficile à déboguer.

> [!NOTE]
> Dans les scénarios où vous appelez une méthode sur le `null` valeur, un `NullReferenceException` résultats. Vous voulez normalement Évitez d’utiliser un `try/catch` block pour une exception générale, autrement dit, une exception qui n’est pas liée à la fonction de bibliothèque spécifique. N’importe quel objet peut lever une `NullReferenceException`. Consultez la documentation de la fonction de bibliothèque si vous n’êtes pas sûr.

Pendant le processus de débogage, il est bon de garder un particulier `assert` instruction jusqu'à ce que vous savez que vous avez besoin pour la remplacer par un correctif de code réel. Supposons que vous décidez que l’utilisateur peut rencontrer l’exception dans une version Release de l’application. Dans ce cas, vous devez refactoriser le code pour vous assurer que votre application ne lèvent une exception irrécupérable ou entraîner une autre erreur. Par conséquent, pour corriger ce code, remplacez le code suivant :

```csharp
if (existingUser == false)
{
    User user = new User();
```

par le code suivant :

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

À l’aide de ce code, vous répondre aux exigences de votre code et assurez-vous que l’option un enregistrement avec un `firstname` ou `lastname` valeur `null` n’est pas ajouté aux données.

Dans cet exemple, nous avons ajouté les deux `assert` instructions à l’intérieur d’une boucle. En règle générale, lorsque vous utilisez `assert`, il est préférable d’ajouter `assert` instructions au point d’entrée (début) d’une fonction ou une méthode. Vous examinez actuellement les `UpdateRecords` méthode dans l’exemple d’application. Dans cette méthode, vous connaissez les ennuis si un des arguments de la méthode est `null`, donc à vérifier les deux avec un `assert` instruction au point d’entrée de la fonction.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Pour les instructions précédentes, votre objectif est que vous chargez des données existantes (`db`) et récupérer de nouvelles données (`users`) avant la mise à jour quoi que ce soit.

Vous pouvez utiliser `assert` avec n’importe quel type d’expression qui correspond à `true` ou `false`. Par conséquent, par exemple, vous pouvez ajouter un `assert` instruction comme celle-ci.

```csharp
Debug.Assert(users[0].points > 0);
```

Le code précédent est utile si vous souhaitez spécifier l’objectif suivant : une nouvelle valeur de point supérieure à zéro (0) est requis pour mettre à jour d’enregistrement de l’utilisateur.

## <a name="inspect-your-code-in-the-debugger"></a>Examinez votre code dans le débogueur

OK, maintenant que vous avez résolu tous les éléments critiques qui ne va pas avec l’exemple d’application, vous pouvez passer à autres choses importantes !

Nous vous avons montré assistance de l’Exception du débogueur, mais le débogueur est un outil beaucoup plus puissant qui vous permet également de faire d’autres éléments tels que de parcourir votre code et examiner ses variables. Ces fonctionnalités plus puissantes sont utiles dans de nombreux scénarios, en particulier les éléments suivants :

* Vous essayez d’isoler un bogue de runtime dans votre code, mais que vous ne parvenez pas à le faire à l’aide des méthodes et outils décrits précédemment.

* Vous souhaitez valider votre code, autrement dit, il regarder pendant son exécution pour vous assurer qu’il est anormal comme vous le souhaitez et faire ce que vous souhaitez.

    Il est intéressant de regarder votre code pendant son exécution. Vous en savoir plus sur votre code de cette façon et pouvez identifier les bogues avant qu’ils ne les problèmes évidents.

Pour savoir comment utiliser les fonctionnalités essentielles du débogueur, consultez [débogage pour les débutants](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Résoudre les problèmes de performances

Bogues d’un autre type incluent du code inefficace qui incite votre application s’exécute lentement ou d’utiliser trop de mémoire. En règle générale, optimisation des performances est une chose plus loin dans votre développement d’applications. Toutefois, vous pouvez rencontrer des problèmes de performances au début (par exemple, vous consultez que certaines parties de votre application est lente), et vous devrez peut-être tester dès le début de votre application avec les outils de profilage. Pour plus d’informations sur le profilage d’outils tels que l’outil utilisation du processeur et de l’Analyseur de mémoire, consultez [tout d’abord examiner les outils de profilage](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez appris comment éviter et résoudre de nombreux bogues courants dans votre code et quand utiliser le débogueur. Ensuite, en savoir plus sur l’utilisation du débogueur Visual Studio pour corriger les bogues.

> [!div class="nextstepaction"]
> [Débogage pour les grands débutants](../debugger/debugging-absolute-beginners.md)
