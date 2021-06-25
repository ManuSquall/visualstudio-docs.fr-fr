---
title: Indicateurs de Command-Line du compilateur VSCT | Microsoft Docs
description: Le compilateur de table de commandes Visual Studio fournit des options de ligne de commande pour garantir la réussite de la compilation des fichiers. vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce83df56e1bcfad50fe71da31291b5c43b26c47a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898889"
---
# <a name="vsct-compiler-command-line-flags"></a>Indicateurs de la ligne de commande du compilateur VSCT
Le compilateur de table de commandes Visual Studio (VSCT) fournit des commutateurs de ligne de commande pour garantir la réussite de la compilation des fichiers. vsct.

## <a name="command-line-parameters"></a>Paramètres de ligne de commande
 Pour afficher l’aide de base VSCT à partir d’une fenêtre de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **commande** , accédez au dossier *chemin d’installation du kit de développement logiciel Visual Studio*\VisualStudioIntegration\Tools\Bin\, puis tapez :

```
vsct /?
```

 Elle retourne ce qui suit :

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Les caractères-(tiret) et/(barre oblique) sont acceptés en notation pour indiquer les paramètres de ligne de commande.

 Les indicateurs acceptables et leur signification sont les suivants.

|Commutateur|Description|
|------------|-----------------|
|-d|Spécifiez des symboles définis supplémentaires.|
|-I|Indiquer les chemins d’accès include supplémentaires qui doivent être utilisés lors de la résolution des références de fichier.|
|-l|Spécifiez le <xref:System.Globalization.CultureInfo> nom de la culture, par exemple « en-US ».|
|-E|Émet des objets C# dans l’espace de noms spécifié pour les éléments de commande, suivis de [C&#124;H&#124;N] :*filename* où C = C#, H = en-tête C++, N = espace de noms. L’espace de noms est requis pour C#.|
|-v|Sortie détaillée.|

 Le commutateur-L demande au compilateur de sélectionner un groupe de chaînes pour produire le fichier. directeur technique binaire qui correspond au nom de <xref:System.Globalization.CultureInfo> culture donné. Le nom de culture spécifié doit correspondre à l’attribut de langage d’un ou de plusieurs [éléments Strings](../../extensibility/strings-element.md) dans le fichier. vsct. Si un élément Strings n’a pas d’attribut Language, il est hérité de l' [élément CommandTable](../../extensibility/commandtable-element.md)conteneur.

 Un fichier. vsct peut avoir plusieurs éléments Strings et chacun peut avoir un attribut Language différent. La globalisation est obtenue en exécutant plusieurs fois le compilateur VSCT et en modifiant le commutateur-L pour chaque nom de culture.

 Si le nom de culture donné par le commutateur-L ne correspond pas à l’attribut de langage d’un élément de chaîne, le compilateur essaiera de correspondre à la langue, et non à la région. Par exemple, si « en-US » est introuvable, le compilateur essaiera « en » à la place. En échec, elle essaiera la culture actuelle du système d’exploitation. À l’échec, elle compilera le premier élément Strings qu’elle trouve.

 Le commutateur-E peut être utilisé pour émettre un fichier d’en-tête de style C qui contient les symboles utilisés par la table de commandes, ou pour émettre un fichier C# qui contient des objets pour les symboles de commande.

 Les commutateurs-D et-I ont la syntaxe des indicateurs de préprocesseur Cl.exe C portant le même nom. Les définitions-D qui ont le format X = Y sont utilisées pour l’expansion des tests basés sur XML \<Defined> dans des `Condition` attributs. -J’inclut des chemins d’accès permettant de résoudre les \<Include> \<Extern> références de \<Bitmap> fichier et. Pour plus d’informations, consultez la [référence de schéma XML vsct](../../extensibility/vsct-xml-schema-reference.md).

 Le compilateur VSCT peut également décompiler un fichier binaire précédemment généré. Pour ce faire, fournissez un fichier binaire pour le \<infile> .   Si le fichier binaire a été généré par le compilateur VSCT, ses symboles seront déjà incorporés et produiront une sortie avec les noms symboliques dans une \<Symbols> section de la sortie. Si le fichier binaire a été généré par le compilateur CTC, la sortie contient les GUID et ID réels. Si le fichier *. ctsym généré par les versions actuelles de Ctc.exe se trouve dans le même dossier que le fichier d’entrée binaire, les symboles sont chargés à partir de ce fichier et utilisés pour la sortie.

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
