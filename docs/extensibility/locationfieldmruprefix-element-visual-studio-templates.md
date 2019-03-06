---
title: LocationFieldMRUPrefix, élément (modèles Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationFieldMRUPrefix
helpviewer_keywords:
- <LocationFieldMRUPrefix> element [Visual Studio Templates]
- LocationFieldMRUPrefix element [Visual Studio Templates]
ms.assetid: 03443691-9eb5-46f4-9169-cc2552a04bcb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8c4c3fa4e64b302c6d1c9d0e393528d46fe072f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680398"
---
# <a name="locationfieldmruprefix-element-visual-studio-templates"></a>LocationFieldMRUPrefix, élément (modèles Visual Studio)
Spécifie les chemins des derniers fichiers utilisés (MRU) dans le **nouveau projet** et **ajouter un nouvel élément** boîte de dialogue.

## <a name="syntax"></a>Syntaxe

```xml
<LocationFieldMRUPrefix> ... </LocationFieldMRUPrefix>
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

## <a name="remarks"></a>Notes
 Cet élément doit être utilisé uniquement pour les modèles de produit via le [!INCLUDE[vsipprvsip](../extensibility/includes/vsipprvsip_md.md)].

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les schémas de modèles Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)