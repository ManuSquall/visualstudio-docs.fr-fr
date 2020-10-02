---
title: Paramètres d’EditorConfig
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: 277e5cd03d4006ced0791356be73ca1fcbe5c217
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659249"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Créer des paramètres d’éditeur personnalisés et portables avec EditorConfig

Vous pouvez ajouter un fichier EditorConfig à votre projet ou code base pour appliquer des styles de codage cohérents pour tous les utilisateurs de la base de code. Les paramètres EditorConfig sont prioritaires par rapport aux paramètres globaux de l’éditeur de texte Visual Studio. Vous pouvez donc personnaliser chaque base de code pour utiliser des paramètres de l’éditeur de texte qui sont propres au projet. Vous pouvez toujours définir vos propres préférences d’éditeur personnelles dans la boîte de dialogue **Options** de Visual Studio. Ces paramètres s’appliquent à chaque fois que vous travaillez dans un codebase sans fichier *.editorconfig*, ou quand le fichier *.editorconfig* ne remplace pas un paramètre particulier. Le style de mise en retrait (tabulations ou espaces) constitue un exemple de préférence de ce type.

Les paramètres EditorConfig sont pris en charge par de nombreux éditeurs de code et IDE, notamment Visual Studio. C’est un composant portable qui accompagne votre code et peut appliquer des styles de codage même en dehors de Visual Studio.

::: moniker range=">=vs-2019"

Quand vous ajoutez un fichier EditorConfig à votre projet dans Visual Studio, les nouvelles lignes de code sont mises en forme en fonction des paramètres de EditorConfig. La mise en forme du code existant n’est pas modifiée, sauf si vous exécutez l’une des commandes suivantes :

 - [Nettoyage du code](../ide/code-styles-and-code-cleanup.md) (**CTRL** + **K**, **CTRL** + **E**), qui applique les paramètres d’espace blanc, tels que le style de retrait, et les paramètres de style de code sélectionnés, comme le tri des `using` directives.
 - **Modifier** > **Paramètres avancés** > **Mettez le document en forme** (ou **Appuyez sur CTRL** + **K**, **CTRL** + **D** dans le profil par défaut), qui n’applique que les paramètres d’espace blanc, tels que le style de retrait.

 ::: moniker-end

::: moniker range="=vs-2017"

