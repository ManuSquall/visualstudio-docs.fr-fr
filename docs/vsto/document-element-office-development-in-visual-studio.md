---
title: '&lt;&gt;élément document (développement Office dans Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e92c17d71b1c0959cb1918ce6fbad0e2cd44d5ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949829"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;&gt;élément document (développement Office dans Visual Studio)
  L' `document` élément de l' `vstov4` espace de noms stocke des informations spécifiques à la personnalisation pour les personnalisations au niveau du document.

## <a name="syntax"></a>Syntaxe

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 Obligatoire uniquement pour les personnalisations au niveau du document. L’élément `document` se trouve dans l’espace de noms `vstov4` . L’élément `document` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`solutionId`|Obligatoire. GUID utilisé par le Visual Studio Tools pour que le runtime Office identifie de manière unique une solution au niveau du document. Cette valeur est stockée en tant que _AssemblyLocation propriété de document personnalisée. Pour plus d’informations, consultez [vue d’ensemble des propriétés de document personnalisé](../vsto/custom-document-properties-overview.md).|

 `document` n’a aucun élément enfant.

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="description"></a>Description
 L’exemple de code suivant illustre l' `document` élément dans une solution Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)