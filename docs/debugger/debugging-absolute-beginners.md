---
title: Débogage du code pour les débutants
description: Si vous effectuez un débogage pour la première fois, découvrez quelques principes pour vous aider à exécuter votre application en mode débogage avec Visual Studio
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 42a04a64f5ed7f62f4b01f703efa85e36aa854ff
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39131867"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Le débogage pour les débutants

Sans échec, le code que nous écrivons en tant que développeurs de logiciels ne fait toujours pas ce que nous attendions à effectuer. Il fait parfois quelque chose de complètement différent ! Dans ce cas, la tâche suivante consiste à identifier la raison, et bien que nous pouvons être tentés de simplement conserver fixant notre code pour les heures, il est beaucoup plus facile et efficace d’utiliser un outil de débogage, ou du débogueur.

Un débogueur, malheureusement, n’est pas quelque chose qui peut révéler comme par magie tous les problèmes ou « bogues », dans notre code. *Débogage* moyen d’exécuter votre code pas à pas dans un outil de débogage que Visual Studio, pour trouver le point exact où vous avez effectué une erreur de programmation. Vous comprenez ensuite les corrections que vous devez faire dans votre code et outils de débogage vous permettent souvent d’apporter des modifications temporaires pour pouvoir continuer l’exécution du programme.

À l’aide d’un débogueur efficacement est également une compétence qui nécessaire du temps et des exercices pratiques pour en savoir plus, mais il est finalement essentiel pour tout développeur de logiciels. Dans cet article, puis, nous présentent les principes fondamentaux du débogage et fournissent des conseils pour vous aider à démarrer.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Clarifier le problème par vous-même poser les bonnes questions

Cela permet de clarifier le problème que vous avez rencontré avant d’essayer de résoudre le problème. Nous pensons que vous avez déjà exécuté dans un problème dans votre code, sinon vous n’ici essaie de déterminer comment déboguer ! Par conséquent, avant de commencer le débogage, veillez à ce que vous avez identifié le problème que vous cherchez à résoudre :

* Ce que vous attendez-vous votre code à faire ?

* Qu’est-il arrivé à la place ?

    Si vous avez rencontré une erreur (exception) pendant l’exécution de votre application, qui peut être une bonne chose ! Une exception est un événement inattendu rencontré lors de l’exécution de code, généralement une erreur quelconque. Un outil de débogage vous permet d’accéder à l’emplacement exact dans votre code où l’exception s’est produite et peut vous aider à examiner les solutions possibles.

    Si quelque chose d’autre s’est produit, ce qui est le symptôme du problème ? Après vous, déjà où ce problème s’est produite dans votre code ? Par exemple, si votre code affiche du texte, mais le texte est incorrect, vous savez que vos données soient incorrectes ou que le code que définir le texte d’affichage a un type de bogue. En parcourant le code dans un débogueur, vous pouvez examiner chaque modification à vos variables pour découvrir exactement quand et comment les valeurs incorrectes sont affectés.

## <a name="examine-your-assumptions"></a>Examinez vos hypothèses

Avant d’examiner un bogue ou une erreur, considérez les hypothèses que vous apportées à certains résultats. Hypothèses masqués ou inconnus peuvent interférer avec identification d’un problème même lorsque vous cherchez directement à la cause du problème dans un débogueur. Avoir une longue liste d’hypothèses possible ! Voici quelques questions à se poser en question vos hypothèses.

* Vous utilisez l’API de droite (autrement dit, l’objet droit, fonction, méthode ou propriété) ? Une API que vous utilisez peut ne pas faire ce que vous pensez qu’il fait. (Une fois que vous examinez l’appel d’API dans le débogueur, sa correction peut nécessiter un aller-retour vers la documentation pour aider à identifier l’API appropriée.)

* Vous utilisez une API correctement ? Peut-être vous utilisé le droit d’API, mais n’a pas l’utiliser dans la bonne façon.

* Votre code contient-il des fautes de frappe ? Quelques fautes de frappe, comme une faute d’orthographe simple d’un nom de variable peuvent être difficiles à voir, en particulier lorsque vous travaillez avec les langues qui ne nécessitent pas de variables à être déclarés avant leur utilisation.

* Fait que vous apportez une modification à votre code et supposent qu’il n’est pas lié au problème que vous observez ?

* Vous attendez-vous un objet ou une variable pour contenir une certaine valeur (ou un certain type de valeur) qui est différent de ce qui est réellement arrivé ?

