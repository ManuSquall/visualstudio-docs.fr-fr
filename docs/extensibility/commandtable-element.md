---
title: "Élément de CommandTable | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a6abf25d0e3eff335c8a6fe62affc19d8037afa
ms.lasthandoff: 02/22/2017

---
# <a name="commandtable-element"></a>Élément de CommandTable
CommandTable est l’élément racine du fichier .vsct. Il s’agit du fichier qui définit la disposition réelle et le type des commandes un VSPackage fournit à l’IDE. Commandes peuvent inclure des éléments de menu, des menus, des barres d’outils et des zones de liste déroulante. Pour plus d’informations, consultez [Table de commandes Visual Studio (. Les fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|xmlns|Obligatoire. Espaces de noms XML :<br /><br /> xmlns = « http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable »<br /><br /> xmlns : xs = « http://www.w3.org/2001/XMLSchema »|  
|language|Facultatif. L’attribut de langage peut être utilisée pour spécifier la langue par défaut de tous les \<chaînes > des éléments de la table commandes.  Si la langue n’est pas spécifiée, la langue du processus actuel est utilisée :<br /><br /> Language = "en-us »|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de extern](../extensibility/extern-element.md)|Facultatif. Contient des directives de préprocesseur du compilateur.|  
|[Élément Include](../extensibility/include-element.md)|Facultatif. Contient les chemins d’accès aux fichiers à inclure dans la compilation.|  
|[Définir l’élément](../extensibility/define-element.md)|Facultatif. Définit un symbole donné son nom et sa valeur.|  
|[Élément Commands](../extensibility/commands-element.md)|Facultatif. L’élément parent définissant toutes les commandes pour le VSPackage qui contient tous les autres éléments.|  
|[Élément de CommandPlacements](../extensibility/commandplacements-element.md)|Facultatif. Définit où sur la barre de commandes les commandes doivent être placés.|  
|[Élément de VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facultatif. Détermine la visibilité des commandes et des barres d’outils statique.|  
|[Élément de thèmes](../extensibility/keybindings-element.md)|Facultatif. Spécifie les combinaisons de touches de raccourci pour les commandes.|  
|[Élément de UsedCommands](../extensibility/usedcommands-element.md)|Facultatif. Permet à un VSPackage éventuellement implémenter sa propre version de la fonctionnalité à l’origine pris en charge par les autres packages VS.|  
|[Élément de symboles](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Facultatif. Contient les données de symbole--GUID, ID et ainsi de suite--pour le compilateur.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun||  
  
## <a name="see-also"></a>Voir aussi  
 [Table de commandes de Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
