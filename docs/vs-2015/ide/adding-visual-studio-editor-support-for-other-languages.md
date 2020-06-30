---
title: Ajout de la prise en charge de l’éditeur pour d’autres langages | Microsoft Docs
ms.date: 11/15/2016
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9dbd245edd81907197e23c0d193a01cc07424b4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548107"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Ajout de la prise en charge de l’éditeur Visual Studio dans d’autres langages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Découvrez comment l’éditeur Visual Studio prend en charge la lecture et la navigation parmi différents langages de programmation, et comment ajouter la prise en charge de l’éditeur Visual Studio dans d’autres langages.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Prise en charge de la coloration syntaxique, de la saisie semi-automatique des instructions et de Naviguer vers
 Des fonctionnalités de l’éditeur Visual Studio, telles que la coloration syntaxique, la saisie semi-automatique des instructions et Naviguer vers, peuvent vous aider à lire, créer et modifier votre code. La capture d’écran suivante montre un exemple de modification de script Perl dans Visual Studio. La syntaxe est colorée automatiquement. Par exemple, les remarques dans le code sont colorées en vert, le code est en noir, les chemins sont en rouge et les instructions sont en bleu. L’éditeur Visual Studio applique automatiquement la coloration syntaxique à tout langage pris en charge. De plus, quand vous commencez à entrer un mot clé de langage ou un objet connu, la saisie semi-automatique affiche une liste d’instructions et d’objets possibles. La saisie semi-automatique des instructions simplifie et accélère la création du code.

 ![Coloration syntaxique dans un script Perl](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Actuellement, Visual Studio fournit la prise en charge de la coloration syntaxique et de la saisie semi-automatique des instructions de base pour les langages suivants à l’aide de [grammaires TextMate](https://manual.macromates.com/en/language_grammars). Si votre langage préféré ne figure pas dans le tableau, ne vous inquiétez pas, vous pouvez l’ajouter.

- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Go
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- LESS
- Python
- SQL
- VBNet
- CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Marque
- Ruby
- TypeScript
- YAML

 Outre la coloration syntaxique et la saisie semi-automatique des instructions de base, Visual Studio propose également une fonctionnalité appelée [Naviguer vers](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Elle vous permet de rechercher rapidement des fichiers de code, des chemins de fichier et des symboles de code. Visual Studio fournit la prise en charge de Naviguer vers pour les langages suivants.

- Go

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C# 

  Tous ces types de fichier offrent les fonctionnalités décrites précédemment même si la prise en charge d’un langage donné n’a pas encore été installée. L’installation de la prise en charge spécialisée pour certains langages peut fournir une prise en charge de langage supplémentaire, comme IntelliSense ou d’autres fonctionnalités de langage avancées comme les ampoules.

## <a name="adding-support-for-non-supported-languages"></a>Ajout de la prise en charge des langages non pris en charge
 Visual Studio 2015 Update 1 et versions ultérieures fournissent la prise en charge des langages dans l’éditeur à l’aide des [grammaires TextMate](https://manual.macromates.com/en/language_grammars). Si votre langage de programmation préféré n’est pas pris en charge dans l’éditeur Visual Studio, recherchez tout d’abord sur le web. Un lot TextMate existe peut-être déjà pour ce langage. Si vous n’en trouvez aucun, vous pouvez ajouter la prise en charge vous-même dans Visual Studio 2015 Update 1 ou ultérieur en créant un modèle de lot TextMate pour des extraits de code et des grammaires de langage.

 Ajoutez les nouvelles grammaires TextMate pour Visual Studio dans le dossier suivant :

 %userprofile%\\.vs\Extensions

 Sous ce chemin de base, ajoutez le ou les dossiers suivants s’ils s’appliquent à votre situation :

|Nom du dossier|Description|
|-----------------|-----------------|
|\\*\<language name>*|Dossier du langage. Remplacez *\<language name>* par le nom de la langue. Par exemple, **\Matlab**.|
|\Syntaxes|Dossier de la grammaire. Contient les fichiers .json de grammaire du langage, tels que **Matlab.json**.|
|\Snippets|Dossier des extraits de code. Contient les extraits de code du langage.|

 Dans Windows,% USERPROFILE% correspond au chemin d’accès : c:\Users \\ *\<user name>* . Si le dossier d’extensions n’existe pas sur votre système, vous devez le créer. Si le dossier existe déjà, il est masqué.

 Pour plus d’informations sur la création de grammaires TextMate, consultez [TextMate – Introduction to Language Grammars: How to add source code syntax highlighting embedded in HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate – Présentation des grammaires de langage : comment ajouter la coloration syntaxique du code source incorporée en HTML) et [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Remarques sur la création d’une grammaire de langage et d’un thème personnalisé pour un lot Textmate).

## <a name="see-also"></a>Voir aussi
 [Visual Studio 2013 accédez aux améliorations](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [procédure pas à pas : Création d’un extrait de Code](../ide/walkthrough-creating-a-code-snippet.md) [procédure pas à pas : Affichage de la saisie semi-automatique des instructions ](../extensibility/walkthrough-displaying-statement-completion.md)