Quand vous ajoutez un fichier EditorConfig à votre projet dans Visual Studio, les nouvelles lignes de code sont mises en forme en fonction des paramètres de EditorConfig. La mise en forme du code existant n’est pas modifiée, sauf si vous mettez en forme le document (**modifier**le  >  **Advanced**  >  **document au format** avancé ou **CTRL** + **K**, **CTRL** + **D** dans le profil par défaut). La mise en forme du document affecte uniquement les paramètres d’espace blanc, tels que le style de retrait, sauf si vous avez configuré le document de format pour [effectuer un nettoyage de code supplémentaire](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

Vous pouvez définir les paramètres EditorConfig que la commande **Mettre le document en forme** doit appliquer dans la [page **Options de mise en forme**](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [EditorConfig dans Visual Studio pour Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Cohérence du code

Les paramètres définis dans les fichiers EditorConfig vous permettent de garantir la cohérence des paramètres et des styles de codage dans une base de code, tels que le style de mise en retrait, la largeur de tabulation, les caractères de fin de ligne et l’encodage, indépendamment de l’éditeur ou de l’IDE que vous utilisez. Par exemple, quand vous codez en C#, si votre codebase a une convention selon laquelle les retraits sont toujours des caractères à cinq espaces, les documents utilisent l’encodage UTF-8 et chaque ligne se termine toujours par un retour chariot/saut de ligne. Pour ce faire, vous pouvez configurer un fichier *.editorconfig*.

Les conventions de codage que vous utilisez dans vos projets personnels peuvent différer de celles utilisées dans les projets de votre équipe. Par exemple, vous préférerez peut-être que lors du codage, la mise en retrait ajoute une tabulation. De son côté, votre équipe préférera peut-être que la mise en retrait ajoute quatre espaces au lieu d’une tabulation. Les fichiers EditorConfig résolvent ce problème en vous permettant d’avoir une configuration pour chaque scénario.

Les paramètres étant contenus dans un fichier dans la base de code, ils se déplacent avec cette base de code. Tant que vous ouvrez le fichier de code dans un éditeur compatible avec EditorConfig, les paramètres de l’éditeur de texte sont implémentés. Pour plus d’informations sur les fichiers EditorConfig, consultez le site web [EditorConfig.org](https://editorconfig.org/).

> [!NOTE]
> Les conventions définies dans un fichier EditorConfig ne sont pour l’instant pas applicables dans un pipeline CI/CD comme erreurs ou avertissements de build. Les écarts de style apparaissent seulement dans l’éditeur Visual Studio et dans la **Liste d’erreurs**.

## <a name="supported-settings"></a>Paramètres pris en charge

L’éditeur de Visual Studio prend en charge l’ensemble principal des [propriétés d’EditorConfig](https://editorconfig.org/#supported-properties) :

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- root

Les paramètres de l’éditeur EditorConfig sont pris en charge dans tous les langages pris en charge par Visual Studio, à l’exception de XML. Par ailleurs, EditorConfig prend en charge les conventions de [style de code](/dotnet/fundamentals/code-analysis/code-style-rule-options), notamment celles de [langage](/dotnet/fundamentals/code-analysis/style-rules/language-rules), [mise en forme](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules) et [affectation de noms](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) pour C# et Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Ajout et suppression de fichiers EditorConfig

Lorsque vous ajoutez un fichier EditorConfig à votre projet ou base de code, les nouvelles lignes de code que vous écrivez sont mises en forme en fonction du fichier EditorConfig. Toutefois, l’ajout d’un fichier EditorConfig ne convertit pas les styles existants en nouveaux styles tant que vous ne mettez pas en forme le document ou exécuté le [nettoyage du code](../ide/code-styles-and-code-cleanup.md). Par exemple, si votre fichier contient des mises en retrait avec des tabulations, et que vous ajoutiez un fichier EditorConfig qui crée des mises en retrait avec des espaces, les tabulations de mise en retrait ne sont pas automatiquement converties en espaces. Lorsque vous mettez en forme le document (**modifier**le  >  **Advanced**  >  **document au format** avancé ou **CTRL** + **K**, **CTRL** + **D**), les paramètres d’espace blanc dans le fichier EditorConfig sont appliqués aux lignes de code existantes.

Si vous supprimez un fichier EditorConfig de votre projet ou base de code et souhaitez que les nouvelles lignes de code soient mises en forme en fonction des paramètres de l’éditeur global, vous devez fermer et rouvrir les fichiers de code ouverts.

### <a name="add-an-editorconfig-file-to-a-project"></a>Ajouter un fichier EditorConfig à un projet

1. Ouvrez un projet ou une solution dans Visual Studio. Sélectionnez le nœud du projet ou de la solution, selon que vos paramètres *.editorconfig* doivent s’appliquer à tous les projets de la solution ou à un seul. Vous pouvez également sélectionner dans votre projet ou votre solution un dossier auquel ajouter le fichier *.editorconfig*.

1. Dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**ou appuyez sur **CTRL** + **MAJ** + **A**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

1. Dans la zone de recherche, recherchez **editorconfig**.

   Deux modèles d'élément de **Fichier editorconfig** s’affichent dans les résultats de recherche.

   ![Modèles d’élément de fichier EditorConfig dans Visual Studio](media/editorconfig-item-templates.png)

1. Sélectionnez le modèle **Fichier editorconfig (par défaut)** pour ajouter un fichier EditorConfig prérempli avec deux options essentielles d’EditorConfig pour le style de mise en retrait et la taille. Vous pouvez aussi sélectionner le modèle **Fichier editorconfig (.NET)** pour ajouter un fichier EditorConfig prérempli avec les conventions de [style de code mise en forme et dénomination .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options) par défaut.

   Un fichier *.editorconfig* s’affiche dans l’explorateur de solutions et s’ouvre dans l’éditeur.

   ![Fichier .editorconfig dans l’Explorateur de solutions et l’éditeur](media/editorconfig-dotnet.png)

1. Modifiez le fichier comme vous le souhaitez.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Autres façons d’ajouter un fichier EditorConfig

Il existe d’autres façons d’ajouter un fichier EditorConfig au projet :

- La [fonctionnalité d’inférence de code](/visualstudio/intellicode/code-style-inference) d’IntelliCode pour Visual Studio déduit vos styles de code à partir du code existant. Elle crée ensuite un fichier EditorConfig non vide avec vos préférences de style de code déjà définies.

- À compter de Visual Studio 2019, vous pouvez [générer un fichier EditorConfig selon vos paramètres de style de code](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) dans **Outils** > **Options**.

## <a name="file-hierarchy-and-precedence"></a>Priorité et hiérarchie des fichiers

Quand vous ajoutez un fichier *.editorconfig* à un dossier de votre hiérarchie de fichiers, ses paramètres s’appliquent à tous les fichiers concernés situés au même niveau et en dessous. Vous pouvez également remplacer les paramètres EditorConfig d’un projet particulier, d’un code base ou d’une partie de code base qui utilise des conventions différentes de celles des autres parties du code base. Ce remplacement peut s’avérer être utile quand vous incorporez du code provenant d’ailleurs et que vous ne voulez pas modifier ses conventions.

Pour remplacer entièrement ou partiellement des paramètres EditorConfig, ajoutez un fichier *.editorconfig* au niveau de la hiérarchie de fichiers à laquelle vous voulez appliquer ces paramètres de remplacement. Les paramètres du nouveau fichier EditorConfig s’appliquent aux fichiers situés au même niveau et dans tous ses sous-répertoires.

![Hiérarchie d’EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Si vous voulez remplacer une partie des paramètres seulement, il suffit de spécifier ces paramètres dans le fichier *.editorconfig*. Seules les propriétés que vous répertoriez explicitement dans le fichier de niveau inférieur sont alors remplacées. Les autres paramètres des fichiers *.editorconfig* de niveau supérieur continuent à s’appliquer. Pour être sûr qu’_aucun_ paramètre _de_ fichiers *.editorconfig* de niveau supérieur n’est appliqué à cette partie du codebase, ajoutez la propriété ```root=true``` au fichier *.editorconfig* de niveau inférieur :

```ini
# top-most EditorConfig file
root = true
```

Les fichiers EditorConfig sont lus de haut en bas. S’il existe plusieurs propriétés portant le même nom, la propriété la plus récemment trouvée portant ce nom est prioritaire.

## <a name="edit-editorconfig-files"></a>Modifier des fichiers EditorConfig

Visual Studio vous permet de modifier les fichiers *.editorconfig* en fournissant des listes de saisie semi-automatique IntelliSense.

![IntelliSense dans un fichier .editorconfig](media/editorconfig-intellisense-no-extension.png)

Une fois que vous avez modifié un fichier EditorConfig, vous devez recharger vos fichiers de code pour que les nouveaux paramètres prennent effet.

Si vous modifiez de nombreux fichiers *.editorconfig*, l’[extension du service de langage EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) peut vous être utile. Les fonctionnalités de cette extension incluent notamment une mise en surbrillance de la syntaxe, ainsi que des fonctionnalités IntelliSense, de validation et de mise en forme de code améliorées.

![IntelliSense avec l’extension du service de langage EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Exemple

L’exemple suivant montre la mise en retrait d’un extrait de code C# avant et après l’ajout d’un fichier *.editorconfig* au projet. Le paramètre **Tabulations** dans la boîte de dialogue **Options** de l’éditeur de texte Visual Studio est défini pour ajouter des espaces quand vous appuyez sur la touche **Tab**.

![Paramètre de tabulation de l’Éditeur de texte](../ide/media/vside_editorconfig_tabsetting.png)

Comme prévu, si l’on appuie sur la touche **Tab** sur la ligne suivante, quatre espaces blancs supplémentaires sont ajoutés, ce qui a pour effet de mettre la ligne en retrait.

![Code avant l’utilisation d’EditorConfig](../ide/media/vside_editorconfig_before.png)

Ajoutez un nouveau fichier appelé *.editorconfig* au projet, avec le contenu suivant. Le paramètre `[*.cs]` signifie que cette modification s’applique uniquement aux fichiers de code C# dans le projet.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Désormais, lorsque vous appuyez sur la touche **Tab** , vous recevez des caractères de tabulation à la place des espaces.

![Un appui sur la touche Tab ajoute un caractère de tabulation](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Résoudre les problèmes liés aux paramètres d’EditorConfig

Si un fichier EditorConfig se trouve n’importe où dans la structure de répertoire au niveau ou au-dessus de votre projet, Visual Studio applique les paramètres de l’éditeur définis dans ce fichier à votre éditeur. Dans ce cas, vous pouvez voir le message suivant s’afficher dans la barre d’état :

   **« Les préférences utilisateur de ce type de fichier sont remplacées par les conventions de codage de ce projet. »**

Cela signifie que si des paramètres de l’éditeur dans **Outils**  >  **options**  >  **éditeur de texte** (tels que la taille et le style du retrait, la taille des tabulations ou les conventions de codage) sont spécifiés dans un fichier EditorConfig au niveau ou au-dessus du projet dans la structure de répertoires, les conventions du fichier EditorConfig remplacent les paramètres dans **options**. Vous pouvez contrôler ce comportement en activant ou en désactivant l’option **Suivre les conventions de codage du projet** dans **Outils** > **Options** > **Éditeur de texte**. Si vous décochez cette option, vous désactivez la prise en charge d’EditorConfig pour Visual Studio.

![Outils Options, Suivre les conventions de codage du projet](media/coding_conventions_option.png)

Vous pouvez rechercher les fichiers *.editorconfig* dans les répertoires parents en ouvrant une invite de commandes et en exécutant la commande suivante à partir de la racine du disque contenant votre projet :

```Shell
dir .editorconfig /s
```

Vous pouvez contrôler la portée de vos conventions EditorConfig en définissant la propriété ```root=true``` dans le fichier *.editorconfig* à la racine de votre référentiel ou dans le répertoire où se trouve votre projet. Visual Studio recherche un fichier nommé *.editorconfig* dans le répertoire du fichier ouvert et dans chaque répertoire parent. La recherche se termine quand il atteint le chemin racine, ou si un fichier *.editorconfig* avec ```root=true``` est trouvé.

## <a name="see-also"></a>Voir aussi

- [Conventions de style du code .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Prise en charge d’EditorConfig pour un service de langage](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Fonctionnalités de l’éditeur de code](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio pour Mac)](/visualstudio/mac/editorconfig)
