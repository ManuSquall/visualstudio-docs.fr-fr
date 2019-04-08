---
title: Indicateurs de ligne de commande du compilateur VSCT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 935734d3ab21fd4ce69afaaf5fd4eef9ac417089
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952611"
---
# <a name="vsct-compiler-command-line-flags"></a>Indicateurs de la ligne de commande du compilateur VSCT
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le compilateur de la Table de commande Visual Studio (VSTC) fournit des commutateurs de ligne de commande pour vous assurer de compilation réussie de fichiers .vsct.  
  
## <a name="command-line-parameters"></a>Paramètres de ligne de commande  
 Pour afficher l’aide VSCT base à partir d’un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **commande** fenêtre, accédez à la *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ dossier et tapez :  
  
```  
vsct /?  
```  
  
 Cette commande renvoie :  
  
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
>  Les caractères - (tiret) et / (barre oblique) sont les deux notation acceptées pour ce qui indique les paramètres de ligne de commande.  
  
 Indicateurs acceptables et leur signification sont les suivantes.  
  
|Basculer|Description|  
|------------|-----------------|  
|-D|Spécifiez tous les symboles définis supplémentaires.|  
|-I|Indiquer que le supplémentaires incluent des chemins d’accès qui doivent être utilisés lors de la résolution des références de fichier.|  
|-L|Spécifiez le <xref:System.Globalization.CultureInfo> nom de culture, par exemple, « en-US ».|  
|-E|Émettre C# suivie d’objets dans l’espace de noms pour les éléments de la commande, [C&#124;H&#124;N] :*filename*où C = C#, H = en-tête C++, N = espace de noms. L’espace de noms est obligatoire pour C#.|  
|-v|Sortie détaillée.|  
  
 Le commutateur -L indique au compilateur pour sélectionner un groupe de chaînes pour générer le fichier .cto binaire qui correspond à la donnée <xref:System.Globalization.CultureInfo> nom de culture. Le nom de culture spécifié doit correspondre à l’attribut de langue d’un ou plusieurs [élément Strings](../../extensibility/strings-element.md) dans le fichier .vsct. Si un élément de chaînes n’a aucun attribut de langage, il est hérité à partir de la contenant [CommandTable élément](../../extensibility/commandtable-element.md).  
  
 Un fichier .vsct peut-être avoir plusieurs éléments de chaînes, et chacun peut avoir un autre attribut de langage. La globalisation est obtenue en exécutant le compilateur VSCT plusieurs fois et en modifiant le commutateur -L pour chaque nom de culture.  
  
 Si le nom de culture fourni par le commutateur -L ne correspond pas à l’attribut Language de n’importe quel élément de chaînes, le compilateur tente de correspondre à la langue et pas la région. Par exemple, si « en-US » est introuvable, le compilateur essaie « fr » à la place. En cas d’échec, il essaiera de la culture actuelle du système d’exploitation. En cas d’échec, il sera compilé le premier élément de chaînes qu’il trouve.  
  
 Le commutateur -E peut être utilisé pour émettre un fichier d’en-tête C-style qui contient les symboles qui sont utilisés par la table de commande ou d’émettre un fichier C# qui contient des objets pour les symboles de commande.  
  
 L’option-D et – je commutateurs ont la syntaxe des indicateurs de préprocesseur Cl.exe C qui portent le même nom. D : définitions qui ont le format X = Y sont utilisées pour l’expansion de basé sur XML \<défini par > tests dans `Condition` attributs. – Je les chemins d’accès include permettent de résoudre \<Include >, \<Extern > et \<Bitmap > références de fichiers. Pour plus d’informations, consultez le [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
 Le compilateur VSCT peut décompiler également un fichier binaire généré précédemment. Pour ce faire, fournissez un fichier binaire pour le \<infile >.   Si le fichier binaire a été produit par le compilateur VSCT, il aura ses symboles déjà incorporées et produira un résultat avec les noms symboliques dans un \<symboles > section de la sortie. Si le fichier binaire a été généré par le compilateur CTC, la sortie contient le GUID et l’ID réel. Si le fichier *.ctsym qui est généré par les versions actuelles de Ctc.exe est dans le même dossier que le fichier d’entrée binaire, les symboles sont chargées à partir de ce fichier et utilisés pour la sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio Command Table (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
