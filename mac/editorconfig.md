---
title: EditorConfig
description: Utilisation d’un fichier editorconfig pour assurer la cohérence des styles de codage de projet dans Visual Studio pour Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 336ec5ef0779bcd67302bea7b51851dced531a7d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957387"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Création et modification d’un fichier EditorConfig personnalisé

Dans Visual Studio pour Mac, vous pouvez ajouter un fichier [EditorConfig](http://editorconfig.org/) à votre projet ou code base pour que tous les utilisateurs qui travaillent dans le code base utilisent des styles de codage cohérents. Les paramètres déclarés dans le fichier EditorConfig sont prioritaires par rapport aux paramètres globaux de l’éditeur de texte Visual Studio. L’utilisation d’un fichier EditorConfig dans votre projet ou code base vous permet de définir un style de codage, des préférences et des avertissements pour votre projet. Tous les utilisateurs de Visual Studio pour Mac peuvent ainsi adhérer plus facilement aux pratiques de codage d’un projet.

Les fichiers [EditorConfig](http://editorconfig.org/) sont pris en charge sur de nombreux IDE et éditeurs de code, notamment Visual Studio 2017. 

## <a name="supported-settings"></a>Paramètres pris en charge

L’éditeur de Visual Studio prend en charge l’ensemble principal des [propriétés d’EditorConfig](http://editorconfig.org/#supported-properties) :

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig prend également en charge la [mise en forme du style de code](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) en C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Ajouter un fichier EditorConfig à un projet

### <a name="adding-a-new-editorconfig-file"></a>Ajout d’un nouveau fichier EditorConfig

1. Ouvrez votre projet dans Visual Studio pour Mac. Sélectionnez le nœud de projet auquel vous souhaitez ajouter des fichiers.

2. Une fois le nœud de projet sélectionné, cliquez sur **Fichier > Nouveau fichier** dans la barre de menus pour ouvrir la boîte de dialogue **Nouveau fichier**.

3. Choisissez **Divers > Fichier texte vide** et donnez-lui le **Nom** `.editorconfig`. Appuyez sur **Nouveau** pour créer le fichier et l’ouvrir dans l’éditeur :

    ![Boîte de dialogue Nouveau fichier](media/editorconfig-image1.png)

4. Modifiez le fichier. Exemple :

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Le fait d’ajouter le fichier ne met pas automatiquement à jour vos paramètres. Pour refléter les paramètres du fichier `.editorconfig`, sélectionnez le nœud de projet et choisissez **Edition > Mettre en forme > Mettre en forme le document** dans la barre de menus :

    ![Élément de menu Mettre en forme le document](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Ajout d’un fichier EditorConfig existant

Si votre projet ou solution contient déjà un fichier `.editorconfig`, aucune intervention de votre part n’est nécessaire pour appliquer les paramètres. Les nouvelles lignes de code sont mises en forme conformément aux paramètres EditorConfig. Bien que Visual Studio pour Mac respecte les fichiers `.editorconfig` au niveau de la solution, il est possible qu’ils n’apparaissent pas dans le Panneau Solutions étant donné que les fichiers commençant par `.` sont masqués dans macOS.

Vous pouvez réutiliser un fichier `.editorconfig` existant dans votre projet. Pour ajouter un fichier existant, vous devez d’abord afficher les fichiers masqués dans le Finder en entrant la commande suivante dans **Terminal** :

```bash
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

Une fois le fichier `.editorconfig` visible, faites-le glisser sur votre nœud de projet. Quand la boîte de dialogue suivante s’affiche, sélectionnez l’option **Copier le fichier dans le répertoire** et sélectionnez **OK** :

![Élément de menu Mettre en forme le document](media/editorconfig-image3.png)

Pour refléter les paramètres du fichier `.editorconfig`, sélectionnez le nœud de projet et choisissez **Edition > Mettre en forme > Mettre en forme le document** dans la barre de menus.

## <a name="editing-an-editorconfig-file"></a>Modification d’un fichier EditorConfig

Pour spécifier des paramètres, les fichiers EditorConfig utilisent une disposition de fichier simple qui est expliquée ci-dessous au moyen d’un exemple précédent :


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Le fait de définir `root` avec la valeur `true` marque ce fichier comme étant au sommet du code base. Tout fichier `.editorconfig` situé plus haut dans le projet est alors ignoré, comme l’explique la section [Substituer les paramètres d’EditorConfig](#override-editorconfig-settings).

Chaque section, dénotée par des crochets (**[]**), spécifie des informations sur les types de fichiers auxquels les propriétés suivantes se rapportent.

Dans l’exemple ci-dessus, certains paramètres sont appliqués à tous les fichiers du projet tandis que d’autres sont ajoutés uniquement aux fichiers C#. Les captures d’écran ci-dessous montrent une section de code avant et après l’application des paramètres `.editorconfig` :

**Avant** :

![Avant l’application des paramètres editorconfig](media/editorconfig-image4.png)

**Après** :

![Après l’application des paramètres editorconfig](media/editorconfig-image5.png)

Pour plus d’informations sur les paramètres EditorConfig disponibles, consultez l’article [Paramètres des conventions de codage .NET pour EditorConfig](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) et la section [Propriétés prises en charge](http://editorconfig.org/#supported-properties) dans la documentation officielle.

## <a name="override-editorconfig-settings"></a>Substituer les paramètres d’EditorConfig

Vous pouvez avoir plusieurs fichiers `.editorconfig` dans chaque solution. Visual Studio pour Mac lit les fichiers `.editorconfig` de haut en bas dans la solution, ajoutant et substituant des paramètres au fur et à mesure. Cela signifie que les paramètres dans le fichier `.editorconfig` _le plus près_ du fichier que vous modifiez sont prioritaires. 

Pour être sûr _qu’aucun_ paramètre de fichiers `.editorconfig` de niveau supérieur n’est appliqué à cette partie du code base, ajoutez la propriété `root=true` au fichier `.editorconfig` de niveau inférieur :

```EditorConfig
# top-most EditorConfig file
root = true
```