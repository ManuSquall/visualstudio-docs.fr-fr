---
title: Débogage du code pour grands débutants
description: Si vous effectuez un débogage pour la première fois, découvrez quelques principes qui vous aideront à exécuter votre application en mode débogage avec Visual Studio.
ms.date: 07/06/2018
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35f9e866f58d52b7f74ac0a136b0eeb49382c612
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927322"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Guide du débogage pour grands débutants

Le code que nous écrivons en tant que développeurs de logiciels ne fait pas toujours ce que nous attendions. Il fait parfois quelque chose de totalement différent ! Dans ce cas, la tâche suivante consiste à identifier la raison, et bien qu’il soit tentant de rester simplement bouche bée devant notre code pendant des heures, il est beaucoup plus facile et efficace d’utiliser un outil de débogage, ou débogueur.

Malheureusement, un débogueur n’est pas quelque chose qui peut révéler comme par magie tous les problèmes ou « bogues » dans notre code. *Déboguer* signifie exécuter votre code pas à pas dans un outil de débogage tel que Visual Studio afin de trouver le point exact où vous avez fait une erreur de programmation. Vous comprenez alors les corrections que vous devez effectuer dans votre code, et les outils de débogage vous permettent souvent d’apporter des modifications temporaires afin de pouvoir continuer l’exécution du programme.

L’utilisation efficace d’un débogueur est également une compétence qui nécessite du temps et des efforts, mais il s’agit d’une tâche essentielle que tout développeur de logiciels doit savoir effectuer. Dans cet article, nous allons présenter les principes fondamentaux du débogage et fournir des conseils pour vous aider à démarrer.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Clarifiez le problème en vous posant les bonnes questions

Cela aide d’identifier clairement le problème que vous avez rencontré avant d’essayer de le résoudre. Nous supposons que vous avez déjà rencontré un problème dans votre code, sinon vous ne seriez pas ici à essayer de déterminer comment déboguer ! Par conséquent, avant de commencer le débogage, veillez à bien identifier le problème que vous cherchez à résoudre :

* Que devait faire votre code initialement ?

* Que s’est-il passé à la place ?

    Si vous avez rencontré une erreur (exception) pendant l’exécution de votre application, cela peut être une bonne chose ! Une exception est un événement inattendu rencontré lors de l’exécution de code, généralement une erreur quelconque. Un outil de débogage vous permet d’accéder à l’emplacement exact dans votre code où l’exception s’est produite, et peut vous aider à examiner les solutions possibles.

    Si quelque chose d’autre s’est produit, quel est le symptôme du problème ? Avez-vous déjà une idée de l’emplacement où ce problème s’est produit dans votre code ? Par exemple, si votre code affiche du texte, mais que celui-ci est incorrect, vous savez que soit vos données sont incorrectes, soit le code qui définit le texte d’affichage présente un bogue. En parcourant le code pas à pas dans un débogueur, vous pouvez examiner chaque modification apportée à vos variables pour découvrir exactement quand et comment des valeurs incorrectes sont affectées.

## <a name="examine-your-assumptions"></a>Examinez vos hypothèses

Avant d’étudier un bogue ou une erreur, réfléchissez aux hypothèses qui vous ont mené à attendre certains résultats. Des hypothèses cachées ou inconnues peuvent interférer avec l’identification d’un problème même quand vous observez directement la cause du problème dans un débogueur. Il se peut que vous ayez une longue liste d’hypothèses ! Voici quelques questions à se poser pour vous aider à y voir plus clair dans vos hypothèses.

* Utilisez-vous la bonne API (autrement dit, l’objet, la fonction, la méthode ou la propriété adéquat) ? Une API que vous utilisez peut ne pas faire ce que vous pensez qu’elle fait. (Une fois que vous avez examiné l’appel d’API dans le débogueur, sa correction peut nécessiter un aller-retour vers la documentation pour aider à identifier l’API correcte.)

* Utilisez-vous une API correctement ? Peut-être avez-vous utilisé la bonne API, mais pas de la bonne manière.

* Votre code contient-il des fautes de frappe ? Certaines fautes de frappe, comme une simple faute d’orthographe dans le nom d’une variable, peuvent être difficiles à voir, en particulier quand vous travaillez avec des langages qui ne nécessitent pas la déclaration des variables avant leur utilisation.

* Avez-vous apporté une modification à votre code, que vous pensez ne pas être liée au problème que vous observez ?

* Vous attendiez-vous à ce qu’un objet ou une variable contienne une certaine valeur (ou un certain type de valeur) différente de celle réellement présente ?

