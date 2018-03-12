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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6fe68f25748df171ec6695554903b37854e7d8c6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="commandtable-element"></a>Élément de CommandTable
CommandTable est l’élément racine du fichier .vsct. Il s’agit du fichier qui définit la disposition et le type des commandes par un VSPackage à l’IDE. Commandes peuvent inclure des éléments de menu, des menus, des barres d’outils et des zones de liste déroulante. Pour plus d'informations, consultez [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
|xmlns|Obligatoire. Espaces de noms XML :<br /><br /> xmlns = « http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable »<br /><br /> prend = « http://www.w3.org/2001/XMLSchema »|  
|language|Facultatif. L’attribut de langue peut être utilisé pour spécifier la langue par défaut de tous les \<chaînes > éléments dans la table de commande.  Si la langue n’est pas spécifiée, la langue du processus actif sera utilisée :<br /><br /> Language = « en-us »|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Extern](../extensibility/extern-element.md)|Facultatif. Contient des directives de préprocesseur du compilateur.|  
|[Élément Include](../extensibility/include-element.md)|Facultatif. Contient les chemins d’accès à tous les fichiers à inclure dans la compilation.|  
|[Élément Define](../extensibility/define-element.md)|Facultatif. Définit un symbole donné son nom et sa valeur.|  
|[Élément Commands](../extensibility/commands-element.md)|Facultatif. L’élément parent définissant toutes les commandes pour le VSPackage qui contient tous les autres éléments.|  
|[Élément CommandPlacements](../extensibility/commandplacements-element.md)|Facultatif. Définit l’emplacement sur la barre de commandes les commandes doit être placé.|  
|[Élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facultatif. Détermine la visibilité statique des commandes et des barres d’outils.|  
|[Élément KeyBindings](../extensibility/keybindings-element.md)|Facultatif. Spécifie les combinaisons de touches de raccourci, le cas échéant, pour les commandes.|  
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|Facultatif. Permet à un VSPackage éventuellement implémenter sa propre version de la fonctionnalité à l’origine de la prise en charge par les autres packages VS.|  
|[Élément Symbols](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Facultatif. Contient les données de symbole--GUID, ID et ainsi de suite--pour le compilateur.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.||  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)