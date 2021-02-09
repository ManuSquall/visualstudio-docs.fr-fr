---
title: '&lt;assemblyIdentity &gt; , élément (application ClickOnce) | Microsoft Docs'
description: L’élément assemblyIdentity est requis dans l’application ClickOnce. Il ne contient pas d’éléments enfants et possède des attributs décrits dans cet article.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92b5c1d323634bbb242cdccb54890908d5668803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911393"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity &gt; , élément (application ClickOnce)
Identifie l’application déployée dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement.

## <a name="syntax"></a>Syntaxe

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `assemblyIdentity` est obligatoire. Il ne contient pas d’éléments enfants et a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`Name`|Obligatoire. Identifie le nom de l’application.<br /><br /> Si `Name` contient des caractères spéciaux, tels que des guillemets simples ou doubles, l’activation de l’application peut échouer.|
|`Version`|Obligatoire. Spécifie le numéro de version de l’application au format suivant : `major.minor.build.revision`|
|`publicKeyToken`|Facultatif. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la `SHA-1` valeur de hachage de la clé publique sous laquelle l’application ou l’assembly est signé. La clé publique utilisée pour signer le catalogue doit être supérieure ou égale à 2048 bits.<br /><br /> Bien que la signature d’un assembly soit recommandée mais facultative, cet attribut est obligatoire. Si un assembly n’est pas signé, vous devez copier une valeur d’un assembly auto-signé ou utiliser une valeur « factice » de zéros.|
|`processorArchitecture`|Obligatoire. Spécifie le processeur. Les valeurs valides sont `msil` pour tous les processeurs, `x86` pour Windows 32 bits, `IA64` pour Windows 64 bits et `Itanium` pour les processeurs Itanium Intel 64 bits.|
|`language`|Obligatoire. Identifie les codes de langue en deux parties (par exemple, `en-US` ) de l’assembly. Cet élément se trouve dans l' `asmv2` espace de noms. S’il n’est pas spécifié, la valeur par défaut est `neutral` .|

## <a name="examples"></a>Exemples

### <a name="description"></a>Description
 L’exemple de code suivant illustre un `assemblyIdentity` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application. Cet exemple de code fait partie d’un exemple plus complet fourni dans le manifeste de l' [application ClickOnce](../deployment/clickonce-application-manifest.md).

### <a name="code"></a>Code

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Voir aussi
- [Manifeste d’application ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> appartient](../deployment/assemblyidentity-element-clickonce-deployment.md)