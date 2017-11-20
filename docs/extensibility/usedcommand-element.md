---
title: "Élément de UsedCommand | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b3974c9103a385badc56fda759ee95ef3a40a93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="usedcommand-element"></a>Élément de UsedCommand
Permet à un VSPackage pour accéder à une commande qui est définie dans un autre fichier .vsct. Par exemple, si votre VSPackage utilise la norme **copie** commande, qui est définie par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interpréteur de commandes, vous pouvez ajouter la commande à un menu ou une barre d’outils sans nouvelle mise en œuvre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. Le GUID de la paire GUID qui identifie la commande.|  
|ID|Obligatoire. ID de la paire GUID qui identifie la commande.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucune||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|Regroupe les éléments UsedCommand et autres regroupements UsedCommands.|  
  
## <a name="remarks"></a>Remarques  
 En ajoutant une commande pour le `<UsedCommands>` informe de l’élément, un VSPackage le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement que le VSPackage requiert la commande. Vous devez ajouter un `<UsedCommand>` , élément pour n’importe quelle commande requiert de votre package qui n’est pas inclus dans toutes les versions et les configurations de Visual Studio. Par exemple, si votre package appelle une commande qui est spécifique à Visual C++, la commande ne sera pas disponible pour les utilisateurs de Visual Web Developer, sauf si vous incluez un `<UsedCommand>` élément pour la commande.  
  
## <a name="example"></a>Exemple  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de UsedCommands](../extensibility/usedcommands-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)