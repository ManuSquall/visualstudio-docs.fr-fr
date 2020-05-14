---
title: Ajouter la prise en charge de l’éditeur pour d’autres langages
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 955a968c52c963c8c6f0204f7687de2bd8482260
ms.sourcegitcommit: c3b6af7367bef67a02c37404534229b935f713a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80892773"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Ajouter la prise en charge de l’éditeur Visual Studio pour d’autres langages

Découvrez comment l’éditeur Visual Studio prend en charge la lecture et la navigation parmi différents langages de programmation, et comment ajouter la prise en charge de l’éditeur Visual Studio dans d’autres langages.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Prise en charge de la coloration syntaxique, de la saisie semi-automatique des instructions et de Naviguer vers

Certaines fonctionnalités de l’éditeur Visual Studio, comme la coloration syntaxique, la saisie semi-automatique des instructions (aussi connue sous le nom d’IntelliSense) et _Naviguer vers_, peuvent vous aider à écrire, lire et modifier votre code. La capture d’écran suivante montre un exemple de modification de script Perl dans Visual Studio. La syntaxe est colorée automatiquement. Par exemple, les remarques dans le code sont colorées en vert, le code est en noir, les chemins sont en rouge et les instructions sont en bleu. L’éditeur Visual Studio applique automatiquement la coloration syntaxique à tout langage pris en charge. De plus, quand vous commencez à entrer un mot clé de langage ou un objet connu, la saisie semi-automatique affiche une liste d’instructions et d’objets possibles. La saisie semi-automatique des instructions simplifie et accélère l’écriture de code.

![Coloration syntaxique dans un script Perl](../ide/media/vside_perledit.png)

Actuellement, Visual Studio fournit la prise en charge de la coloration syntaxique et de la saisie semi-automatique des instructions de base pour les langages suivants à l’aide de [grammaires TextMate](https://manual.macromates.com/en/language_grammars). Si votre langage préféré ne figure pas dans le tableau, ne vous inquiétez pas, vous pouvez l’ajouter.

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Go|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|LESS|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Marque|Ruby|TypeScript|YAML|

Outre la coloration syntaxique et la saisie semi-automatique des instructions de base, Visual Studio propose également une fonctionnalité appelée [Naviguer vers](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Elle permet de rechercher rapidement des fichiers de code, des chemins de fichier et des symboles de code. Visual Studio fournit la prise en charge de Naviguer vers pour les langages suivants.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Go

- Java

- PHP

Tous ces types de fichiers offrent les fonctionnalités décrites précédemment même si la prise en charge d’un langage donné n’a pas encore été installée. L’installation de la prise en charge spécialisée pour certains langages peut fournir une prise en charge de langage supplémentaire, comme IntelliSense ou d’autres fonctionnalités de langage avancées comme les ampoules.

## <a name="add-support-for-non-supported-languages"></a>Ajouter la prise en charge des langages non pris en charge

Visual Studio assure la prise en charge des langages dans l’éditeur avec des [grammaires TextMate](https://manual.macromates.com/en/language_grammars). Si votre langage de programmation préféré n’est pas pris en charge dans l’éditeur Visual Studio, recherchez tout d’abord sur le web &mdash; il est possible qu’un bundle TextMate existe déjà pour ce langage. Si vous n’en trouvez pas, vous pouvez ajouter la prise en charge vous-même en créant un modèle de bundle TextMate pour les extraits de code et les grammaires du langage.

Ajoutez les nouvelles grammaires TextMate pour Visual Studio dans le dossier suivant :

*% d’utilisateursprofile%\\.vs’Extensions*

Sous ce chemin de base, ajoutez les dossiers suivants s’ils s’appliquent à votre situation :

|Nom du dossier|Description|
|-----------------|-----------------|
|\\*\<nom de langue>*|Dossier du langage. Remplacez le * \<nom de langue>* par le nom de la langue. Par exemple, *\Matlab*.|
|*\Syntaxes*|Dossier de la grammaire. Contient les fichiers *.json* grammaire pour la langue, tels que *Matlab.json*.|
|*Snippets*|Dossier des extraits de code. Contient les extraits de code du langage.|

Dans Windows, la résolution de *%userprofile%* donne le chemin suivant : *c:\Users\\\<nom_utilisateur>*. Si le dossier *Extensions* n’existe pas sur votre système, vous devrez le créer. Si le dossier existe déjà, il est masqué.

> [!TIP]
> S’il y a des fichiers ouverts dans l’éditeur, vous devrez les fermer et les rouvrir pour afficher la coloration syntaxique après avoir ajouté les grammaires TextMate.

Pour plus d’informations sur la création de grammaires TextMate, voir [TextMate – Présentation des grammaires de langage](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) et [Remarques sur la création d’une grammaire de langage et d’un thème personnalisé pour un bundle TextMate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Voir aussi

- [Ajouter une extension du protocole de serveur de langage](../extensibility/adding-an-lsp-extension.md)
- [Procédure pas à pas : Créer un extrait de code](../ide/walkthrough-creating-a-code-snippet.md)
- [Procédure pas à pas : afficher la saisie semi-automatique des instructions](../extensibility/walkthrough-displaying-statement-completion.md)
- [Exemple de code : Grammaire textmate](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Exemple de code : Support linguistique personnalisé](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)