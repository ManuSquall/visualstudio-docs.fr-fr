---
title: '&lt;assembly&gt; , élément (Application ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b629243920021adc3833f43f268f05638029dc7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640400"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;assembly&gt; , élément (Application ClickOnce)
Élément de niveau supérieur pour le manifeste d’application.

## <a name="syntax"></a>Syntaxe

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 Le `assembly` élément est l’élément racine et est obligatoire. Le premier élément de relation contenant-contenu doit être un `assemblyIdentity` élément. Les éléments du manifeste doivent être dans un des espaces de noms suivants :

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Les éléments enfants de l’assembly doivent également être dans ces espaces de noms, par héritage ou par balisage.

 L’élément `assembly` comporte l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`manifestVersion`|Obligatoire. Le `manifestVersion` attribut doit être défini sur `1.0`.|

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre un `assembly` élément dans un manifeste d’application pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Cet exemple de code fait partie d’un exemple plus complet fourni dans [manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md).

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>Voir aussi
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assembly > élément](../deployment/assembly-element-clickonce-deployment.md)
