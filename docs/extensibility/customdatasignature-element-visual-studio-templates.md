---
title: Élément CustomDataSignature (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eddff64680dd41637f78f33c46fe78f32bbc3a85
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561315"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Élément CustomDataSignature (modèles Visual Studio)
Spécifie la signature de texte pour localiser les données personnalisées.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<CustomDataSignature >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CustomDataSignature>"string"</CustomDataSignature>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il est affiché dans un le **nouveau projet** ou **ajouter un nouvel élément** boîte de dialogue.|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Le texte est une chaîne qui a la signature de texte qui est nécessaire pour localiser les données personnalisées.  
  
## <a name="remarks"></a>Notes  
 `CustomDataSignature` est un élément facultatif.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma de modèle de Studio Visual](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)