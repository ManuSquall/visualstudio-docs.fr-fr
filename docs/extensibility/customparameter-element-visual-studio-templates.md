---
title: CustomParameter, élément (modèles Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 154586701386f5f8f56c128920e12ca3147deb6b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100567"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter, élément (modèles Visual Studio)
Contient un nom de paramètre personnalisé et une valeur à utiliser lorsqu’un projet ou un élément est créé à partir du modèle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Name`|Obligatoire. Nom du paramètre. Le format des paramètres est $*nom*$.|  
|`Value`|Obligatoire. La valeur de remplacement pour le paramètre.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Regroupe les paramètres personnalisés qui doivent être passés à l’Assistant modèle lorsque les remplacements de paramètres.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un modèle contient `CustomParameter` éléments, chaque instance de la `Name` attribut est remplacé par le `Value` attribut dans les fichiers de projet ou un élément créés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser plusieurs paramètres personnalisés dans un modèle. Création d’un projet ou un élément à partir d’un modèle avec les paramètres personnalisés suivants, toutes les instances de `$color1$` et `$color2$` dans le modèle de fichiers seront remplacés par `Red` et `Blue`, respectivement.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CustomParameters, élément (modèles Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)