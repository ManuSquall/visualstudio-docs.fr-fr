---
title: '&lt;formRegions &gt; , élément (développement Office dans Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a1a718c6a247528788d91e9c1f30ad636acb7ab9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970333"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions &gt; , élément (développement Office dans Visual Studio)
  L' `formRegions` élément de l' `vstov4` espace de noms contient les zones de formulaire Microsoft Office Outlook associées à un complément VSTO.

## <a name="syntax"></a>Syntaxe

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `formRegions` de l’espace de noms `vstov4` contient tous les éléments `formRegion` pour un complément VSTO Outlook. Il est uniquement obligatoire pour les compléments VSTO Outlook qui incluent des zones de formulaire.

 Un seul élément `formRegions` peut être défini dans un manifeste de l’application.

 L’élément `formRegions` ne comporte pas d’attributs.

 L’élément `formRegions` possède l’élément suivant.

### <a name="formregion"></a>formRegion
 Obligatoire pour les compléments VSTO Outlook qui comprennent des zones de formulaire. L' `formRegion` élément est défini dans [&#60;élément formRegion&#62; &#40;développement Office dans Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="description"></a>Description
 L’exemple de code suivant illustre un élément `formRegions` dans un manifeste de l’application pour une solution Office au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)