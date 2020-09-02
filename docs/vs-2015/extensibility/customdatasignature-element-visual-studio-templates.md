---
title: Élément CustomDataSignature (modèles Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 784704bea43a87f1aebdc42941906179dca815ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580415"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>Élément CustomDataSignature (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie la signature du texte pour localiser les données personnalisées.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<CustomDataSignature>  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Classe le modèle et définit son mode d’affichage dans la boîte de dialogue **nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Le texte est une chaîne qui possède la signature de texte requise pour localiser les données personnalisées.  
  
## <a name="remarks"></a>Notes  
 `CustomDataSignature` est un élément facultatif.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)
