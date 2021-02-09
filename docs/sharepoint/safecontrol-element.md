---
title: Élément SafeControl | Microsoft Docs
description: Obtenir des informations sur l’élément SafeControl, qui représente un contrôle ASPX ou un composant WebPart marqué comme sécurisé pour qu’un utilisateur accède à la page ASPX d’un site SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f08046666ff00d4a0e5489bc78c0c70967774f08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889471"
---
# <a name="safecontrol-element"></a>SafeControl (élément)
  Représente un contrôle ASPX ou un composant WebPart qui est désigné comme sécurisé pour tout utilisateur qui peut accéder à n’importe quelle page ASPX sur le site SharePoint.

## <a name="syntax"></a>Syntaxe

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>Attributs et éléments
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|**Assembly**|Attribut **XS : String** facultatif.<br /><br /> Nom de l’assembly dans lequel le contrôle ASPX ou le composant WebPart est défini. Par défaut, cet attribut utilise le paramètre Replaceable **$SharePoint. Project. AssemblyFullName $** pour le nom de l’assembly. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).|
|**IsSafe**|Attribut **XS : Boolean** facultatif.<br /><br /> Spécifie si le contrôle ASPX ou le composant WebPart est sécurisé pour l’accès des utilisateurs non approuvés.|
|**IsSafeAgainstScript**|Attribut **XS : Boolean** facultatif.<br /><br /> Spécifie si les utilisateurs non fiables peuvent afficher ou modifier les propriétés du composant WebPart ou du contrôle ASPX.|
|**Nom**|Attribut **XS : String** facultatif.<br /><br /> Nom de cette entrée de contrôle sécurisé dans la collection.|
|**Espace de noms**|Attribut **XS : String** facultatif.<br /><br /> Espace de noms du contrôle ASPX ou du composant WebPart.|
|**TypeName**|Attribut **XS : String** facultatif.<br /><br /> Nom de type du contrôle ASPX ou du composant WebPart.|

### <a name="child-elements"></a>Éléments enfants
 Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|Représente une collection de contrôles ASPX et WebParts désignés comme sécurisés pour n’importe quel utilisateur à accéder à n’importe quelle page ASPX sur le site SharePoint.|

## <a name="remarks"></a>Remarques
 Pour plus d’informations sur les contrôles sécurisés, consultez [fournir des informations sur l’empaquetage et le déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informations sur les éléments

|Propriété|Valeur|
|-|-|
|**Espace de noms**|http : \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nom du schéma**|Schéma d’élément de projet SharePoint|
|**Fichier de validation**|ProjectItemModelSchema. xsd|
|**Peut être vide**|Non|

## <a name="see-also"></a>Voir aussi
- [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fournir des informations d’empaquetage et de déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
