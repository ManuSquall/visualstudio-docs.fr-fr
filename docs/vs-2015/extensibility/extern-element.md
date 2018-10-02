---
title: Élément extern | Microsoft Docs
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
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dce51835164424272874b42b6073131607c7272
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516879"
---
# <a name="extern-element"></a>Élément Extern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [élément Extern](https://docs.microsoft.com/visualstudio/extensibility/extern-element).  
  
L’élément Extern fait référence à tous les fichiers externes en-tête (.h) à fusionner avec le fichier .vsct à la compilation. Les fichiers devant être fusionnées doivent être sur le chemin d’accès Include donnée au compilateur VSCT ou référencé par une [élément Include](../extensibility/include-element.md). Les fichiers peuvent être des autres fichiers .vsct ou les fichiers d’en-tête C++.  
  
 Définitions de fichiers d’en-tête doivent être sous la forme « #define [symbole] [valeur] » la valeur peut être un autre symbole s’il est défini précédemment. Les définitions sont utilisables dans des instructions conditionnelles d’éléments de la commande. N’importe quel symbole ne sont pas utilisé est ignorée.  
  
 Élément CommandTable  
Élément Extern  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|href|Obligatoire. Le chemin d’accès du fichier d’en-tête :<br /><br /> href="stdidcmd.h »|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Facultatif. La langue par défaut de tous les [ \<chaînes >](../extensibility/strings-element.md) éléments dans la table de commande :<br /><br /> Language = « en-us »|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.|Aucun.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes, autrement dit, les éléments de menu, les menus, les barres d’outils et les zones de liste déroulante, qu’un VSPackage fournit à l’IDE.|  
  
## <a name="example"></a>Exemple  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio Command Table (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)

