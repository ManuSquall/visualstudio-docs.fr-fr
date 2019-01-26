---
title: Élément extern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bac2f7e5611e8e87dd3ad6c268c0fd2ea6292c14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924189"
---
# <a name="extern-element"></a>Élément extern
L’élément Extern fait référence à n’importe quel en-tête externe (*.h*) fichiers à fusionner avec le *.vsct* fichier au moment de la compilation. Les fichiers devant être fusionnées doivent être sur le chemin d’accès Include donnée au compilateur VSCT ou référencé par une [élément Include](../extensibility/include-element.md). Les fichiers peuvent être des autres *.vsct* fichiers ou des fichiers d’en-tête C++.  
  
 Définitions de fichiers d’en-tête doivent être sous la forme « #define [symbole] [valeur] » la valeur peut être un autre symbole s’il est défini précédemment. Les définitions sont utilisables dans des instructions conditionnelles d’éléments de la commande. N’importe quel symbole ne sont pas utilisé est ignorée.  
  
 Élément CommandTable  
Élément Extern  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|href|Obligatoire. Le chemin d’accès du fichier d’en-tête :<br /><br /> href="stdidcmd.h"|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Facultatif. La langue par défaut de tous les [ \<chaînes >](../extensibility/strings-element.md) éléments dans la table de commande :<br /><br /> language="en-us"|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Aucun.|Aucun.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément CommandTable](../extensibility/commandtable-element.md)|Définit tous les éléments qui représentent des commandes, autrement dit, les éléments de menu, les menus, les barres d’outils et les zones de liste déroulante, qu’un VSPackage fournit à l’IDE.|  
  
## <a name="example"></a>Exemple  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio fichiers command table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)