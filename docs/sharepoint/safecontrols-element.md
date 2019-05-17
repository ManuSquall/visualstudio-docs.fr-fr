---
title: SafeControls, élément | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce943416bba84c46ce7b709c3d2bdb6ddb3e4447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009556"
---
# <a name="safecontrols-element"></a>SafeControls (élément)
  Une collection de contrôles ASPX et les composants WebPart qui sont désignés comme sécurisé pour un utilisateur d’accéder sur n’importe quelle page ASPX du site SharePoint.

## <a name="syntax"></a>Syntaxe

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs
 Aucun.

### <a name="child-elements"></a>Éléments enfants

|Élément|Description|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Élément facultatif.<br /><br /> Représente un contrôle ASPX ou un composant WebPart qui est désigné comme sécurisé pour un utilisateur d’accéder sur n’importe quelle page ASPX du site SharePoint.|

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Représente un élément de projet SharePoint. Cet élément de l’élément racine requis de la *.spdata* fichier.|

## <a name="remarks"></a>Notes
 Pour plus d’informations sur les contrôles sécurisés, consultez [fournissent des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informations sur les éléments

|||
|-|-|
|**Espace de noms**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom de schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema.xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence de schéma élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
