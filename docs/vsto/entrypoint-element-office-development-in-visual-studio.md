---
title: '&lt;entryPoint &gt; , élément (développement Office dans Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17f57b90b7c6aa4c254b2b55ee838a3086193ef7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543596"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint &gt; , élément (développement Office dans Visual Studio)
  Chaque élément `entryPoint` de l’espace de noms `vstav3` identifie un assembly de personnalisation qui doit être exécuté lorsque cette application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] est installée.

## <a name="syntax"></a>Syntax

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `entryPoint` est obligatoire et se trouve dans l’espace de noms `vstav3` .

 Chaque élément `entryPoint` peut contenir un seul assembly de personnalisation. Plusieurs éléments `entryPoint` peuvent être définis dans un manifeste d’application.

 L’élément `entryPoint` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`class`|Obligatoire. Identifie un assembly de personnalisation à exécuter. La syntaxe de cet attribut est *NomEspaceNoms.NomClasse*.|

 `entryPoint` possède l’élément suivant.

### <a name="assemblyidentity"></a>assemblyIdentity
 Obligatoire. L’élément `assemblyIdentity` de l’espace de noms `vstav3` fait référence à un élément `assemblyIdentity` du manifeste d’application [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

 Le rôle de `assemblyIdentity` et de ses attributs est défini dans [&#60;élément assemblyIdentity&#62; &#40;&#41;d’application ClickOnce ](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document

### <a name="description"></a>Description
 L’exemple de code suivant illustre les éléments `entryPoint` d’un manifeste d’application pour une solution Office au niveau du document déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>Exemple de complément VSTO

### <a name="description"></a>Description
 L’exemple de code suivant illustre un élément `entryPoint` d’un manifeste d’application pour une solution Office au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [les manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Voir aussi

- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)