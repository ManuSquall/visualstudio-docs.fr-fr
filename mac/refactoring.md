---
title: Refactorisation du code
description: La réorganisation du code dans Visual Studio pour Mac est simplifiée via l’utilisation de l’analyse du code source.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: d7df01e2d2c6e4acb347b40cb82a04bee9394fe1
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335387"
---
# <a name="refactoring"></a>Refactorisation

La refactorisation du code consiste à réorganiser, restructurer et clarifier le code existant tout en garantissant que le comportement global du code ne change pas.

Elle génère une base de code plus saine, rendant le code plus utilisable, lisible et gérable pour vous ou pour tout autre développeur ou utilisateur susceptible de faire référence au code.

L’intégration de Visual Studio pour Mac à Roslyn, la plateforme de compilateurs .NET open source de Microsoft, permet une refactorisation plus importante.

## <a name="renaming"></a>Renommage

La commande de refactorisation *Renommer* peut être utilisée sur n’importe quel identificateur du code (par exemple un nom de classe, un nom de propriété, etc.) pour rechercher toutes les occurrences de cet identificateur et les changer. Pour renommer un symbole, cliquez avec le bouton droit sur celui-ci et choisissez **Refactoriser > Renommer**, ou la combinaison de touches **Cmd+R** :

![Élément de menu Renommer](media/refactoring-renaming1.png)

Ceci met en évidence le symbole et toutes les références à celui-ci. Quand vous commencez à taper un nouveau nom, il change automatiquement toutes les références dans votre code. Vous pouvez indiquer que le renommage a été effectué en appuyant sur **Entrée** :

![Renommage et identificateur](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Actions contextuelles

Les actions contextuelles vous permettent d’inspecter le code C# et de voir toutes les options de refactorisation possibles.

Les éléments contextuels **Résoudre** et **Refactoriser** sont combinés en un seul élément *Correction rapide...* qui vous propose toutes les actions contextuelles disponibles :

![Afficher les éléments contextuels](media/refactoring-context-action.png)

En passant le pointeur de la souris sur les actions contextuelles, vous obtenez un aperçu de ce qui est ajouté ou supprimé dans votre code.

Vous pouvez aussi appuyer sur **Option+Entrée** n’importe où dans votre code :

![Option Entrer les éléments contextuels](media/refactoring-image2a.png)

Pour activer ces options, vous devez sélectionner *Activer l’analyse du code source des fichiers ouverts* dans les options de **Visual Studio pour Mac > Préférences > Éditeur de texte > Analyse du code source** :

![Activer l’analyse du code source](media/refactoring-options.png)

Il existe plus de 100 actions possibles qui peuvent être suggérées, qui sont activées ou désactivées en accédant à **Visual Studio pour Mac > Préférences > Analyse du code source > C# > Actions de code**, et en cochant ou en décochant la case en regard de l’action :

![Actions de l’analyse du code source C#](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Actions contextuelles courantes

Certaines des actions contextuelles les plus couramment utilisées sont expliquées ci-dessous.

#### <a name="extract-method"></a>Extraire la méthode

L’opération de refactorisation Extraire la méthode vous permet de créer une nouvelle méthode en extrayant une sélection de code dans un membre existant. Cette action effectue deux opérations :

* Elle crée une méthode qui contient le code sélectionné.
* Elle appelle la nouvelle méthode là où se trouvait le code sélectionné.

##### <a name="example"></a>Exemple

1. Ajoutez le code suivant :

```csharp
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Mettez en surbrillance la ligne `double volume = (baseArea * height) / 3;`, cliquez avec le bouton droit sur celle-ci et sélectionnez **Refactoriser > Extraire la méthode**.

3. Utilisez les touches de direction pour sélectionner l’emplacement de la nouvelle méthode dans votre code.

#### <a name="encapsulate-field"></a>Encapsuler le champ

L’opération Encapsuler le champ vous permet de créer une propriété à partir d’un champ existant et met à jour votre code pour référencer la propriété nouvellement créée. En créant une propriété qui encapsule votre champ, vous empêchez un accès direct à votre champ public, ce qui signifie que qu’autres objets ne peuvent pas le modifier.

Cette action effectue les opérations suivantes :

* Elle change le modificateur d’accès en privé.
* Elle génère une méthode getter et une méthode setter pour le champ (sauf si le champ est en lecture seule, auquel cas elle crée seulement une méthode getter).

## <a name="source-analysis"></a>Analyse du code source

L’analyse du code source analyse votre code à la volée. Elle souligne les erreurs potentielles et les violations de style, et fournit des corrections automatiques sous forme d’actions contextuelles.

Vous pouvez voir tous les résultats de l’analyse du code source pour n’importe quel fichier et à tout moment, en consultant la barre de défilement sur le côté droit de l’éditeur de texte :

![Barre latérale Analyse du code source](media/refactoring-image4a.png)

Si vous cliquez sur le cercle en haut, vous pouvez parcourir les différentes suggestions, les problèmes avec la gravité la plus élevée figurant en premier. Passez le pointeur sur un résultat ou une ligne individuelle pour afficher le problème. Vous pouvez alors le corriger via des actions contextuelles :

![Élément d’analyse du code source](media/refactoring-image5.png)

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Voir aussi

- [Actions rapides (Visual Studio sur Windows)](/visualstudio/ide/quick-actions)
- [Refactoriser du code (Visual Studio sur Windows)](/visualstudio/ide/refactoring-in-visual-studio)