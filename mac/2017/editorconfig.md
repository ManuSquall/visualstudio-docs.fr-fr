---
title: EditorConfig
description: Utilisation d’un fichier editorconfig pour assurer la cohérence des styles de codage de projet dans Visual Studio pour Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: d42103d17b64ee9b3fb2a0660017824490655808
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998775"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Création et modification d’un fichier EditorConfig personnalisé

Dans Visual Studio pour Mac, vous pouvez ajouter un fichier [EditorConfig](http://editorconfig.org/) à votre projet ou votre solution pour permettre à tous ceux qui travaillent dans le code base d’utiliser des styles de codage cohérents. Les paramètres déclarés dans le fichier EditorConfig sont prioritaires sur les paramètres globaux de l’éditeur de texte de Visual Studio pour Mac. L’utilisation d’un fichier EditorConfig dans votre projet ou code base vous permet de définir le style de codage, les préférences et les avertissements relatifs à votre projet. Dans la mesure où le fichier fait partie de votre code base, il est plus facile pour l’ensemble des utilisateurs d’adhérer aux pratiques de codage d’un projet, quel que soit l’IDE ou l’éditeur de code utilisé.

Les fichiers [EditorConfig](http://editorconfig.org/) sont pris en charge sur de nombreux IDE et éditeurs de code, notamment Visual Studio 2017.

## <a name="supported-settings"></a>Paramètres pris en charge

L’éditeur de Visual Studio pour Mac prend en charge le jeu principal de [propriétés EditorConfig](http://editorconfig.org/#supported-properties) :

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig prend également en charge les [conventions de codage](/visualstudio/ide/editorconfig-code-style-settings-reference) en C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Ajouter un fichier EditorConfig à un projet

### <a name="adding-a-new-editorconfig-file"></a>Ajout d’un nouveau fichier EditorConfig

1. Ouvrez votre projet dans Visual Studio pour Mac. Sélectionnez la solution ou le nœud de projet auquel vous souhaitez ajouter le fichier EditorConfig. L’ajout du fichier au répertoire de la solution permet d’appliquer les paramètres du fichier .editorconfig à tous les projets de la solution.

2. Cliquez avec le bouton droit sur le nœud, puis sélectionnez **Ajouter > Nouveau fichier** pour ouvrir la boîte de dialogue **Nouveau fichier** :

    ![Éléments de menu de contenu](media/editorconfig-image0.png)

3. Choisissez **Divers > Fichier texte vide** et donnez-lui le **Nom** `.editorconfig`. Appuyez sur **Nouveau** pour créer le fichier et l’ouvrir dans l’éditeur :

    ![Boîte de dialogue Nouveau fichier](media/editorconfig-image1.png)

    L’ajout de l’élément au niveau de la solution permet de le créer et de l’imbriquer automatiquement dans un dossier **Éléments de solution** :

    ![Élément de solution affiché dans le panneau Solutions](media/editorconfig-image1a.png)

4. Modifiez le fichier. Par exemple :

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

4. Les paramètres du fichier `.editorconfig` s’appliquent au nouveau code que vous écrivez. Toutefois, vous devrez peut-être remettre en forme le code existant pour qu’il soit cohérent par rapport aux nouveaux paramètres. Pour appliquer les paramètres du fichier `.editorconfig` à un fichier source existant, ouvrez le fichier, puis choisissez **Edition > Format > Mettre le document en forme** dans la barre de menus :

    ![Élément de menu Mettre en forme le document](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Ajout d’un fichier EditorConfig existant

Si votre projet ou solution contient déjà un fichier `.editorconfig`, aucune intervention de votre part n’est nécessaire pour appliquer les paramètres. Les nouvelles lignes de code sont mises en forme conformément aux paramètres EditorConfig.

Vous pouvez réutiliser un fichier `.editorconfig` existant dans votre projet. Pour ajouter un fichier existant, effectuez ce qui suit :

1. Cliquez avec le bouton droit sur le dossier à ajouter, puis sélectionnez **Ajouter > Ajouter des fichiers**.

2. Accédez au répertoire du fichier nécessaire.

3. Les fichiers qui commencent par `.` (par exemple `.editorconfig`) sont des fichiers masqués dans macOS. Vous devez donc appuyer sur **Commande + Maj + .** pour rendre le fichier `.editorconfig` visible.

4. Sélectionnez le fichier `.editorconfig`, puis cliquez sur **Ouvrir** :

    ![fenêtre d’ajout de nouveau fichier](media/editorconfig-image3b.png)

5. Quand la boîte de dialogue suivante s’affiche, sélectionnez l’option **Copier le fichier dans le répertoire** et sélectionnez **OK** :

    ![Options de la boîte de dialogue Ajouter un fichier à un dossier](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Reflet des paramètres du fichier .editorconfig

Une fois que vous avez ajouté un fichier EditorConfig à votre code base, tout nouveau code ajouté est automatiquement mis en forme en fonction des paramètres spécifiés. Le code existant ne reflète pas automatiquement les paramètres, sauf si vous mettez en forme le code base.

Pour refléter les paramètres du fichier `.editorconfig`, sélectionnez le nœud de solution, puis choisissez **Edition > Format > Mettre le document en forme** dans la barre de menus :

![Option Mettre le document en forme de la barre de menus](media/editorconfig-image3a.png)

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

Si vous affectez à `root` la valeur `true`, ce fichier est marqué comme étant au sommet du code base. Tout fichier `.editorconfig` situé plus haut dans le projet est ignoré, comme l’explique la section [Substituer les paramètres d’EditorConfig](#override-editorconfig-settings).

Chaque section, dénotée par des crochets (**[]**), spécifie des informations sur les types de fichiers auxquels les propriétés suivantes se rapportent.

Dans l’exemple ci-dessus, certains paramètres sont appliqués à tous les fichiers du projet tandis que d’autres sont ajoutés uniquement aux fichiers C#. Les captures d’écran ci-dessous montrent une section de code avant et après l’application des paramètres `.editorconfig` :

**Avant** :

![Avant l’application des paramètres editorconfig](media/editorconfig-image4.png)

**Après** :

![Après l’application des paramètres editorconfig](media/editorconfig-image5.png)

Pour plus d’informations sur les paramètres EditorConfig disponibles, consultez l’article [Paramètres des conventions de codage .NET pour EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) et la section [Propriétés prises en charge](http://editorconfig.org/#supported-properties) dans la documentation officielle.

## <a name="override-editorconfig-settings"></a>Substituer les paramètres d’EditorConfig

Vous pouvez avoir plusieurs fichiers `.editorconfig` dans chaque solution. Visual Studio pour Mac lit les fichiers `.editorconfig` de haut en bas dans la solution, en ajoutant et en remplaçant les paramètres au fur et à mesure. Cela signifie que les paramètres de `.editorconfig` _les plus proches_ du fichier que vous modifiez sont prioritaires. Les paramètres sont extraits du fichier `.editorconfig` du même dossier (s’il existe), puis de `.editorconfig` dans le dossier parent (s’il existe), etc. jusqu’à ce que `root=true` soit trouvé.

Pour être sûr _qu’aucun_ paramètre de fichiers `.editorconfig` de niveau supérieur n’est appliqué à cette partie du code base, ajoutez la propriété `root=true` au fichier `.editorconfig` de niveau inférieur :

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Voir aussi

- [Créer des paramètres d’éditeur personnalisés avec EditorConfig (Visual Studio sur Windows)](/visualstudio/ide/create-portable-custom-editor-options)