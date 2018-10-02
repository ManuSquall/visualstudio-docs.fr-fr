---
title: Élément UsedCommands | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8a3f4719b6d35be56ba447279d3a85d2a3f5118
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503943"
---
# <a name="usedcommands-element"></a>Élément UsedCommands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [UsedCommands élément](https://docs.microsoft.com/visualstudio/extensibility/usedcommands-element).  
  
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

