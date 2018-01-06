---
title: "Extern élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ff198f5c4b574bf3a27ae1ee8fb6ffdd482c7f71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extern-element"></a>Élément de extern
L’élément Extern fait référence à des fichiers externes en-tête (.h) à fusionner avec le fichier .vsct au moment de la compilation. Les fichiers devant être fusionnées doivent être sur le chemin d’accès Include donnée au compilateur VSCT ou référencé par une [l’élément Include](../extensibility/include-element.md). Les fichiers peuvent être des autres fichiers .vsct ou les fichiers d’en-tête C++.  
  
 Définitions des fichiers d’en-tête doivent être sous la forme « #define [symbole] [valeur] » la valeur peut être un autre symbole si elle est définie précédemment. Les définitions peuvent servir dans les instructions conditionnelles des éléments de la commande. N’importe quel symbole ne sont pas utilisé est ignorée.  
  
 Élément de CommandTable  
Élément de extern  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|href|Obligatoire. Le chemin d’accès au fichier d’en-tête :<br /><br /> href="stdidcmd.h »|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Facultatif. La langue par défaut de tous les [ \<chaînes >](../extensibility/strings-element.md) éléments dans la table de commande :<br /><br /> Language = « en-us »|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.|Aucun.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes, autrement dit, les éléments de menu, menus, barres d’outils et zones de liste déroulante, par un VSPackage à l’IDE.|  
  
## <a name="example"></a>Exemple  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tableau de commandes de Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)