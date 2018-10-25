---
title: Élément UsedCommands | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e707a8336fb5e324c667ae16eceac2c2e9f55654
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934767"
---
# <a name="usedcommands-element"></a>Élément UsedCommands
L’élément UsedCommands regroupe les éléments UsedCommand et autres regroupements UsedCommands.  
  
 L’élément UsedCommands est facultatif. Si vous n’appelez pas les commandes définies en dehors de votre package, il est inutile d’inclure cette section dans votre fichier .vsct.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément UsedCommand](../extensibility/usedcommand-element.md)|La commande est implémentée par un autre code.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes (par exemple, les éléments de menu, menus, barres d’outils et zones de liste déroulante) qui fournit un VSPackage à l’environnement de développement intégré (IDE).|  
  
## <a name="example"></a>Exemple  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément UsedCommand](../extensibility/usedcommand-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)