---
title: VsCT Compiler Command-Line Flags (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703969"
---
# <a name="vsct-compiler-command-line-flags"></a>Indicateurs de la ligne de commande du compilateur VSCT
Le compilateur Visual Studio Command Table (VSCT) fournit des commutateurs de ligne de commande pour assurer une compilation réussie des fichiers .vsct.

## <a name="command-line-parameters"></a>Paramètres de la ligne de commande
 Pour voir l’aide [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSCT de base à partir d’une fenêtre **de commande,** naviguez vers le *chemin d’installation Visual Studio SDK*'VisualStudioIntegration’Tools’Bin ' dossier et tapez:

```
vsct /?
```

 Cette demande renvoie :

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
> Les caractères - (dash) et / (slash vers l’avant) sont tous deux acceptés notation pour indiquer les paramètres de la ligne de commande.

 Les drapeaux acceptables et ce qu’ils signifient sont les suivants.

|Commutateur|Description|
|------------|-----------------|
|-d|Spécifier d’autres symboles définis.|
|-I|Indiquer les autres inclure les chemins qui doivent être utilisés lors de la résolution des références de fichiers.|
|-l|Spécifier le nom de la <xref:System.Globalization.CultureInfo> culture, par exemple "en-US".|
|-E|Émettre des objets CMD dans l’espace de nom spécifié pour les éléments de commande, suivi de [C&#124;H&#124;N]:*nom de fichier*où C ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' L’espace de nom est requis pour le C.|
|-v|Sortie Verbose.|

 Le commutateur -L demande au compilateur de sélectionner un groupe de chaînes pour produire <xref:System.Globalization.CultureInfo> le fichier binaire .cto qui correspond au nom de la culture donnée. Le nom de culture spécifié doit correspondre à l’attribut linguistique d’un ou plusieurs [éléments de cordes](../../extensibility/strings-element.md) dans le fichier .vsct. Si un élément strings n’a pas d’attribut de langue, il est hérité de [l’élément De commande](../../extensibility/commandtable-element.md)contenant .

 Un fichier .vsct peut avoir plusieurs éléments de cordes, et chacun peut avoir un attribut de langue différent. La mondialisation est réalisée en exécutant le compilateur VSCT plusieurs fois et en changeant le commutateur -L pour chaque nom de culture.

 Si le nom de culture donné par le commutateur -L ne correspond pas à l’attribut linguistique de n’importe quel élément de cordes, le compilateur va essayer de faire correspondre la langue, et non la région. Par exemple, si "en-US" ne peut pas être trouvé, le compilateur va essayer "en" à la place. À défaut, il va essayer la culture actuelle du système d’exploitation. À défaut, il compilera le premier élément Strings qu’il trouve.

 Le commutateur -E peut être utilisé pour émettre un fichier d’en-tête de type C qui contient les symboles qui sont utilisés par la table de commande, ou pour émettre un fichier Cmd qui contient des objets pour les symboles de commande.

 Les commutateurs -D et-I ont la syntaxe des drapeaux préprocesseurs Cl.exe C qui ont le même nom. -D définitions qui ont le format X-Y sont utilisés \<pour l’expansion `Condition` de XML-basé Défini> tests dans les attributs. -J’inclus des chemins \<sont utilisés \<pour résoudre Inclure>, Extern> et \<Bitmap> références de fichiers. Pour plus d’informations, voir la [référence VSCT XML Schema](../../extensibility/vsct-xml-schema-reference.md).

 Le compilateur VSCT peut également décomposer un fichier binaire précédemment construit. Pour ce faire, fournir un \<fichier binaire pour le> infile.   Si le fichier binaire a été produit par le compilateur VSCT, il aura ses \<symboles déjà intégrés et produira la sortie avec les noms symboliques dans une section symboles> de la sortie. Si le binaire a été produit par le compilateur de la CCT, la sortie contiendra les GUID et les DME réels. Si le fichier 'ctsym qui est produit par les versions actuelles de Ctc.exe est dans le même dossier que le fichier d’entrée binaire, les symboles seront chargés à partir de ce fichier et utilisés pour la sortie.

## <a name="see-also"></a>Voir aussi
- [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