* Connaissez-vous l’intention du code ? Il est souvent plus difficile de déboguer le code rédigé par quelqu’un d’autre. Si ce n’est pas votre code, vous devrez peut-être consacrer du temps à apprendre ce que fait exactement le code avant de pouvoir le déboguer efficacement.

    > [!TIP]
    > Lors de l’écriture de code, commencez à petite échelle et avec du code qui fonctionne ! (Un bon exemple de code est utile ici.) Parfois, il est plus facile de corriger un ensemble volumineux ou complexe de code en commençant par un petit segment de code qui illustre le but principal que vous voulez atteindre. Ensuite, vous pouvez modifier ou ajouter du code de façon incrémentielle, en effectuant des tests à chaque stade.

Par la remise en question de vos hypothèses, vous pouvez réduire le temps nécessaire pour identifier un problème dans votre code. Vous pouvez également réduire le temps nécessaire pour résoudre un problème.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Parcourez votre code pas à pas en mode débogage pour déterminer où le problème s’est produit.

Quand vous exécutez normalement une application, vous voyez les erreurs et les résultats incorrects uniquement après l’exécution du code. Un programme peut également se terminer de façon inattendue sans vous indiquer pourquoi.

Quand vous exécutez une application dans un débogueur (autrement dit en *mode débogage*), le débogueur surveille activement tout ce qui se produit durant l’exécution du programme. Cela vous permet également de suspendre l’exécution de l’application à tout moment pour examiner son état, et de parcourir votre code ligne par ligne afin d’observer chaque détail à mesure qu’il se produit.

