---
title: Indicateurs de ligne de commande du compilateur VSCT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e2e1045adb451c7f4dd06b888fca356d26b7ff3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139771"
---
# <a name="vsct-compiler-command-line-flags"></a>Indicateurs de ligne de commande du compilateur VSCT
Le compilateur de la Table de commande Visual Studio (VSTC) fournit des commutateurs de ligne de commande pour vous assurer de la compilation des fichiers .vsct réussit.  
  
## <a name="command-line-parameters"></a>Paramètres de ligne de commande  
 Pour afficher l’aide VSCT base d’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **commande** fenêtre, accédez à la *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ dossier et le type :  
  
```  
vsct /?  
```  
  
 Cet exemple renvoie :  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Les caractères - (tiret) et / (barre oblique) sont les deux notation acceptée pour indiquer les paramètres de ligne de commande.  
  
 Indicateurs acceptables et leur signification sont les suivantes.  
  
|Basculer|Description|  
|------------|-----------------|  
|-D|Spécifiez tous les symboles définis supplémentaires.|  
|-I|Indiquer que supplémentaires incluent des chemins d’accès qui doivent être utilisés lors de la résolution des références de fichier.|  
|-L|Spécifiez le <xref:System.Globalization.CultureInfo> nom de culture, par exemple, « en-US ».|  
|-E|Émettre des objets c# dans l’espace de noms pour les éléments de la commande, suivi par [C&#124;H&#124;N] :*nom de fichier*où C = c#, H = en-tête C++, N = espace de noms. L’espace de noms est requis pour c#.|  
|-v|Sortie des commentaires.|  
  
 Le commutateur -L indique au compilateur pour sélectionner un groupe de chaînes pour générer le fichier .cto binaire qui correspond à la donnée <xref:System.Globalization.CultureInfo> nom de la culture. Le nom de culture spécifié doit correspondre à l’attribut de langue d’un ou plusieurs [élément Strings](../../extensibility/strings-element.md) dans le fichier .vsct. Si un élément de chaînes n’a aucun attribut de langage, il est hérité de l’objet contenant [CommandTable élément](../../extensibility/commandtable-element.md).  
  
 Un fichier .vsct peut avoir plusieurs éléments de chaînes, et chacune peut avoir un attribut de langue différent. Globalisation est obtenue en exécutant le compilateur VSCT plusieurs fois et la modification du commutateur -L pour chaque nom de la culture.  
  
 Si le nom de culture donné par le commutateur -L ne correspond pas à l’attribut Language de n’importe quel élément de chaînes, le compilateur tente de correspondre à la langue et pas la région. Par exemple, si « en-US » est introuvable, le compilateur va tenter « fr » à la place. À défaut, il va tenter de la culture actuelle du système d’exploitation. À défaut, il peut être compilé le premier élément de chaînes qu’il trouve.  
  
 Le commutateur -E peut être utilisé pour émettre un fichier d’en-tête C-style qui contient les symboles qui sont utilisées par la table de commande ou d’émettre un fichier c# qui contient des objets pour les symboles de commande.  
  
 L’option-D et - commutateurs ont la syntaxe des indicateurs de préprocesseur Cl.exe C qui portent le même nom. D - définitions qui ont le format X = Y sont utilisées pour le développement basé sur XML \<Defined > teste dans `Condition` attributs. -Inclure des chemins d’accès sont utilisés pour résoudre \<Include >, \<Extern > et \<Bitmap > références de fichiers. Pour plus d’informations, consultez la [référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Le compilateur VSCT peut décompiler également un fichier binaire généré précédemment. Pour ce faire, fournissez un fichier binaire pour le \<fichier_entree >.   Si le fichier binaire a été généré par le compilateur VSCT, il aura ses symboles déjà incorporées et produira un résultat avec les noms symboliques dans un \<symboles > section de la sortie. Si le fichier binaire a été produit par le compilateur CTC, la sortie contient le GUID et l’ID réel. Si le fichier *.ctsym qui est généré par les versions actuelles de Ctc.exe est dans le même dossier que le fichier d’entrée binaire, les symboles sont chargées à partir de ce fichier et utilisés pour la sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Tableau de commandes de Visual Studio (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Référence du schéma XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)