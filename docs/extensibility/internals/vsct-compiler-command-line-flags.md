---
title: Indicateurs de ligne de commande du compilateur VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71634a007019dd39e843ccc63af1c3188f778ea9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722032"
---
# <a name="vsct-compiler-command-line-flags"></a>Indicateurs de la ligne de commande du compilateur VSCT
Le compilateur de table de commandes Visual Studio (VSCT) fournit des commutateurs de ligne de commande pour garantir la réussite de la compilation des fichiers. vsct.

## <a name="command-line-parameters"></a>Paramètres de ligne de commande
 Pour afficher l’aide de base VSCT à partir d’une fenêtre de **commande** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], accédez au dossier *chemin d’installation du kit de développement logiciel Visual Studio*\VisualStudioIntegration\Tools\Bin\, puis tapez :

```
vsct /?
```

 Cela retourne :

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

|Basculer|Description|
|------------|-----------------|
|-D|Spécifiez des symboles définis supplémentaires.|
|-I|Indiquer les chemins d’accès include supplémentaires qui doivent être utilisés lors de la résolution des références de fichier.|
|-L|Spécifiez le nom de la culture <xref:System.Globalization.CultureInfo>, par exemple « en-US ».|
|-E|C# Émettez des objets dans l’espace de noms spécifié pour les éléments de&#124;commande&#124;, suivis de [c H C#N] : C++ *NomFichier*où C =, H = en-tête, N = espace de noms. L’espace de noms est C#requis pour.|
|-v|Sortie détaillée.|

 Le commutateur-L demande au compilateur de sélectionner un groupe de chaînes pour produire le fichier. directeur technique binaire qui correspond au nom de culture <xref:System.Globalization.CultureInfo> donné. Le nom de culture spécifié doit correspondre à l’attribut de langage d’un ou de plusieurs [éléments Strings](../../extensibility/strings-element.md) dans le fichier. vsct. Si un élément Strings n’a pas d’attribut Language, il est hérité de l' [élément CommandTable](../../extensibility/commandtable-element.md)conteneur.

 Un fichier. vsct peut avoir plusieurs éléments Strings et chacun peut avoir un attribut Language différent. La globalisation est obtenue en exécutant plusieurs fois le compilateur VSCT et en modifiant le commutateur-L pour chaque nom de culture.

 Si le nom de culture donné par le commutateur-L ne correspond pas à l’attribut de langage d’un élément de chaîne, le compilateur essaiera de correspondre à la langue, et non à la région. Par exemple, si « en-US » est introuvable, le compilateur essaiera « en » à la place. En échec, elle essaiera la culture actuelle du système d’exploitation. À l’échec, elle compilera le premier élément Strings qu’elle trouve.

 Le commutateur-E peut être utilisé pour émettre un fichier d’en-tête de style C qui contient les symboles utilisés par la table de commandes, ou pour C# émettre un fichier qui contient des objets pour les symboles de commande.

 Les commutateurs-D et-I ont la syntaxe des indicateurs de préprocesseur CL. exe C portant le même nom. Les définitions-D qui ont le format X = Y sont utilisées pour l’expansion des tests de > \<définis par XML dans des attributs de `Condition`. -J’inclut des chemins d’accès permettant de résoudre les \<inclure des références de >, \<extern > et \<bitmap > de fichiers. Pour plus d’informations, consultez la [référence de schéma XML vsct](../../extensibility/vsct-xml-schema-reference.md).

 Le compilateur VSCT peut également décompiler un fichier binaire précédemment généré. Pour ce faire, fournissez un fichier binaire pour le \<> INFILE.   Si le fichier binaire a été généré par le compilateur VSCT, ses symboles sont déjà incorporés et génèrent une sortie avec les noms symboliques dans une \<> section de la sortie. Si le fichier binaire a été généré par le compilateur CTC, la sortie contient les GUID et ID réels. Si le fichier *. ctsym généré par les versions actuelles de CTC. exe se trouve dans le même dossier que le fichier d’entrée binaire, les symboles sont chargés à partir de ce fichier et utilisés pour la sortie.

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)