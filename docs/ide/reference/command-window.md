---
title: Fenêtre Commande
description: Découvrez comment vous pouvez utiliser le Fenêtre Commande pour exécuter des commandes ou des alias directement dans l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e133f20464fb19752c7616d2fab1a631fa802c9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040887"
---
# <a name="command-window"></a>Fenêtre Commande
La fenêtre **Commande** est utilisée pour exécuter des commandes ou des alias directement dans l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Vous pouvez exécuter à la fois les commandes de menu et les commandes qui n’apparaissent dans aucun menu. Pour afficher la fenêtre **Commande**, sélectionnez **Autres fenêtres** dans le menu **Affichage** et choisissez **Fenêtre Commande**.

## <a name="displaying-the-values-of-variables"></a>Affichage des valeurs de variables
Pour vérifier la valeur d’une variable `varA`, utilisez la [commande Imprimer](../../ide/reference/print-command.md) :

```cmd
>Debug.Print varA
```

Le point d’interrogation (?) est un alias pour `Debug.Print` et cette commande peut donc également s’écrire comme suit :

```cmd
>? varA
```

Les deux versions de cette commande retournent la valeur de la variable `varA`.

## <a name="entering-commands"></a>Entrée de commandes
Le symbole supérieur à (`>`) apparaît à gauche de la fenêtre Commande comme une invite pour les nouvelles lignes. Utilisez les touches de direction HAUT et BAS pour faire défiler les commandes précédemment émises.

|Tâche|Solution|Exemple|
|----------|--------------|-------------|
|Évaluer une expression.|Faites précéder l’expression d’un point d’interrogation (`?`).|`? myvar`|
|Basculer vers une fenêtre Exécution.|Entrez `immed` dans la fenêtre sans le signe supérieur à (>)|`immed`|
|Revenir à la fenêtre Commande à partir d’une fenêtre Exécution.|Entrez `cmd` dans la fenêtre.|`>cmd`|

Les raccourcis suivants vous aident à naviguer en mode Commande.

|Action|Emplacement du curseur|Combinaison de touches|
|------------| - |----------------|
|Parcourir la liste des commandes précédemment entrées.|Ligne d’entrée|HAUT et BAS|
|Faire défiler le contenu de la fenêtre vers le haut.|Contenu de la fenêtre Commande|Ctrl+Haut|
|Faire défiler le contenu de la fenêtre vers le bas.|Contenu de la fenêtre Commande|BAS ou CTRL+BAS|

> [!TIP]
> Vous pouvez copier une commande antérieure, en partie ou en totalité, vers la ligne d’entrée : à cet effet, faites défiler le contenu de la fenêtre jusqu’à la commande voulue, mettez en surbrillance le texte à copier, puis appuyez sur Entrée.

## <a name="mark-mode"></a>Mode Marque
Quand vous cliquez sur n’importe quelle ligne précédente dans la fenêtre **Commande**, vous passez automatiquement en mode Marque. Cela vous permet de sélectionner, de modifier et de copier le texte de commandes précédentes comme vous le feriez dans n’importe quel éditeur de texte, et de les coller dans la ligne active.

## <a name="the-equals--sign"></a>Signe égal (=)
La fenêtre utilisée pour entrer la commande `EvaluateStatement` détermine si un signe égal (=) est interprété comme un opérateur de comparaison ou comme un opérateur d’assignation.

Dans la fenêtre **Commande**, un signe égal (=) est interprété comme un opérateur de comparaison. Vous ne pouvez pas utiliser d’opérateurs d’assignation dans la fenêtre **Commande**. Ainsi, si les valeurs des variables `varA` et `varB` sont différentes, la commande `>Debug.EvaluateStatement(varA=varB)` retourne la valeur `False`.

Dans la fenêtre **Exécution**, en revanche, un signe égal (=) est interprété comme un opérateur d’assignation. Ainsi, la commande `>Debug.EvaluateStatement(varA=varB)` assigne à la variable `varA` la valeur de variable `varB`.

## <a name="parameters-switches-and-values"></a>Paramètres, commutateurs et valeurs
Certaines commandes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ont des arguments, des commutateurs et des valeurs obligatoires et facultatifs. L’utilisation de ces commandes est régie par un ensemble de règles spécifiques. La commande complexe suivante est un exemple de commande destiné à clarifier la terminologie employée.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

Dans cet exemple,

- `Edit.ReplaceInFiles` est la commande

- `/case` et `/pattern:regex` sont des commutateurs (précédés de la barre oblique [/])

- `regex` est la valeur du commutateur `/pattern` ; le commutateur `/case` n’a pas de valeur

- `var[1-3]+` et `oldpar` sont des paramètres

    > [!NOTE]
    > Les commandes, paramètres, commutateurs ou valeurs qui comportent des espaces doivent être entourés de guillemets doubles.

Les commutateurs et les paramètres peuvent être placés à n’importe quel endroit de la ligne de commande, à l’exception de la commande [Shell](../../ide/reference/shell-command.md), dont les commutateurs et les paramètres doivent respecter un ordre précis.

Pratiquement tous les commutateurs pris en charge par une commande peuvent avoir deux formes : une abrégée (un seul caractère) et une longue. Plusieurs commutateurs de forme abrégée peuvent être regroupés. Par exemple, `/p /g /m` peut aussi être spécifié sous la forme `/pgm`.

Quand une valeur est attribuée à un groupe de commutateurs de forme abrégée, cette valeur s’applique à chacun des commutateurs. Par exemple, `/pgm:123` équivaut à `/p:123 /g:123 /m:123`. Si l’un des commutateurs du groupe n’accepte pas la valeur spécifiée, une erreur se produit.

## <a name="escape-characters"></a>Caractères d’échappement
La présence d’un signe d’insertion (^) dans une ligne de commande signifie que le caractère situé juste après ce signe est interprété littéralement, et non comme un caractère de contrôle. Ceci permet d’incorporer des guillemets ("), des espaces, des barres obliques, des accents circonflexes ou tout autre caractère littéral dans une valeur de paramètre ou de commutateur, à l’exception des noms de commutateur. Par exemple,

```cmd
>Edit.Find ^^t /regex
```

Un accent circonflexe fonctionne de la même façon, qu’il soit à l’intérieur ou en dehors des guillemets. Si un accent circonflexe est le dernier caractère de la ligne, il est ignoré. L’exemple illustré ici montre comment rechercher le modèle « ^t ».

## <a name="use-quotes-for-path-names-with-spaces"></a>Utiliser des guillemets pour les noms de chemin avec des espaces
Si, par exemple, vous souhaitez ouvrir un fichier qui possède un chemin contenant des espaces, vous devez placer des guillemets doubles autour du chemin ou du segment de chemin contenant des espaces : **C:\\"Program Files"** ou **"C:\Program Files"**.

## <a name="see-also"></a>Voir aussi

- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
