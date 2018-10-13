---
title: TemplateGroupID, élément (modèles Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a6c2852938e77f87143b3ddd15fce0a4a6e5bcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203916"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID, élément (modèles Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie le genre de projet dans lequel les modèles d'élément doivent s'afficher. Cet élément est important quand [ShowByDefault (modèles Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) est défini sur `false`. Lorsque [ShowByDefault (modèles Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) est défini sur `true`, puis un modèle d’élément est disponible dans tous les types de projet.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Une valeur texte est requise.  
  
 Le texte spécifie un identificateur pour une catégorie de modèles d'élément.  
  
## <a name="remarks"></a>Notes  
 `TemplateGroupID` est un élément.  
  
 La valeur de la `TemplateGroupID` élément est utilisé avec l’inscription de système de projet (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<numéro de version >* \Projects\\) Pour filtrer les modèles qui apparaissent dans le **ajouter un nouvel élément** boîte de dialogue.  
  
|Valeur Visual C++|Signification|  
|------------------------|-------------|  
|VC-Native|Utilisé pour les projets natifs. Correspond également à la valeur par défaut, s'il est impossible de déterminer un type de projet.|  
|VC-Managed|Utilisé pour les projets managés (/clr)|  
|VC-Windows|Utilisé pour tous les projets qui ciblent la plateforme Windows (natifs/managés/Store)|  
|WinRT-Native-UAP|Utilisé pour les projets de Store Windows 10|  
|CodeSharing-Native|Utilisé pour les projets d'éléments partagés|  
|WinRT-Native-6.3|Utilisé pour les projets de Store Windows 8.1|  
|WinRT-Native-Phone-6.3|Utilisé pour les projets Windows Phone 8.1|  
|WinRT-Native|Utilisé pour les projets de Store Windows 8.0|  
|VC-Android|Utilisé pour les projets Android|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)