* Connaissez-vous l’intention du code ? Il est souvent plus difficile à quelqu'un d’autre déboguer du code. Si elle n’est pas votre code, il est possible que vous devrez peut-être passer du temps à apprendre fait exactement quel le code avant de pouvoir les déboguer efficacement.

    > [!TIP]
    > Lors de l’écriture de code, commencer à petite échelle et commencez avec le code qui fonctionne ! (Les exemples de code est utile ici.) Parfois, il est plus facile de corriger un ensemble volumineux ou complexe de code en commençant par un petit morceau de code qui illustre la tâche principale que vous voulez atteindre. Ensuite, vous pouvez modifier ou ajouter du code de façon incrémentielle, à chaque point pour les erreurs de test.

Par la remise en question vos hypothèses, vous pouvez réduire le temps que nécessaire pour trouver un problème dans votre code. Vous pouvez également réduire le temps que nécessaire pour résoudre un problème.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Parcourir votre code en mode pour trouver où le problème s’est produite de débogage

Lorsque vous exécutez normalement une application, vous voir les erreurs et des résultats incorrects uniquement après l’exécution du code. Un programme peut également interrompre de façon inattendue sans vous indiquant pourquoi.

Exécution d’une application dans un débogueur, également appelé *mode débogage*, signifie que le débogueur surveille activement tout ce qui se produit en tant que le programme s’exécute. Il vous permet également à suspendre l’application à tout moment pour examiner son état et puis parcourir votre code ligne par ligne et écoutez tous les détails du problème.

Dans Visual Studio, vous permet d’entrer en mode débogage à l’aide de **F5** (ou le **déboguer** > **démarrer le débogage** commande de menu ou le **démarrer le débogage**  bouton ![démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "démarrer le débogage")) dans la barre d’outils déboguer. Si toutes les exceptions se produisent, assistance de l’Exception de Visual Studio ouvre le point exact où l’exception s’est produite et fournit d’autres informations utiles.

Si vous n’obtenez une exception, vous avez probablement une bonne idée où rechercher le problème dans votre code. Cela dans lequel vous utilisez *des points d’arrêt* avec le débogueur pour vous-même une occasion d’examiner votre code plus attentivement. Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Un point d’arrêt indique où Visual Studio doit suspendre votre code en cours d’exécution afin que vous puissiez examiner les valeurs des variables, ou le comportement de la mémoire ou la séquence dans laquelle le code s’exécute.

Dans Visual Studio, vous pouvez rapidement définir un point d’arrêt en cliquant dans la marge de gauche en regard d’une ligne de code. Placez le curseur sur une ligne et appuyez sur un ou **F9**.

Pour illustrer ces concepts, nous vous guident un exemple de code qui a déjà plusieurs bogues. Nous sommes à l’aide de c#, mais les fonctionnalités de débogage s’appliquent à Visual Basic, C++, JavaScript, Python et autres langues prises en charge.

### <a name="create-a-sample-app-with-some-bugs"></a>Créer un exemple d’application (avec des bogues)

Ensuite, nous allons créer une application qui a quelques bogues.

1. Vous devez avoir installé Visual Studio et soit le. **Développement bureautique NET** charge de travail ou. **NET Core le développement multiplateforme** charge de travail, selon le type d’application qui vous souhaitez créer.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

    Si vous devez installer la charge de travail, mais avez déjà installé Visual Studio, cliquez sur **outils** > **obtenir les outils et fonctionnalités**. Visual Studio Installer est lancé. Choisissez le. **Développement bureautique NET** (ou. **NET Core le développement multiplateforme**) charge de travail, puis choisissez **modifier**.

1. Ouvrez Visual Studio, puis choisissez **fichier** > **New** > **projet**.

1. Choisir un modèle pour votre code d’application.

    Pour .NET Framework, dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C#**, **Windows Desktop** à partir de la section Modèles installés, puis, dans le panneau central, sélectionnez  **Application console (.NET Framework)**.

    Pour .NET Core, dans le **nouveau projet** boîte de dialogue, sélectionnez **Visual C#**, **.NET Core** à partir de la section Modèles installés, puis, dans le volet du milieu sélectionnez  **Console App (.NET Core)**.

    Si vous ne voyez pas ces modèles, vous devez installer la charge de travail approprié (voir les étapes précédentes).

1. Dans le **nom** , tapez **ConsoleApp-FirstApp** et cliquez sur **OK**.

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

    Notre intention pour ce code consiste à afficher le nom de galaxy, la distance et le galaxy et le type de galaxy tout dans une liste. Pour déboguer, il est important de comprendre l’objectif du code. Voici le format pour une seule ligne dans la liste que nous souhaitons afficher dans la sortie :

    *nom de Galaxy*, *distance*, *type de galaxy*.

### <a name="run-the-app"></a>Exécuter l'application

