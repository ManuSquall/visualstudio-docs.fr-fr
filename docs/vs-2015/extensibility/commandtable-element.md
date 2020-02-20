---
title: Élément CommandTable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477049"
---
# <a name="commandtable-element"></a>Élément CommandTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable est l’élément racine du fichier. vsct. Il s’agit du fichier qui définit la disposition et le type réels des commandes qu’un VSPackage fournit à l’IDE. Les commandes peuvent inclure des éléments de menu, des menus, des barres d’outils et des zones de liste modifiable. Pour plus d'informations, consultez [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
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
  
| Attribut |                                                                                                                   Description                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Obligatoire. Espaces de noms XML :<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| langage  | facultatif. L’attribut Language peut être utilisé pour spécifier la langue par défaut de toutes les chaînes de \<> éléments dans la table de commandes.  Si la langue n’est pas spécifiée, la langue du processus en cours sera utilisée :<br /><br /> Language = "en-US" |
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Extern](../extensibility/extern-element.md)|facultatif. Contient des directives de préprocesseur pour le compilateur.|  
|[Élément Include](../extensibility/include-element.md)|facultatif. Contient les chemins d’accès à tous les fichiers à inclure dans la compilation.|  
|[Élément Define](../extensibility/define-element.md)|facultatif. Définit un symbole en fonction de son nom et de sa valeur.|  
|[Commands, élément](../extensibility/commands-element.md)|facultatif. Élément parent qui définit toutes les commandes pour le VSPackage qui contient tous les autres éléments.|  
|[Élément CommandPlacements](../extensibility/commandplacements-element.md)|facultatif. Définit l’emplacement où les commandes doivent être placées dans la barre de commandes.|  
|[Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|facultatif. Détermine la visibilité statique des commandes et des barres d’outils.|  
|[Élément KeyBindings](../extensibility/keybindings-element.md)|facultatif. Spécifie les combinaisons de touches de raccourci, le cas échéant, pour les commandes.|  
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|facultatif. Permet à un VSPackage d’implémenter éventuellement sa propre version de fonctionnalité prise en charge à l’origine par d’autres VSPackages.|  
|[Élément Symbols](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|facultatif. Contient des données de symboles (GUID, ID, etc.) pour le compilateur.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|None||  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
