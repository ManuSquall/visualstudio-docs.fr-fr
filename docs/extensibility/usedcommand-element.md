---
title: "&#201;l&#233;ment de UsedCommand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UsedCommands, élément (schéma XML de VSCT)"
  - "Éléments du schéma XML de VSCT, UsedCommands"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# &#201;l&#233;ment de UsedCommand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Permet à un VSPackage pour accéder à une commande qui est définie dans un autre fichier .vsct. Par exemple, si votre VSPackage utilise la norme **copie** commande, qui est définie par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, vous pouvez ajouter la commande à un menu ou une barre d'outils sans les ré\-implémenter.  
  
## Syntaxe  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|GUID|Obligatoire. Le GUID de la paire GUID qui identifie la commande.|  
|ID|Obligatoire. ID de la paire GUID qui identifie la commande.|  
|Condition|Facultatif. Consultez [Attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|None||  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément de UsedCommands](../extensibility/usedcommands-element.md)|Regroupe les éléments UsedCommand et autres regroupements UsedCommands.|  
  
## Notes  
 En ajoutant une commande à la `<UsedCommands>` élément, un VSPackage informe le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] environnement que le VSPackage requiert la commande. Vous devez ajouter un `<UsedCommand>` élément pour n'importe quelle commande votre package requiert qui n'est pas inclus dans toutes les versions et configurations de Visual Studio. Par exemple, si votre package appelle une commande qui est spécifique à Visual C\+\+, la commande ne sera pas disponible pour les utilisateurs de Visual Web Developer, sauf si vous incluez un `<UsedCommand>` élément pour la commande.  
  
## Exemple  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## Voir aussi  
 [Élément de UsedCommands](../extensibility/usedcommands-element.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)