1. Appuyez sur **F5** ou **démarrer le débogage** bouton ![démarrer le débogage](../debugger/media/dbg-tour-start-debugging.png "démarrer le débogage") dans la barre d’outils de débogage, situés au-dessus de l’éditeur de code.

    L’application démarre et aucune exception n’est indiquée pour nous par le débogueur. Toutefois, la sortie que vous voyez dans la fenêtre de console n’est pas ce que vous attendez. Voici la sortie attendue :

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Toutefois, nous voyons ceci à la place :

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Recherchez la sortie et notre code, nous savons que `GType` est le nom de la classe qui stocke le type galaxy. Nous essayons d’afficher le type réel galaxy (par exemple, « spirale »), pas le nom de classe !

### <a name="debug-the-app"></a>Déboguer l’application

1. Avec l’application en cours d’exécution, définissez un point d’arrêt en cliquant dans la marge de gauche à côté du `Console.WriteLine` appel de méthode dans cette ligne de code.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Lorsque vous définissez le point d’arrêt, un point rouge apparaît dans la marge de gauche.

    Étant donné que nous voyons un problème dans la sortie, nous allons commencer le débogage en examinant le code précédent qui définit la sortie dans le débogueur.

1. Cliquez sur le **redémarrer** ![redémarrer une application](../debugger/media/dbg-tour-restart.png "RestartApp") bouton dans la barre d’outils déboguer (**Ctrl** + **MAJ**   +  **F5**).

    L’application s’arrête au point d’arrêt que vous définissez. Le hightlighting jaune indique où le débogueur est suspendu (la ligne jaune de code n’a pas encore exécuté).

1. Placez le curseur sur le `GalaxyType` variable sur la droite, puis, à gauche de l’icône de clé, développez `theGalaxy.GalaxyType`. Vous pouvez constater que `GalaxyType` contient une propriété `MyGType`, et la valeur de propriété est définie sur `Spiral`.

    ![Inspecter une variable](../debugger/media/beginners-inspect-variable.png)

    « Spirale » est effectivement la valeur correcte que vous attendiez imprimer sur la console ! Il est donc un bon point de départ que vous pouvez accéder cette valeur dans ce code lors de l’exécution de l’application. Dans ce scénario, nous utilisons l’API incorrect. Nous verrons si nous pouvons résoudre ce problème lors de l’exécution de code dans le débogueur.

1. Dans le même code, pendant le débogage encore, placez votre curseur à la fin de `theGalaxy.GalaxyType` et remplacez-le par `theGalaxy.GalaxyType.MyGType`. Bien que vous pouvez effectuer cette modification, l’éditeur de code vous montre une erreur indiquant qu’il ne peut pas compiler ce code.

    ![Erreur de syntaxe](../debugger/media/beginners-edit.png)

1. Cliquez sur **modifier** dans le **Modifier & Continuer** boîte de message. Vous voyez un message d’erreur présent dans le **liste d’erreurs** fenêtre. L’erreur indique que le `'object'` ne contient pas une définition pour `MyGType`.

    ![Erreur de syntaxe](../debugger/media/beginners-no-definition.png)

    Même si nous définissons chaque galaxy avec un objet de type `GType` (qui a le `MGType` propriété), le débogueur ne reconnaît pas le `theGalaxy` objet en tant qu’objet de type `GType`. Que se passe-t-il ? Vous souhaitez examiner n’importe quel code qui définit le type de galaxy. Lorsque vous effectuez cette opération, vous constatez que le `GType` classe a sans aucun doute une propriété de `MyGType`, mais quelque chose ne vous convient pas. Le message d’erreur sur `object` s’avère pour être l’indice ; pour l’interpréteur de langage, le type semble être un objet de type `object` au lieu d’un objet de type `GType`.