Dans Visual Studio, vous basculez en mode débogage à l’aide de la touche **F5** (ou de la commande de menu **Déboguer** > **Démarrer le débogage** ou du bouton **Démarrer le débogage** ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage") dans la barre d’outils Débogage). Si des exceptions se produisent, l’Assistance sur l’exception de Visual Studio vous amène au point exact où l’exception s’est produite et fournit d’autres informations utiles.

Si aucune exception ne s’est produite, vous avez probablement une bonne idée de l’endroit où rechercher le problème dans votre code. C’est dans ce cas-là que vous utilisez des *points d’arrêt* avec le débogueur afin d’examiner votre code plus attentivement. Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d’arrêt, Visual Studio interrompt l’exécution du code à l’emplacement du point d’arrêt pour vous permettre d’examiner les valeurs des variables, le comportement de la mémoire ou la séquence d’exécution du code.

Dans Visual Studio, vous pouvez rapidement définir un point d’arrêt en cliquant dans la marge de gauche en regard d’une ligne de code, ou en plaçant le curseur sur une ligne et en appuyant sur **F9**.

Pour illustrer ces concepts, nous allons vous guider à travers un exemple de code qui a déjà plusieurs bogues. Nous utilisons C#, mais les fonctionnalités de débogage s’appliquent à Visual Basic, C++, JavaScript, Python et d’autres langages pris en charge.

### <a name="create-a-sample-app-with-some-bugs"></a>Créer un exemple d’application (avec des bogues)

Nous allons maintenant créer une application qui comporte quelques bogues.

1. Visual Studio et la charge de travail **Développement .NET Desktop** ou **Développement multiplateforme .NET Core**, en fonction du type d’application que vous souhaitez créer, doivent être installés.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  pour l’installer gratuitement.

    Si vous devez installer la charge de travail, mais que vous avez déjà installé Visual Studio, cliquez sur **Outils** > **Obtenir des outils et fonctionnalités**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop** (ou **Développement multiplateforme .NET Core**), puis **Modifier**.

1. Ouvrez Visual Studio, puis choisissez **Fichier** > **Nouveau** > **Projet**.

1. Choisissez un modèle pour votre code d’application.

    Pour .NET Framework, dans la boîte de dialogue **Nouveau projet**, sélectionnez **Visual C#** , **Windows Desktop** dans la section Modèles installés puis, dans le volet central, sélectionnez **Application console (.NET Framework)**.

    Pour .NET Core, dans la boîte de dialogue **Nouveau projet**, sélectionnez **Visual C#** , **.NET Core** dans la section Modèles installés puis, dans le volet central, sélectionnez **Application console (.NET Core)**.

    Si vous ne voyez pas ces modèles, vous devez installer la charge de travail appropriée (voir les étapes précédentes).

1. Dans le champ **Nom**, tapez **ConsoleApp-FirstApp** et cliquez sur **OK**.

    Visual Studio crée le projet de console, qui apparaît dans l’Explorateur de solutions dans le volet droit.

1. Dans *Program.cs*, remplacez tout le code par défaut par le code suivant :

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Notre intention pour ce code consiste à afficher le nom de la galaxie, sa distance et son type dans une même liste. Pour déboguer, il est important de comprendre l’intention du code. Voici le format d’une ligne de la liste que nous souhaitons afficher dans la sortie :

    *nom de la galaxie*, *distance*, *type de galaxie*.

### <a name="run-the-app"></a>Exécuter l'application

1. Appuyez sur **F5** ou sur le bouton **Démarrer le débogage** ![Démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "Démarrer le débogage") dans la barre d’outils Débogage située au-dessus de l’éditeur de code.

    L’application démarre et aucune exception n’est signalée par le débogueur. Toutefois, la sortie visible dans la fenêtre de console n’est pas celle à laquelle vous vous attendez. Voici la sortie attendue :

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Et voici ce que nous obtenons à la place :

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    D’après la sortie et notre code, nous savons que `GType` est le nom de la classe qui stocke le type de galaxie. Nous essayons d’afficher le type de galaxie (par exemple, « Spiral »), pas le nom de la classe !

### <a name="debug-the-app"></a>Déboguer l’application

1. Avec l’application en cours d’exécution, définissez un point d’arrêt en cliquant dans la marge de gauche à côté de l’appel de méthode `Console.WriteLine` sur cette ligne de code.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Quand vous définissez le point d’arrêt, un point rouge apparaît dans la marge de gauche.

    Puisque nous constatons la présence d’un problème dans la sortie, nous allons commencer le débogage en examinant le code précédent qui définit la sortie dans le débogueur.

1. Cliquez sur le bouton **Redémarrer** ![Redémarrer l’application](../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils Débogage (**Ctrl** + **Maj** + **F5**).

    L’application s’interrompt au point d’arrêt que vous avez défini. La mise en surbrillance jaune indique où le débogueur est suspendu (la ligne de code jaune n’a pas encore été exécutée).

1. Placez le curseur sur la variable `GalaxyType` à droite puis, à gauche de l’icône de clé, développez `theGalaxy.GalaxyType`. Vous pouvez constater que `GalaxyType` contient une propriété `MyGType`, et que la valeur de propriété est définie sur `Spiral`.

    ![Inspecter une variable](../debugger/media/beginners-inspect-variable.png)

    « Spiral » est la valeur correcte que vous attendiez dans la console. Un bon point de départ consiste donc à pouvoir accéder à cette valeur dans ce code pendant l’exécution de l’application. Dans ce scénario, nous n’utilisons pas la bonne API. Nous allons voir si nous pouvons corriger cela pendant l’exécution du code dans le débogueur.

1. Dans le même code, toujours pendant le débogage, placez votre curseur à la fin de `theGalaxy.GalaxyType` et remplacez-le par `theGalaxy.GalaxyType.MyGType`. Bien que vous puissiez effectuer cette modification, l’éditeur de code signale une erreur indiquant qu’il ne peut pas compiler ce code.

    ![Erreur de syntaxe](../debugger/media/beginners-edit.png)

1. Cliquez sur **Modifier** dans la boîte de message **Modifier et Continuer**. Un message d’erreur s’affiche maintenant dans la fenêtre **Liste d’erreurs**. L’erreur indique que `'object'` ne contient pas de définition pour `MyGType`.

    ![Erreur de syntaxe](../debugger/media/beginners-no-definition.png)

    Bien que nous ayons défini chaque galaxie avec un objet de type `GType` (qui a la propriété `MyGType`), le débogueur ne reconnaît pas l’objet `theGalaxy` comme un objet de type `GType`. Que se passe-t-il ? Vous devez examiner tout code qui définit le type de galaxie. Vous constatez alors que la classe `GType` a indubitablement une propriété `MyGType`, mais quelque chose ne va pas. Le message d’erreur concernant `object` s’avère être l’indice : pour l’interpréteur de langage, le type semble être un objet de type `object` au lieu d’un objet de type `GType`.

1. En examinant votre code associé à la définition du type de galaxie, vous constatez que la propriété `GalaxyType` de la classe `Galaxy` est spécifiée comme `object` au lieu de `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Remplacez le code précédent par ceci :

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Cliquez sur le bouton **Redémarrer** ![Redémarrer l’application](../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils Débogage (**Ctrl** + **Maj**  + **F5**) pour recompiler le code et redémarrer.

    Maintenant, quand le débogueur s’arrête sur `Console.WriteLine`, vous pouvez pointer sur `theGalaxy.GalaxyType.MyGType` et vérifier que la valeur est définie correctement.

1. Supprimez le point d’arrêt en cliquant sur le cercle de point d’arrêt dans la marge de gauche (ou cliquez avec le bouton droit et choisissez **Point d’arrêt** > **Supprimer le point d’arrêt**), puis appuyez sur **F5** pour continuer.

    L’application s’exécute et affiche la sortie. Cela semble correct désormais, mais vous remarquez une chose : vous vous attendiez à ce que la galaxie Small Magellanic Cloud apparaisse comme une galaxie de type Irregular dans la sortie de console, mais aucun type de galaxie n’est mentionné.

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Définissez un point d’arrêt sur cette ligne de code.

    ```csharp
    public GType(char type)
    ```

    Ce code étant celui où le type de galaxie est défini, nous devons l’examiner plus en détail.

1. Cliquez sur le bouton **Redémarrer** ![Redémarrer l’application](../debugger/media/dbg-tour-restart.png "RestartApp") dans la barre d’outils Débogage (**Ctrl** + **Maj**  + **F5**) pour redémarrer.

    Le débogueur s’arrête sur la ligne de code où vous avez défini le point d’arrêt.  

1. Pointez sur la variable `type`. Vous voyez la valeur `S` (après le code de caractère). Ce qui vous intéresse, c’est une valeur `I`, puisque vous savez qu’il s’agit du type de galaxie Irregular.

1. Appuyez sur **F5** et pointez à nouveau sur la variable `type`. Répétez cette étape jusqu’à voir la valeur `I` dans la variable `type`.

    ![Inspecter une variable](../debugger/media/beginners-inspecting-data.png)

1. Maintenant, appuyez sur **F11** (**Déboguer** > **Pas à pas détaillé** ou le bouton **Pas à pas détaillé** dans la barre d’outils Débogage).

    **F11** fait avancer le débogueur (et exécute le code) une seule instruction à la fois. **F10** (**Pas à pas principal**) est une commande similaire, et toutes deux sont extrêmement utiles pour apprendre à utiliser le débogueur.

1. Appuyez sur **F11** jusqu’à vous arrêter sur une ligne de code dans l’instruction `switch` pour une valeur « I ». Vous constatez ici un problème évident résultant d’une faute de frappe. Vous vous attendiez à ce que le code accède à l’emplacement où il définit `MyGType` comme type de galaxie Irregular, mais au lieu de cela le débogueur ignore complètement ce code et s’arrête à la section `default` de l’instruction `switch`.

    ![Rechercher une faute de frappe](../debugger/media/beginners-typo.png)

    En examinant le code, vous voyez une faute de frappe dans l’instruction `case 'l'`. Cela devrait être `case 'I'`.

1. Cliquez dans le code `case 'l'` et remplacez-le par `case 'I'`.

1. Supprimez votre point d’arrêt, puis cliquez sur le bouton **Redémarrer** pour redémarrer l’application.

    Les bogues sont maintenant corrigés et vous voyez la sortie attendue.

    Appuyez sur n’importe quelle touche pour fermer l’application.

## <a name="summary"></a>Récapitulatif

Quand vous constatez un problème, utilisez le débogueur et les [commandes de pas à pas](../debugger/navigating-through-code-with-the-debugger.md) telles que **F10** et **F11** pour rechercher la région de code où se trouve le problème.

> [!NOTE]
> Si son identification est difficile, définissez un point d’arrêt dans le code qui s’exécute avant le moment où le problème se produit, puis utilisez les commandes de pas à pas jusqu’à ce que le problème se manifeste. Vous pouvez également utiliser des [points de trace](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) pour enregistrer des messages dans la fenêtre **Sortie**. En examinant les messages enregistrés (et en observant ceux qui n’ont pas encore été enregistrés), vous pouvez souvent isoler la région de code présentant un problème. Vous devrez peut-être répéter ce processus plusieurs fois afin de localiser l’emplacement précis du problème.

Une fois identifiée la région de code à problème, utilisez le débogueur pour l’examiner. Pour rechercher la cause d’un problème, inspectez le code défectueux tout en exécutant votre application dans le débogueur :

* [Inspectez les variables](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) et vérifiez si elles contiennent le type de valeur prévu. Si vous trouvez une valeur incorrecte, recherchez où elle a été définie (vous devrez peut-être pour cela redémarrer le débogueur, examiner la [pile des appels](../debugger/how-to-use-the-call-stack-window.md), ou les deux).

* Vérifiez si votre application exécute le code prévu. (Par exemple, dans l’exemple d’application, nous nous attendions à ce que le code pour l’instruction switch affecte la valeur Irregular comme type de galaxie, mais l’application a ignoré le code à cause de la faute de frappe.)

> [!TIP]
> Vous utilisez un débogueur pour vous aider à trouver des bogues. Un outil de débogage peut trouver des bogues *à votre place* uniquement s’il connaît l’intention de votre code. Un outil ne peut avoir connaissance de l’intention de votre code que si vous, le développeur, exprimez cette intention. Vous devez pour cela écrire des [tests unitaires](../test/improve-code-quality.md). 

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez découvert quelques concepts généraux liés au débogage. Vous pouvez à présent en découvrir plus sur le débogueur.

> [!div class="nextstepaction"]
> [Présentation du débogueur](../debugger/debugger-feature-tour.md)
