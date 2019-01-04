---
title: '&lt;document&gt; élément (développement Office dans Visual Studio)'
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c1798815ee3216d6f3bb41eae70ae3e2cdc0121
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854750"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;document&gt; élément (développement Office dans Visual Studio)
  Le `document` élément de la `vstov4` espace de noms stocke les informations de personnalisation spécifiques pour les personnalisations au niveau du document.

## <a name="syntax"></a>Syntaxe

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 Obligatoire uniquement pour les personnalisations au niveau du document. L’élément `document` se trouve dans l’espace de noms `vstov4` . L’élément `document` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`solutionId`|Obligatoire. Le GUID utilisé par Visual Studio Tools pour Office runtime pour identifier de manière unique une solution au niveau du document. Cette valeur est stockée en tant que la propriété de document personnalisée _AssemblyLocation. Pour plus d’informations, consultez [vue d’ensemble des propriétés de document personnalisées](../vsto/custom-document-properties-overview.md).|

 `document` n’a aucun élément enfant.

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="description"></a>Description
 L’exemple de code suivant illustre la `document` élément dans une solution de Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifestes d’Application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)