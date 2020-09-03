---
title: '&lt;&gt;élément appAddin (développement Office dans Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1bf9ea990d12bd24adee3f6a24a39fa43c74fb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531636"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;&gt;élément appAddin (développement Office dans Visual Studio)
  L’élément **appAddin** de l' `vstov4` espace de noms stocke des informations spécifiques à la personnalisation pour les compléments VSTO.

## <a name="syntax"></a>Syntaxe

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément **appAddin** est obligatoire et se trouve dans l' `vstov4` espace de noms. Il n’existe qu’un seul élément **appAddin** défini dans un manifeste d’application.

 L’élément **appAddin** a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|**application**|Obligatoire. Identifie l’application Microsoft Office. La valeur peut être l’une des suivantes : Excel, InfoPath, Outlook, PowerPoint, Project, Visio ou Word.|
|**loadBehavior**|facultatif. Par défaut, le **LoadBehavior** est activé en définissant cette valeur sur. Pour le débogage, vous pouvez désactiver le complément VSTO en définissant la valeur sur deux. Pour plus d’informations, consultez le tableau intitulé valeurs LoadBehavior dans les [entrées de Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|
|**keyName**|Obligatoire. Cette valeur est le nom de la clé de Registre que l’application utilise pour charger le complément VSTO. Pour plus d’informations, consultez [entrées du Registre pour les compléments VSTO](../vsto/registry-entries-for-vsto-add-ins.md).|

 L’élément **appAddin** contient les éléments enfants suivants.

### <a name="friendlyname"></a>friendlyName
 facultatif. L’élément **FriendlyName** est expliqué dans [&#60;&#62; élément FriendlyName &#40;développement Office dans Visual Studio&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>description
 facultatif. L’élément **Description** est expliqué dans [&#60;description&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 Obligatoire uniquement pour les compléments VSTO Outlook qui comprennent des zones de formulaire. L’élément **FormRegions** est expliqué dans [&#60;&#62; élément &#40;développement Office dans Visual Studio&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="description"></a>Description
 L’exemple de code suivant illustre des éléments **appAddin** dans une solution Outlook déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
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
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)