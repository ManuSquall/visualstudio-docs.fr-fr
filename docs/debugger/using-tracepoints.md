---
title: Utiliser des points de trace dans le débogueur | Microsoft Docs
ms.date: 9/17/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 263657213f1720eaca7a0462bb31585adaacf9bb
ms.sourcegitcommit: 6244689e742e551e7b6933959bd42df56928ece3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72516389"
---
# <a name="use-tracepoints-in-the-visual-studio-debugger"></a>Utiliser des points de trace dans le débogueur Visual Studio

Les points de trace vous permettent d’enregistrer des informations dans la fenêtre sortie sous des conditions configurables sans modifier ou arrêter votre code. Cette fonctionnalité est prise en charge pour le code managé et natif, ainsi que pour plusieurs langages C#tels que JavaScript et.

## <a name="let39s-take-an-example"></a>Prenons&#39;un exemple

L’exemple de programme suivant est une simple `for` boucle avec une variable de compteur qui augmente d’une unité chaque fois que la boucle exécute une autre itération.

![Exemple de compteur](../debugger/media/counterexample.png "Exemple de compteur")

## <a name="set-tracepoints-in-source-code"></a>Définir des points de trace dans le code source

Vous pouvez définir des points de trace en spécifiant une chaîne de sortie sous la case à cocher **action** dans la fenêtre **paramètres de point d’arrêt** .

1. Pour initialiser un trace, cliquez d’abord sur la reliure à gauche du numéro de la ligne où vous souhaitez définir le trace.

   ![Initialisation du point d’arrêt](../debugger/media/breakpointinitialization.png "Initialisation du point d’arrêt")

2. Pointez sur le cercle rouge, puis cliquez sur l’icône d’engrenage.
3. La fenêtre **paramètres de point d’arrêt** s’ouvre.

   ![Fenêtre de point d’arrêt](../debugger/media/breakpointwindow.png "Fenêtre de point d’arrêt")

4. Activez la case à cocher **action** .

   ![Zone actions activées](../debugger/media/checkedactionsbox.png "Zone actions activées")

   Notez que le cercle rouge devient un losange indiquant que vous vous êtes passé d’un point d’arrêt à un point de trace.

5. Entrez le message que vous souhaitez connecter à la zone de texte **afficher un message dans le fenêtre Sortie** (pour plus d’informations, consultez les sections suivantes de cet article).

   Votre trace est maintenant défini. Appuyez sur le bouton de &quot; &quot;Close si vous souhaitez uniquement enregistrer des informations dans le Fenêtre Sortie.

6. Si vous souhaitez ajouter des conditions qui déterminent si votre message s’affiche, activez la case à cocher **conditions** .

   ![Zone des conditions vérifiées](../debugger/media/checkedconditionsbox.png "Zone des conditions vérifiées")

   Vous avez trois possibilités pour les conditions : **expression conditionnelle**, **filtre**et **nombre d’accès**.

## <a name="actions-menu"></a>Menu actions

Ce menu vous permet de consigner un message dans la fenêtre sortie. Tapez les chaînes que vous souhaitez générer dans la boîte de message (sans guillemets). Si vous souhaitez afficher des valeurs de variables, veillez à les placer entre accolades.

Par exemple, si vous souhaitez afficher la valeur de la variable `counter` dans la console de sortie, tapez {Counter} dans la zone de texte message.

![Message de sortie du compteur](../debugger/media/counteroutputmessage.png "Message de sortie du compteur")

Si vous cliquez sur **Fermer** , puis déboguez le programme (**F5**), la sortie suivante s’affiche dans la fenêtre sortie.

![Message d’action dans Fenêtre Sortie](../debugger/media/actionsmessageinoutputwindow.png "Message d’action dans Fenêtre Sortie")

Vous pouvez également utiliser des mots clés spéciaux pour afficher des informations plus spécifiques. Entrez le mot clé exactement comme indiqué ci-dessous (utilisez un « $ » devant chaque mot clé et tous les majuscules pour le mot clé proprement dit).

| Mot clé | Ce qui est affiché |
| --- | --- |
| $ADDRESS | Instruction actuelle |
| $CALLER | Nom de la fonction appelante |
| $CALLSTACK | Pile des appels |
| $FUNCTION | Nom de la fonction actuelle |
| $PID | ID du processus |
| $PNAME | Nom du processus |
| $TID | ID du thread |
| $TNAME   | Nom du thread |
| $TICK | Nombre de cycles (à partir de Windows GetTickCount) |

## <a name="conditions-menu"></a>Menu conditions

Les conditions vous permettent de filtrer vos messages de sortie, afin qu’ils s’affichent uniquement dans certains scénarios. Il existe trois types principaux de conditions à votre disposition.

### <a name="conditional-expression"></a>Expression conditionnelle
Pour une expression conditionnelle, un message de sortie s’affiche uniquement lorsque certaines conditions sont remplies.

