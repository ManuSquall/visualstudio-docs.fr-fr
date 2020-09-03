---
title: '&lt;&gt;élément de personnalisation (développement Office dans Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1239c6749f25bf4bce7a1f5cc89a2a8430c98a4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544870"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;&gt;élément de personnalisation (développement Office dans Visual Studio)
  L’élément `customization` de l’espace de noms `vstov4` décrit une solution Office spécifique. Les éléments enfants sont différents pour les personnalisations au niveau du document et les compléments VSTO.

## <a name="syntax-for-document-level-customizations"></a>Syntaxe pour les personnalisations au niveau du document

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>Syntaxe pour les compléments VSTO

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `customization` contient des informations propres à la personnalisation. Cet élément doit être dans l’espace de noms suivant : `vstov4=urn:schemas-microsoft-com:vsto.v4`. Il existe un seul élément `customization` pour chaque solution Office. Par exemple, si vous déployez trois solutions Office dans un déploiement à projets multiples, il existe trois éléments `customization` dans le manifeste de l’application.

 Les éléments enfants de l’assembly doivent également figurer dans cet espace de noms.

 L’élément `customization` comporte l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`id`|Obligatoire pour un déploiement à projets multiples. L’élément `id` identifie de façon unique une solution Office.|

### <a name="document-level-customizations"></a>Personnalisations au niveau du document
 L’élément `customization` possède l’élément enfant suivant.

#### <a name="document"></a>document
 L' `document` élément de l' `vstov4` espace de noms est défini dans [&#60;élément document&#62; &#40;le développement Office dans Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>Compléments VSTO
 L’élément `customization` possède l’élément enfant suivant.

#### <a name="appaddin"></a>appAddin
 L' `appAddin` élément de l' `vstov4` espace de noms est défini dans [&#60;élément appAddin&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Exemple de personnalisation au niveau du document

### <a name="description"></a>Description
 L’exemple de code suivant illustre l’élément `customization` d’une personnalisation au niveau du document. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Exemple de complément VSTO

### <a name="description"></a>Description
 L’exemple de code suivant illustre l' `customization` élément d’un complément VSTO. Il s’agit d’un complément VSTO Outlook qui inclut des zones de formulaire. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:customization>
  <vstov4:appAddIn
    application="Outlook"
    loadBehavior="3"
    keyName="ContosoOutlookAddIn">
    <vstov4:friendlyName>
      ContosoOutlookAddIn
    </vstov4:friendlyName>
    <vstov4:description>
      ContosoOutlookAddIn - Outlook VSTO Add-in
      created with Visual Studio Tools for Office
    </vstov4:description>
    <vstov4:formRegions>
      <vstov4:formRegion
          name="OutlookAddIn1.FormRegion1">
        <vstov4:messageClass name="IPM.Note" />
        <vstov4:messageClass name="IPM.Contact" />
        <vstov4:messageClass name="IPM.Appointment" />
      </vstov4:formRegion>
    </vstov4:formRegions>
  </vstov4:appAddIn>
</vstov4:customization>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)