---
title: Élément UsedCommand | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78ab46c4524bb25563d407514aa0590e75feffaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505649"
---
# <a name="usedcommand-element"></a>Élément UsedCommand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [UsedCommand élément](https://docs.microsoft.com/visualstudio/extensibility/usedcommand-element).  
  
Permet à un VSPackage pour accéder à une commande qui est définie dans un autre fichier .vsct. Par exemple, si votre VSPackage utilise le standard **copie** commande, qui est défini par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shell, vous pouvez ajouter la commande à un menu ou une barre d’outils sans les ré-implémenter.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. Le GUID de la paire ID GUID qui identifie la commande.|  
|ID|Obligatoire. L’ID de la paire ID GUID qui identifie la commande.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément UsedCommands](../extensibility/usedcommands-element.md)|Regroupe les éléments UsedCommand et autres regroupements UsedCommands.|  
  
## <a name="remarks"></a>Notes  
 En ajoutant une commande pour le `<UsedCommands>` élément, un VSPackage informe le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement que le VSPackage nécessite la commande. Vous devez ajouter un `<UsedCommand>` élément pour n’importe quelle commande votre package requiert que peuvent ne pas figurer dans toutes les versions et les configurations de Visual Studio. Par exemple, si votre package appelle une commande qui est spécifique à Visual C++, la commande ne sera pas disponible pour les utilisateurs de Visual Web Developer, sauf si vous incluez un `<UsedCommand>` élément pour la commande.  
  
## <a name="example"></a>Exemple  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément UsedCommands](../extensibility/usedcommands-element.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

