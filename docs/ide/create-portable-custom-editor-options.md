---
title: Utilisation des paramètres EditorConfig dans Visual Studio
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.openlocfilehash: 9758aab8d36b113a5e4ba2fea5d475f1967dabab
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39469052"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Créer des paramètres d’éditeur personnalisés et portables avec EditorConfig

Dans Visual Studio 2017, vous pouvez ajouter un fichier [EditorConfig](http://editorconfig.org/) à votre projet ou code base pour appliquer des styles de codage cohérents pour tous les utilisateurs qui travaillent dans le code base. Les paramètres EditorConfig sont prioritaires par rapport aux paramètres globaux de l’éditeur de texte Visual Studio. Vous pouvez donc personnaliser chaque base de code pour utiliser des paramètres de l’éditeur de texte qui sont propres au projet. Vous pouvez toujours définir vos propres préférences d’éditeur personnelles dans la boîte de dialogue **Options** de Visual Studio. Ces paramètres s’appliquent à chaque fois que vous travaillez dans un codebase sans fichier *.editorconfig*, ou quand le fichier *.editorconfig* ne remplace pas un paramètre particulier. Le style de mise en retrait (tabulations ou espaces) constitue un exemple de préférence de ce type.

Les paramètres EditorConfig sont pris en charge par de nombreux éditeurs de code et IDE, notamment Visual Studio. C’est un composant portable qui accompagne votre code et peut appliquer des styles de codage même en dehors de Visual Studio.

> [!NOTE]
> Quand vous ajoutez un fichier EditorConfig à votre projet dans Visual Studio, la mise en forme du code existant n’est pas modifiée, sauf si vous mettez en forme le document (**Modifier** > **Avancé** > **Mettre le document en forme** ou **Ctrl**+**K**, **Ctrl**+**D**). Toutefois, les nouvelles lignes de code sont mises en forme selon les paramètres EditorConfig.

## <a name="coding-consistency"></a>Cohérence du codage

Les paramètres définis dans les fichiers EditorConfig vous permettent de garantir la cohérence des paramètres et des styles de codage dans une base de code, tels que le style de mise en retrait, la largeur de tabulation, les caractères de fin de ligne et l’encodage, indépendamment de l’éditeur ou de l’IDE que vous utilisez. Par exemple, quand vous codez en C#, si votre codebase a une convention selon laquelle les retraits sont toujours des caractères à cinq espaces, les documents utilisent l’encodage UTF-8 et chaque ligne se termine toujours par un retour chariot/saut de ligne. Pour ce faire, vous pouvez configurer un fichier *.editorconfig*.

Les conventions de codage que vous utilisez dans vos projets personnels peuvent différer de celles utilisées dans les projets de votre équipe. Par exemple, vous préférerez peut-être que lors du codage, la mise en retrait ajoute une tabulation. De son côté, votre équipe préférera peut-être que la mise en retrait ajoute quatre espaces au lieu d’une tabulation. Les fichiers EditorConfig résolvent ce problème en vous permettant d’avoir une configuration pour chaque scénario.

Les paramètres étant contenus dans un fichier dans la base de code, ils se déplacent avec cette base de code. Tant que vous ouvrez le fichier de code dans un éditeur compatible avec EditorConfig, les paramètres de l’éditeur de texte sont implémentés. Pour plus d’informations sur les fichiers EditorConfig, consultez le site web [EditorConfig.org](http://editorconfig.org/).

## <a name="supported-settings"></a>Paramètres pris en charge

L’éditeur de Visual Studio prend en charge l’ensemble principal des [propriétés d’EditorConfig](http://editorconfig.org/#supported-properties) :

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- racine

Les paramètres de l’éditeur EditorConfig sont pris en charge dans tous les langages pris en charge par Visual Studio, à l’exception de XML. Par ailleurs, EditorConfig prend en charge les conventions de [style de code](../ide/editorconfig-code-style-settings-reference.md) et de [nommage](../ide/editorconfig-naming-conventions.md) pour C# et Visual Basic.

## <a name="adding-and-removing-editorconfig-files"></a>Ajout et suppression de fichiers EditorConfig

L’ajout d’un fichier EditorConfig à votre projet ou code base ne convertit pas les styles existants en nouveaux styles. Par exemple, si votre fichier contient des mises en retrait avec des tabulations, et que vous ajoutiez un fichier EditorConfig qui crée des mises en retrait avec des espaces, les tabulations de mise en retrait ne sont pas automatiquement converties en espaces. Toutefois, les nouvelles lignes de code sont mises en forme selon le fichier EditorConfig. Par ailleurs, si vous mettez en forme le document (**Modifier** > **Avancé** > **Mettre le document en forme** ou **Ctrl**+**K**, **Ctrl**+**D**), les paramètres contenus dans le fichier EditorConfig sont appliqués aux lignes de code existantes.

Si vous supprimez un fichier EditorConfig de votre projet ou base de code, vous devez fermer tous les fichiers de code ouverts et les rouvrir pour réappliquer les paramètres généraux de l’éditeur aux nouvelles lignes de code.

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>Pour ajouter un fichier EditorConfig à un projet ou une solution

1. Ouvrez un projet ou une solution dans Visual Studio. Sélectionnez le nœud du projet ou de la solution, selon que vos paramètres *.editorconfig* doivent s’appliquer à tous les projets de la solution ou à un seul. Vous pouvez également sélectionner dans votre projet ou votre solution un dossier auquel ajouter le fichier *.editorconfig*.

1. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément** ou appuyez sur **Ctrl**+**Maj**+**A**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Dans les catégories situées à gauche, choisissez **Général**, puis choisissez le modèle **Fichier texte**. Dans la zone de texte **Nom**, entrez `.editorconfig`, puis choisissez **Ajouter**.

   Un fichier *.editorconfig* s’affiche dans l’explorateur de solutions et s’ouvre dans l’éditeur.

   ![Fichier .editorconfig dans l’Explorateur de solutions](media/editorconfig-in-solution-explorer.png)

1. Modifiez le fichier comme vous le souhaitez, par exemple :

   ```EditorConfig
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

### <a name="other-ways-to-add-an-editorconfig-file"></a>Autres façons d’ajouter un fichier EditorConfig

Il existe d’autres façons d’ajouter un fichier EditorConfig au projet :

- Installez l’[extension des services de langage EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) pour ajouter plus facilement un fichier *.editorconfig* vide au projet. Après avoir installé cette extension, choisissez simplement **Ajouter** > **Fichier .editorconfig** en cliquant avec le bouton droit pour afficher un menu contextuel du nœud de la solution, du nœud de projet ou d’un dossier de l’**Explorateur de solutions**. Cette extension améliore également l’expérience utilisateur permettant de modifier le fichier *.editorconfig*.

   ![Ajouter le fichier .editorconfig avec l’extension](media/editorconfig-extension-add.png)

- Essayez l’[extension IntelliCode](/visualstudio/intellicode/intellicode-visual-studio). Cette extension expérimentale déduit vos styles de code à partir du code existant, puis crée un fichier *.editorconfig* non vide avec vos préférences de style de code déjà définies.

## <a name="override-editorconfig-settings"></a>Substituer les paramètres d’EditorConfig

Quand vous ajoutez un fichier *.editorconfig* à un dossier de votre hiérarchie de fichiers, ses paramètres s’appliquent à tous les fichiers concernés situés au même niveau et en dessous. Vous pouvez également remplacer les paramètres EditorConfig d’un projet particulier, d’un code base ou d’une partie de code base qui utilise des conventions différentes de celles des autres parties du code base. Ce remplacement peut s’avérer être utile quand vous incorporez du code provenant d’ailleurs et que vous ne voulez pas modifier ses conventions.

Pour remplacer entièrement ou partiellement des paramètres EditorConfig, ajoutez un fichier *.editorconfig* au niveau de la hiérarchie de fichiers à laquelle vous voulez appliquer ces paramètres de remplacement. Les paramètres du nouveau fichier EditorConfig s’appliquent aux fichiers situés au même niveau et dans tous ses sous-répertoires.

![Hiérarchie d’EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Si vous voulez remplacer une partie des paramètres seulement, il suffit de spécifier ces paramètres dans le fichier *.editorconfig*. Seules les propriétés que vous répertoriez explicitement dans le fichier de niveau inférieur sont alors remplacées. Les autres paramètres des fichiers *.editorconfig* de niveau supérieur continuent à s’appliquer. Pour être sûr qu’_aucun_ paramètre _de_ fichiers *.editorconfig* de niveau supérieur n’est appliqué à cette partie du codebase, ajoutez la propriété ```root=true``` au fichier *.editorconfig* de niveau inférieur :

```EditorConfig
# top-most EditorConfig file
root = true
```

Les fichiers EditorConfig sont lus de haut en bas, et les fichiers EditorConfig les plus proches sont lus en dernier. Les conventions des sections correspondantes d’EditorConfig sont appliquées dans l’ordre de leur lecture. Les conventions dans les fichiers les plus proches sont donc prioritaires.

## <a name="editing-editorconfig-files"></a>Modification des fichiers EditorConfig

Visual Studio vous permet de modifier les fichiers *.editorconfig* en fournissant des listes de saisie semi-automatique IntelliSense.

![IntelliSense dans un fichier .editorconfig](media/editorconfig-intellisense-no-extension.png)

Une fois que vous avez modifié un fichier EditorConfig, vous devez recharger vos fichiers de code pour que les nouveaux paramètres prennent effet.

Si vous modifiez de nombreux fichiers *.editorconfig*, l’[extension du service de langage EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) peut vous être utile. Les fonctionnalités de cette extension incluent notamment une mise en surbrillance de la syntaxe, ainsi que des fonctionnalités IntelliSense, de validation et de mise en forme de code améliorées.

![IntelliSense avec l’extension du service de langage EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Exemple

L’exemple suivant montre la mise en retrait d’un extrait de code C# avant et après l’ajout d’un fichier *.editorconfig* au projet. Le paramètre **Tabulations** dans la boîte de dialogue **Options** de l’éditeur de texte Visual Studio est défini pour ajouter des espaces quand vous appuyez sur la touche **Tab**.

![Paramètre de tabulation de l’Éditeur de texte](../ide/media/vside_editorconfig_tabsetting.png)

Comme prévu, un appui sur la touche **Tab** sur la ligne suivante met en retrait la ligne en ajoutant quatre espaces supplémentaires.

![Code avant l’utilisation d’EditorConfig](../ide/media/vside_editorconfig_before.png)

Ajoutez un nouveau fichier appelé *.editorconfig* au projet, avec le contenu suivant. Le paramètre `[*.cs]` signifie que cette modification s’applique uniquement aux fichiers de code C# dans le projet.

```EditorConfig
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Maintenant, quand vous appuyez sur la touche **Tab**, vous obtenez des caractères de tabulation au lieu des espaces.

![Un appui sur la touche Tab ajoute un caractère de tabulation](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Résoudre les problèmes liés aux paramètres d’EditorConfig

Si un fichier EditorConfig se trouve n’importe où dans la structure de répertoire au niveau ou au-dessus de votre projet, Visual Studio applique les paramètres de l’éditeur définis dans ce fichier à votre éditeur. Dans ce cas, vous pouvez voir le message suivant s’afficher dans la barre d’état :

   **« Les préférences utilisateur de ce type de fichier sont remplacées par les conventions de codage de ce projet. »**

Cela signifie que si des paramètres de l’éditeur dans **Outils** > **Options** > **Éditeur de texte** (tels que la taille et le style de mise en retrait, la taille des tabulations ou les conventions de codage) sont définis dans un fichier EditorConfig au niveau du projet ou au-dessus dans la structure des répertoires, les conventions définies dans le fichier EditorConfig remplacent les paramètres définis dans **Options**. Vous pouvez contrôler ce comportement en activant ou en désactivant l’option **Suivre les conventions de codage du projet** dans **Outils** > **Options** > **Éditeur de texte**. Si vous décochez cette option, vous désactivez la prise en charge d’EditorConfig pour Visual Studio.

![Outils Options, Suivre les conventions de codage du projet](media/coding_conventions_option.png)

Vous pouvez rechercher les fichiers *.editorconfig* dans les répertoires parents en ouvrant une invite de commandes et en exécutant la commande suivante à partir de la racine du disque contenant votre projet :

```Shell
dir .editorconfig /s
```

Vous pouvez contrôler la portée de vos conventions EditorConfig en définissant la propriété ```root=true``` dans le fichier *.editorconfig* à la racine de votre référentiel ou dans le répertoire où se trouve votre projet. Visual Studio recherche un fichier nommé *.editorconfig* dans le répertoire du fichier ouvert et dans chaque répertoire parent. La recherche se termine quand il atteint le chemin racine, ou si un fichier *.editorconfig* avec ```root=true``` est trouvé.

## <a name="see-also"></a>Voir aussi

- [Conventions de style du code .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Conventions de nommage .NET](../ide/editorconfig-naming-conventions.md)
- [Prise en charge d’EditorConfig pour un service de langage](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](http://editorconfig.org/)
- [Fonctionnalités de l’éditeur de code](writing-code-in-the-code-and-text-editor.md)