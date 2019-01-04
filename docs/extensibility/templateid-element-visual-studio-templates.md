---
title: TemplateID, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bbd9bddaeab9d073affb35a1b275f0eef7afe99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874068"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID, élément (modèles Visual Studio)
Spécifie un identificateur pour un modèle d’élément est classé dans un groupe de modèles d’élément par le [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) élément.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateID >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<TemplateID> ... </TemplateID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Élément requis.<br /><br /> Définit la catégorie du modèle et comment il s’affiche dans la boîte de dialogue **Nouveau projet** ou **Ajouter un nouvel élément** .|  
  
## <a name="text-value"></a>Valeur texte  
 Un `string` qui représente un identificateur pour un modèle d’élément est classé dans un groupe de modèles d’élément par le `TemplateGroupID` élément.  
  
## <a name="remarks"></a>Notes  
 `TemplateID` est un élément facultatif.  
  
 Si un fichier .vstemplate omet le `TemplateID` élément, puis le [nom](../extensibility/name-element-visual-studio-templates.md) élément est utilisé comme identificateur pour le modèle.  
  
 La valeur de la `TemplateID` élément est utilisé avec l’inscription de système de projet (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) pour filtrer les modèles qui apparaissent dans le **ajouter un nouvel élément** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)