1. En lisant votre code lié à la définition du type galaxy, vous trouvez le `GalaxyType` propriété de la `Galaxy` classe est spécifiée en tant que `object` au lieu de `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Modifiez le code précédent comme suit :

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Cliquez sur le **redémarrer** ![redémarrer une application](../debugger/media/dbg-tour-restart.png "RestartApp") bouton dans la barre d’outils déboguer (**Ctrl** + **MAJ**   +  **F5**) pour recompiler le code et de redémarrer.

    Désormais, lorsque le débogueur met en pause sur `Console.WriteLine`, vous pouvez pointer sur `theGalaxy.GalaxyType.MyGType`et vérifie qu’elle est définie correctement.

1. Supprimer le point d’arrêt en cliquant sur le cercle de point d’arrêt dans la marge de gauche (ou avec le bouton droit et choisissez **point d’arrêt** > **supprimer un point d’arrêt**), puis appuyez sur **F5** pour continuer.

    L’application s’exécute et affiche la sortie. Cela semble assez bonne maintenant, mais vous remarquer une chose ; vous vous attendiez le galaxy petit nuage Magellanic s’affiche comme une galaxie très irrégulière dans la sortie de console, mais il n’affiche aucun type galaxy du tout.

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

    Ce code étant où le type galaxy est défini, nous souhaitons tirer un examiner plus en détail.

1. Cliquez sur le **redémarrer** ![redémarrer une application](../debugger/media/dbg-tour-restart.png "RestartApp") bouton dans la barre d’outils déboguer (**Ctrl** + **MAJ**   +  **F5**) à redémarrer.

    Le débogueur s’arrête à la ligne de code où vous avez défini le point d’arrêt.  

1. Placez le curseur sur la `type` variable. Vous voyez la valeur `S` (en suivant le code de caractère). Vous êtes intéressé par une valeur de `I`, étant donné que vous savez qui est un type galaxy irrégulières.

1. Appuyez sur **F5** et placez le curseur sur la `type` variable à nouveau. Répétez cette étape jusqu'à ce que vous voyez la valeur `I` dans le `type` variable.

    ![Inspecter une variable](../debugger/media/beginners-inspecting-data.png)

1. Maintenant, appuyez sur **F11** (**déboguer** > **pas à pas détaillé** ou **pas à pas détaillé** bouton dans la barre d’outils Déboguer).

    **F11** fait avancer le débogueur (et exécute le code) à une seule instruction à la fois. **F10** (**pas à pas principal**) est une commande similaire, et les deux sont extrêmement utiles pour apprendre à utiliser le débogueur.

1. Appuyez sur **F11** jusqu'à ce que vous arrêtiez sur la ligne de code dans la `switch` instruction pour une valeur de « I ». Vous voyez ici un problème clair résultant d’une faute de frappe. Vous vous attendiez le code pour accéder à où elle définit `MyGType` comme un anormales type de galaxy, mais le débogueur à la place ignore ce code complètement et s’arrête à la `default` section de la `switch` instruction.

    ![Rechercher une faute de frappe](../debugger/media/beginners-typo.png)

    En examinant le code, vous voyez une faute de frappe dans le `case 'l'` instruction. Il doit être `case 'I'`.

1. Cliquez sur dans le code de `case 'l'`et remplacez-la par ' case 'I'.

1. Supprimer votre point d’arrêt, puis cliquez sur le **redémarrer** bouton redémarrer l’application.

    Les bogues sont corrigés maintenant et vous voyez la sortie que vous attendez !

    Appuyez sur n’importe quelle touche pour terminer l’application.

## <a name="summary"></a>Récapitulatif

Lorsque vous identifiez un problème, utilisez le débogueur et [étape commandes](../debugger/navigating-through-code-with-the-debugger.md) comme **F10** et **F11** pour rechercher la région de code avec le problème.

> [!NOTE]
> S’il est difficile d’identifier la région de code où le problème se produit, définir un point d’arrêt dans le code qui s’exécute avant que le problème se produit, puis utilisez les commandes pas à pas jusqu'à ce que vous voyiez le problème manifeste. Vous pouvez également utiliser [des points de trace](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) pour connecter des messages vers le **sortie** fenêtre. En examinant les messages enregistrés (et constaté que les messages n’ont pas encore été enregistrées !), vous pouvez souvent isoler la région de code avec le problème. Vous devrez peut-être répéter ce processus plusieurs fois pour le réduire.

Lorsque vous trouvez la région de code avec le problème, utilisez le débogueur pour examiner. Pour rechercher la cause d’un problème, examinez le code de problème lors de l’exécution de votre application dans le débogueur :

* [Inspecter les variables](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) et vérifier s’ils contiennent le type de valeurs qu’ils doivent contenir. Si vous trouvez une valeur incorrecte, Découvrez où la valeur incorrecte a été définie (pour rechercher où la valeur a été définie, vous devrez peut-être soit redémarrer le débogueur, examinez le [pile des appels](../debugger/how-to-use-the-call-stack-window.md), ou les deux).

* Vérifiez si votre application s’exécute le code que vous attendez. (Par exemple, dans l’exemple d’application, nous attendions le code pour l’instruction switch définir le type de galaxy à irréguliers, mais l’application ignorée le code en raison de la faute de frappe.)

> [!TIP]
> Vous utilisez un débogueur pour vous aider à trouver des bogues. Un outil de débogage peut trouver des bogues *vous* uniquement s’il en connaît l’objectif de votre code. Un outil ne peut avoir connaissance l’objectif de votre code si vous, le développeur, exprimer cette intention. Écriture [tests unitaires](../test/improve-code-quality.md) est comment procéder.

## <a name="next-steps"></a>Étapes suivantes

Dans cet article, vous avez appris quelques concepts généraux de débogage. Ensuite, vous pouvez démarrer d’apprendre à déboguer avec Visual Studio.

> [!div class="nextstepaction"]
> [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)
