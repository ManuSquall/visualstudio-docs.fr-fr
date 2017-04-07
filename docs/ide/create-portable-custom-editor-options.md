---
title: "Créer des paramètres d’éditeur personnalisés et portables avec EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: f377ada139d9c0e8b01b640cf603cf349dc1c3c3
ms.lasthandoff: 03/27/2017

---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Créer des paramètres d’éditeur personnalisés et portables avec EditorConfig
Les paramètres de l’éditeur de texte dans Visual Studio s’appliquent à tous les projets d’un type donné. Ainsi, par exemple, si vous modifiez un paramètre d’éditeur de texte C#, ce paramètre s’applique à *tous* les projets C# dans Visual Studio. Toutefois, dans certains cas, vous devrez peut-être utiliser des conventions qui diffèrent de vos préférences d’éditeur personnelles. Les fichiers [EditorConfig](http://editorconfig.org/) vous permettent de le faire en fournissant des options d’éditeur de texte courantes sur la base de chaque projet. Les paramètres EditorConfig, qui sont contenus dans un fichier .editorconfig ajouté à votre base de code, remplacent les paramètres globaux de l’éditeur de texte Visual Studio. Cela signifie que vous pouvez personnaliser chaque base de code pour utiliser les paramètres de l’éditeur de texte que vous préférez. Aucun plug-in n’est nécessaire pour utiliser cette fonctionnalité dans Visual Studio.

## <a name="coding-consistency"></a>Cohérence du codage
Les paramètres dans les fichiers EditorConfig vous permettent de conserver des paramètres et des styles de codage cohérents pour un langage, tels que le style de mise en retrait, la largeur de tabulation, les caractères de fin de ligne, l’encodage, ceci dans une base de code indépendamment de l’éditeur ou de l’IDE que vous utilisez. Par exemple, quand vous codez en C#, si votre base de code a une convention selon laquelle les retraits sont toujours des caractères à cinq espaces, les documents utilisent l’encodage UTF-8, et chaque ligne se termine toujours par un retour chariot/saut de ligne, vous pouvez configurer un fichier .editorconfig pour ce faire.

Les conventions de codage que vous utilisez dans vos projets personnels peuvent différer de celles utilisées dans les projets de votre équipe. Par exemple, vous préférerez peut-être que lors du codage, un appui sur la touche Tab ajoute un caractère de tabulation. De son côté, votre équipe préférera peut-être que la mise en retrait ajoute quatre caractères d’espace au lieu d’un caractère de tabulation. Les fichiers EditorConfig résolvent ce problème en vous permettant d’avoir une configuration pour chaque scénario.

Les paramètres étant contenus dans un fichier dans la base de code, ils se déplacent avec cette base de code. Tant que vous ouvrez le fichier de code dans un éditeur compatible avec EditorConfig, les paramètres de l’éditeur de texte sont implémentés. Pour plus d’informations sur les fichiers EditorConfig, consultez le site web [EditorConfig.org](http://editorconfig.org/). Si vous modifiez un grand nombre de fichiers .editorconfig, vous trouverez peut-être utile l’extension [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig).

## <a name="override-editorconfig-settings"></a>Substituer les paramètres d’EditorConfig
Quand vous ajoutez un fichier .editorconfig dans un dossier de votre hiérarchie de fichiers, ses paramètres s’appliquent à tous les fichiers applicables à ce niveau et en dessous. Pour substituer les paramètres d’EditorConfig pour une base de code ou un projet particulier et utiliser des valeurs de substitution ou autres que celles du fichier .editorconfig de niveau supérieur, ajoutez simplement un fichier .editorconfig au niveau que vous souhaitez modifier.

![Hiérarchie d’EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Les nouveaux paramètres du fichier .editorconfig s’appliqueront au niveau auquel il se trouve et à tous ses sous-fichiers.

## <a name="supported-settings"></a>Paramètres pris en charge
L’éditeur de Visual Studio prend en charge les valeurs suivantes de l’ensemble principal d’options d’EditorConfig.
- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- racine
- [conventions de style de code](../ide/editorconfig-code-style-settings-reference.md)

Les paramètres d’EditorConfig sont pris en charge dans tous les langages pris en charge par Visual Studio, à l’exception de XML.

## <a name="example"></a>Exemple
Voici un exemple qui montre l’état de mise en retrait d’un extrait de code C# avant et après l’ajout d’un fichier .editorconfig au projet. Le paramètre **Tabulations** dans la boîte de dialogue **Options** de l’éditeur de texte Visual Studio est configuré pour générer des espaces quand vous appuyez sur la touche Tab dans votre code.

![Paramètre de tabulation de l’Éditeur de texte](../ide/media/vside_editorconfig_tabsetting.png)

Comme prévu, un appui sur la touche Tab sur la ligne suivante met en retrait la ligne en ajoutant quatre espaces supplémentaires.

![Code avant l’utilisation d’EditorConfig](../ide/media/vside_editorconfig_before.png)

Nous allons ajouter ce qui suit à un nouveau fichier appelé .editorconfig dans le projet. (Le paramètre `[*.cs]` signifie que cette modification s’applique uniquement aux fichiers .cs de ce projet.)

![Fichier .editorconfig ajouté au projet](../ide/media/vside_editorconfig_addconfig.png)

Maintenant, quand vous appuyez sur la touche Tab, vous obtenez des caractères de tabulation plutôt que des espaces.

![Un appui sur Tab ajoute le caractère de tabulation](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  L’ajout d’un fichier .editorconfig à votre projet ou votre base de code ne convertira pas les styles existants en nouveaux styles. Il s’appliquera uniquement aux lignes qui viennent d’être ajoutées. Si vous supprimez un fichier .editorconfig de votre projet ou de votre base de code, vous devez recharger les fichiers de code pour que les paramètres de l’éditeur reviennent aux paramètres globaux. Toute erreur dans les fichiers .editorconfig est signalée dans la fenêtre Erreurs dans Visual Studio.

## <a name="support-editorconfig-for-your-language-service"></a>Prendre en charge EditorConfig pour votre service de langage

Dans la plupart des cas, quand vous implémentez un service de langage Visual Studio, aucun travail supplémentaire n’est nécessaire pour la prise en charge des propriétés universelles EditorConfig. L’éditeur principal découvre et lit automatiquement le fichier .editorconfig quand les utilisateurs ouvrent des fichiers, et définit les options d’affichage et de mémoire tampon de texte appropriées. Toutefois, certains services de langage choisissent d’utiliser une option d’affichage de texte contextuel appropriée à la place de paramètres globaux pour des éléments tels que des tabulations et des espaces quand un utilisateur modifie ou met en forme un texte. Dans ce cas, le service de langage doit être mis à jour pour prendre en charge les fichiers EditorConfig.

Le tableau suivant répertorie les modifications nécessaires pour mettre à jour un service de langage afin qu’il prenne en charge les fichiers EditorConfig.

| Option globale spécifique au langage dépréciée | Option contextuelle de remplacement |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs ou Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) ou !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize ou Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) ou textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize ou Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) ou textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

# <a name="see-also"></a>Voir aussi
[Créer des options d’éditeur personnalisées et portables avec EditorConfig](create-portable-custom-editor-options.md)
