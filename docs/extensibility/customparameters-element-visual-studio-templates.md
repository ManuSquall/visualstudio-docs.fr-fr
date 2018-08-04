---
title: CustomParameters, élément (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464c4720dc4693ef2fb968a23a538e74d03d1a26
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498647"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters, élément (modèles Visual Studio)
Regroupe les paramètres personnalisés qui doivent être passés à l’Assistant modèle lorsque les remplacements de paramètres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Élément facultatif.<br /><br /> Contient un nom de paramètre personnalisé et une valeur à utiliser lorsqu’un projet ou un élément est créé à partir du modèle. Un élément `CustomParameter` peut ne contenir aucun élément `CustomParameters` ou en contenir plusieurs.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Spécifie le contenu du modèle.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser plusieurs paramètres personnalisés dans un modèle. Création d’un projet ou un élément à partir d’un modèle avec les paramètres personnalisés suivants, toutes les instances de `$color1$` et `$color2$` dans le modèle de fichiers seront remplacées par `Red` et `Blue`, respectivement.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CustomParameter, élément (modèles Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)