Pour les expressions conditionnelles, vous pouvez soit définir le décompte de trace pour générer un message quand une certaine condition est vraie, soit quand il a changé. Par exemple, si vous souhaitez uniquement afficher la valeur du compteur pendant les itérations de la boucle `for`, vous pouvez sélectionner l’option **est true** , puis taper `i%2 == 0` dans la zone de texte message.

![L’expression conditionnelle a la valeur true](../debugger/media/conditionalexpressionistrue.png "L’expression conditionnelle a la valeur true")

Si vous souhaitez imprimer la valeur du compteur lorsque l’itération de la `for` boucle change, sélectionnez l’option **lors** de la modification et tapez `i` dans la zone de texte message.

![Expression conditionnelle en cas de modification](../debugger/media/conditionalexpressionwhenchanged.png "Expression conditionnelle en cas de modification")

Le comportement de l’option **When Changed** est différent pour différents langages de programmation.

- Pour le code natif, le débogueur ne considère pas la première évaluation de la condition comme étant une modification, donc n’atteint pas le point de trace de la première évaluation.
- Pour le code managé, le débogueur atteint le trace de la première évaluation après que la **modification a été** sélectionnée.

Pour obtenir une vue plus complète des expressions valides que vous pouvez utiliser lors de la définition des conditions, consultez [expressions dans le débogueur](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Nombre d’accès
Une condition de nombre d’accès vous permet d’envoyer une sortie uniquement après que la ligne de code où le point de trace est défini a été exécutée un nombre de fois spécifié.

Pour le nombre d’accès, vous pouvez choisir de générer un message lorsque la ligne de code où le point de trace est défini a été exécutée un nombre de fois égal à, est un multiple de, ou est supérieur ou égal à la valeur du nombre d’accès spécifié. Choisissez l’option qui correspond le mieux à vos besoins et tapez une valeur entière dans le champ (par exemple, 5) qui représente cette itération.

![Nombre d’accès aux expressions conditionnelles](../debugger/media/conditionalexpressionhitcount.png "Nombre d’accès aux expressions conditionnelles")

### <a name="filter"></a>Filtre
Pour une condition de filtre, spécifiez les périphériques, les processus ou les threads pour lesquels la sortie est affichée.

![Filtre d’expression conditionnelle](../debugger/media/conditionalexpressionfilter.png "Filtre d’expression conditionnelle")

Liste des expressions de filtre :

- MachineName = "nom"
- ProcessId = valeur
- ProcessName = "nom"
- ThreadId = valeur
- ThreadName = "nom"

Placez les chaînes (telles que les noms) entre guillemets doubles. Les valeurs peuvent être entrées sans guillemets. Vous pouvez combiner des clauses à l’aide de `&` (`AND`), `||` (`OR`), `!` (`NOT`) et des parenthèses.

## <a name="considerations"></a>Éléments à prendre en considération

Alors que les points de trace ont pour but de faciliter le débogage, vous devez tenir compte de certaines considérations lorsqu’il s’agit de les utiliser.

Parfois, lorsque vous Inspectez une propriété ou un attribut d’un objet, sa valeur peut changer. Il ne s’agit pas d’un bogue provoqué par la fonctionnalité de points de trace elle-même, mais il est intéressant de mentionner que l’utilisation des points de trace pour inspecter les objets n’évite pas ces modifications accidentelles.

La façon dont les expressions sont évaluées dans la boîte de message d' **action** peut être différente de celle utilisée actuellement pour le développement. Par exemple, pour générer une chaîne, vous n’avez pas besoin d’encapsuler un message entre guillemets, même si vous utilisez `Debug.WriteLine()` ou `console.log()`. En outre, la syntaxe de l’accolade (`{ }`) aux expressions de sortie peut également être différente de la Convention pour sortir des valeurs dans votre langage de développement. (Toutefois, le contenu entre accolades (`{ }`) doit toujours être écrit à l’aide de la syntaxe de votre langage de développement).

Si vous essayez de déboguer une application active et de rechercher une fonctionnalité similaire, consultez notre fonctionnalité point dans le Débogueur de capture instantanée. Le débogueur de capture instantanée est un outil utilisé pour étudier les problèmes dans les applications de production. Points vous permet également d’envoyer des messages au Fenêtre Sortie sans avoir à modifier le code source et à n’affecter pas votre application en cours d’exécution. Pour plus d’informations, consultez [déboguer une application Azure en direct](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Voir aussi

- [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)
- [Écrire du C# code de meilleure qualité à l’aide de Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Premier aperçu du débogage](../debugger/debugger-feature-tour.md)
- [Expressions dans le débogueur](expressions-in-the-debugger.md)
- [Utiliser des points d’arrêt](../debugger/using-breakpoints.md)
- [Déboguer des applications Azure en direct](../debugger/debug-live-azure-applications.md)
