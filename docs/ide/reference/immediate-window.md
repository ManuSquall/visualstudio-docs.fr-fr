---
title: Fenêtre Exécution
description: Découvrez comment utiliser la fenêtre exécution pour déboguer et évaluer des expressions, exécuter des instructions et imprimer des valeurs de variables.
ms.custom: SEO-VS-2020
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73d3d2cc42e958c59ef058a1f69921145ea18475
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852477"
---
# <a name="immediate-window"></a>Exécution (fenêtre)

Utilisez la fenêtre **Exécution** pour déboguer et évaluer des expressions, exécuter des instructions et imprimer les valeurs de variables. La fenêtre **Exécution** évalue les expressions en générant et en utilisant le projet actuellement sélectionné.

Pour afficher la fenêtre **Exécution**, ouvrez un projet à modifier, puis choisissez **Déboguer** > **Fenêtres** > **Exécution** ou appuyez sur **Ctrl**+**Alt**+**I**. Vous pouvez également entrer **Debug.Immediate** dans la fenêtre **Commande**.

La fenêtre **Exécution** prend en charge IntelliSense.

## <a name="display-the-values-of-variables"></a>Afficher les valeurs de variables

La fenêtre **Exécution** est particulièrement utile lors du débogage d’une application. Par exemple, pour vérifier la valeur d’une variable `varA`, vous pouvez utiliser la [commande Imprimer](../../ide/reference/print-command.md) :

```cmd
>Debug.Print varA
```

Le point d’interrogation (?) est un alias pour `Debug.Print` et cette commande peut donc également s’écrire comme suit :

```cmd
? varA
```

Les deux versions de cette commande retournent la valeur de la variable `varA`.

> [!TIP]
> Pour émettre une commande Visual Studio dans la fenêtre **Exécution**, vous devez faire précéder la commande d’un signe supérieur à (>). Pour entrer plusieurs commandes, passez à la [Fenêtre Commande](command-window.md).

## <a name="design-time-expression-evaluation"></a>Évaluation des expressions au moment du design

Vous pouvez utiliser la fenêtre **Exécution** pour exécuter une fonction ou une sous-routine au moment du design.

### <a name="execute-a-function-at-design-time"></a>Exécuter une fonction au moment du design

1. Copiez le code suivant dans une application console Visual Basic :

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. Dans le menu **Déboguer**, choisissez **Windows** > **Exécution**.

3. Tapez `?MyFunction(2)` dans la fenêtre **Exécution** et appuyez sur **Entrée**.

    La fenêtre **Exécution** exécute `MyFunction` et affiche `4`.

Si la fonction ou la sous-routine contient un point d’arrêt, Visual Studio arrête l’exécution à ce point. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Pour plus d’informations, consultez [procédure pas à pas : débogage au moment du design](../../debugger/walkthrough-debugging-at-design-time.md).

Vous ne pouvez pas utiliser l’évaluation des expressions au moment du design dans les types de projet qui requièrent le démarrage d’un environnement d’exécution, notamment les projets Visual Studio Tools pour Office, projets web, projets Smart Device et projets SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Évaluation des expressions au moment du design dans les solutions à projets multiples

Lors de l’établissement du contexte pour l’évaluation des expressions au moment du design, Visual Studio référence le projet actuellement sélectionné dans l’Explorateur de solutions. Si aucun projet n’est sélectionné dans l’Explorateur de solutions, Visual Studio tente alors d’évaluer la fonction par rapport au projet de démarrage. Si la fonction ne peut pas être évaluée dans le contexte actuel, un message d’erreur s’affiche. Si vous essayez d’évaluer une fonction dans un projet qui n’est pas le projet de démarrage pour la solution et que vous recevez une erreur, essayez de sélectionner le projet dans l’Explorateur de solutions et tentez à nouveau l’évaluation.

## <a name="enter-commands"></a>Entrer des commandes

Vous devez entrer le signe supérieur à (>) lors de l’émission de commandes Visual Studio dans la fenêtre **Exécution**. Utilisez les touches **Haut** et **Bas** pour faire défiler les commandes précédemment utilisées.

|Tâche|Solution|Exemple|
|----------|--------------|-------------|
|Évaluer une expression.|Faites précéder l’expression d’un point d’interrogation (?).|`? a+b`|
|En mode Exécution, passer temporairement en mode Commande (pour exécuter une seule commande).|Entrez la commande en la faisant précéder du signe supérieur à (>).|`>alias`|
|Basculer vers la fenêtre Commande.|Entrez la commande `cmd` dans la fenêtre en la faisant précéder du signe supérieur à (>).|`>cmd`|
|Revenir à la fenêtre Exécution.|Entrez la commande `immed` dans la fenêtre sans le signe supérieur à (>).|`immed`|

## <a name="mark-mode"></a>Mode Marque

Quand vous cliquez sur n’importe quelle ligne précédente dans la fenêtre **Exécution**, vous passez automatiquement en mode Marque. Cela vous permet de sélectionner, de modifier et de copier le texte de commandes précédentes comme vous le feriez dans n’importe quel éditeur de texte, et de les coller dans la ligne active.

## <a name="examples"></a>Exemples

L’exemple suivant montre les quatre expressions et leurs résultats dans la fenêtre **Exécution** pour un projet Visual Basic.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>Notifications d’exceptions de première chance

Dans certaines configurations de paramètres, les notifications d’exceptions de première chance sont affichées dans la fenêtre **Exécution**.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Activer/désactiver les notifications d’exceptions de première chance dans la fenêtre Exécution

1. Dans le menu **Affichage**, cliquez sur **Autres fenêtres**, puis sur **Sortie**.

2. Cliquez avec le bouton droit sur la zone de texte de la fenêtre **Sortie**, puis sélectionnez ou désélectionnez **Messages d’exception**.

## <a name="see-also"></a>Voir aussi

- [Naviguer dans le code avec le débogueur](../../debugger/navigating-through-code-with-the-debugger.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Présentation du débogueur](../../debugger/debugger-feature-tour.md)
- [Procédure pas à pas : débogage au moment du design](../../debugger/walkthrough-debugging-at-design-time.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Utilisation d’expressions régulières dans Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
