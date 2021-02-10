---
title: '&lt;formRegion &gt; , élément (développement Office dans Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 469b041ac879753e5fe4be0f9bd739be1030a942
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970387"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion &gt; , élément (développement Office dans Visual Studio)
  L' `formRegion` élément de l' `vstov4` espace de noms identifie une zone de formulaire Microsoft Office Outlook associée à un complément VSTO.

## <a name="syntax"></a>Syntaxe

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `formRegion` de l’espace de noms `vstov4` identifie une zone de formulaire associée à un complément VSTO Outlook. Il est uniquement obligatoire pour les compléments VSTO Outlook qui incluent des zones de formulaire.

 Plusieurs éléments `formRegion` peuvent être définis à l’intérieur d’un élément `formRegions` pour un même complément VSTO.

 L’élément `formRegion` comporte l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`name`|Obligatoire. Identifie le nom de la zone de formulaire.|

 L’élément `formRegion` comporte les éléments enfants suivants.

### <a name="messageclass"></a>messageClass
 L’élément `messageClass` identifie le formulaire Outlook associé à la zone de formulaire.

 L’élément `messageClass` comporte l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`name`|Obligatoire. Identifie le formulaire associé à la zone de formulaire.|

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre un élément `formRegion` dans le manifeste d’application d’un complément VSTO Outlook déployé à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cette zone de formulaire est associée à trois classes de message. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Voir aussi

- [Créer des zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)