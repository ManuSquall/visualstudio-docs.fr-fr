---
title: Débogage avec Visual Studio pour Mac
description: Le débogage est une partie courante et nécessaire de la programmation. Étant un IDE arrivé à maturité, Visual Studio pour Mac contient une suite complète de fonctionnalités facilitant le débogage. Du débogage sans échec à la visualisation des données, cet article explique comment utiliser tout le potentiel du débogage dans Visual Studio pour Mac.
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: 8a12880c25e980d668351ef4c24ced1e479577d4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75397921"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Débogage avec Visual Studio pour Mac

Visual Studio for Mac a débogénaires avec le soutien de .Net Core, .NET Framework, Unity, et Xamarin applications.

Visual Studio pour Mac utilise le [*débogueur Mono Soft*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), qui est implémenté dans le runtime Mono, ce qui permet de Visual Studio pour Mac de déboguer du code managé sur toutes les plateformes.

## <a name="the-debugger"></a>Le débogueur

Visual Studio pour Mac utilise le débogueur Mono Soft pour déboguer le code managé (C# ou F#) dans toutes les applications Xamarin. Le débbugger Mono Soft est différent des débbuggers réguliers en ce qu’il est un débbugger coopératif qui est intégré dans le runtime Mono; le code généré et le temps d’exécution Mono coopèrent avec l’IDE pour fournir une expérience de débogage. Le runtime Mono expose les fonctionnalités de débogage via un protocole connecté, sur lequel vous pouvez trouver plus d’informations [dans la documentation Mono](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Les débogueurs « durs », comme [LLDB]( http://lldb.llvm.org/index.html) ou [GDB]( https://www.gnu.org/software/gdb/), contrôlent un programme sans connaissance ou coopération du programme débogué, mais ils peuvent néanmoins être utiles lors du débogage d’applications de Xamarin dans le cas où vous devez déboguer du code iOS ou Android natif.

Pour les applications .NET Core et ASP.NET Core, Visual Studio for Mac utilise le débâillement .NET Core. Ce débbugger est également un débbugger coopératif et travaille avec le runtime .NET.

## <a name="using-the-debugger"></a>Utilisation du débogueur

Pour démarrer le débogage d’une application, vérifiez toujours que la configuration est définie sur **Debug**. La configuration Debug fournit un ensemble pratique d’outils pour prendre en charge le débogage, comme les points d’arrêt, l’utilisation de visualiseurs de données et l’affichage de la pile des appels :

![Configuration Debug](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Définition d'un point d'arrêt

Pour définir un point d’arrêt dans votre IDE, cliquez sur la zone de marge de votre éditeur, en regard du numéro de ligne où vous voulez marquer un arrêt :

![Définition d’un point d’arrêt dans la marge](media/debugging-image0.png)

Vous pouvez afficher tous les points d’arrêt qui ont été définis dans votre code en allant sur le **pad Breakpoints**:

![Liste des points d’arrêt](media/debugging-image0a.png)

## <a name="start-debugging"></a>Démarrer le débogage

Pour commencer à débogage, sélectionnez le navigateur cible, l’appareil ou le simulateur/émulateur :

![Configuration](media/debugging-image_0.png)
![Debug Sélectionnez l’appareil cible](media/debugging-image1.png)

Ensuite, déployez votre application en cliquant sur le bouton **Lecture** ou en appuyant sur **Cmd+Entrée**. Quand vous atteignez un point d’arrêt, le code est mis en surbrillance en jaune :

![Mise en surbrillance montrant que le point d’arrêt a été atteint](media/debugging-image2.png)

Des outils de débogage, comme celui utilisé pour inspecter les valeurs des objets, peuvent être utilisés à ce stade pour obtenir plus d’informations sur ce qui se passe dans votre code :

![Visualisations du débogage](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Points d’arrêt conditionnels

Vous pouvez également définir des règles spécifiant les circonstances dans lesquelles un point d’arrêt doit se produire : on parle alors de l’ajout d’un *point d’arrêt conditionnel*. Pour définir un point d’arrêt conditionnel, accédez à la **fenêtre Propriétés de point d’arrêt**, ce que vous pouvez faire de deux façons :

* Pour ajouter un nouveau point d’arrêt conditionnel, cliquez avec le bouton droit sur la marge de l’éditeur, à gauche du numéro de la ligne de code pour laquelle vous voulez définir un point d’arrêt, et sélectionnez Nouveau point d’arrêt :

 ![Menu contextuel Point d'arrêt](media/debugging-image4.png)

* Pour ajouter une condition à un point d’arrêt existant, cliquez sur le point d’arrêt et sélectionnez **Propriétés de point d’arrêt** ou, dans le **panneau Points d’arrêt**, sélectionnez le bouton Modifier le point d’arrêt, comme illustré ci-dessous :

 ![Modifier un point d’arrêt existant dans le panneau Points d’arrêt](media/debugging-image5.png)

Vous pouvez ensuite entrer la condition selon laquelle vous voulez que le point d’arrêt se produise :

 ![Modifier les conditions d’un point d’arrêt](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Exécution de code pas à pas

Quand un point d’arrêt a été atteint, les outils de débogage vous permettent de prendre le contrôle de l’exécution du programme. Visual Studio pour Mac affiche quatre boutons, qui vous permettent d’exécuter le code pas à pas. Dans Visual Studio pour Mac, ils se présentent comme ceci :

 ![Boutons pour parcourir le code pas à pas](media/debugging-image7.png)

Voici les quatre boutons :

* **Lecture** : commence l’exécution du code, jusqu’au point d’arrêt suivant.
* **Étape plus** - Cela exécutera la prochaine ligne de code. Si la ligne suivante est un appel de fonction, Step Over exécutera la fonction, et s’arrêtera à la ligne suivante de code *après* la fonction.
* **Étape -** Cela exécutera également la prochaine ligne de code. Si la ligne suivante est un appel de fonction, Pas à pas détaillé s’arrête à la première ligne de la fonction, ce qui vous permet de continuer le débogage ligne par ligne de la fonction. Si la ligne suivante n’est pas une fonction, il se comporte comme Pas à pas principal.
* **Sortir** - Cela reviendra à la ligne où la fonction actuelle a été appelée.

## <a name="debugging-monos-class-libraries"></a>Débogage des bibliothèques de classes de Mono

Les produits Xamarin sont livrés avec le code source pour les bibliothèques de classes de Mono, que vous pouvez utiliser pour avancer pas à pas à partir du débogueur pour examiner comment les choses fonctionnent à l’arrière-plan.

Comme cette fonctionnalité consomme plus de mémoire pendant le débogage, elle est désactivée par défaut.

Pour activer cette fonctionnalité, rendez-vous sur **Visual Studio pour Mac > Préférences > Debugger** et assurez-vous que l’option « Step into external**code**» est **sélectionnée,** comme illustré ci-dessous :

![Entrez dans l’option de code externe](media/debugging-image8.png)

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio (sur Windows)](/visualstudio/debugger/)
