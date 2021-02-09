---
title: '&lt;assemblyIdentity &gt; , élément (déploiement ClickOnce) | Microsoft Docs'
description: L’élément assemblyIdentity est requis dans le déploiement ClickOnce. Il ne contient pas d’éléments enfants et possède des attributs décrits dans cet article.
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bc689c80d033c6b92178f020c0d3273f6ec86ca7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911348"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity &gt; , élément (déploiement ClickOnce)
Identifie l’assembly principal de l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

## <a name="syntax"></a>Syntaxe

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `assemblyIdentity` est obligatoire. Il ne contient pas d’éléments enfants et a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`name`|Obligatoire. Identifie le nom explicite du déploiement à des fins d’information.<br /><br /> Si `name` contient des caractères spéciaux, tels que des guillemets simples ou doubles, l’activation de l’application peut échouer.|
|`version`|Obligatoire. Spécifie le numéro de version de l’assembly au format suivant : `major.minor.build.revision` .<br /><br /> Cette valeur doit être incrémentée dans un manifeste mis à jour pour déclencher une mise à jour d’application.|
|`publicKeyToken`|Obligatoire. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la valeur de hachage SHA-1 de la clé publique sous laquelle le manifeste de déploiement est signé. La clé publique utilisée pour signer doit être supérieure ou égale à 2048 bits.<br /><br /> Bien que la signature d’un assembly soit recommandée mais facultative, cet attribut est obligatoire. Si un assembly n’est pas signé, vous devez copier une valeur d’un assembly auto-signé ou utiliser une valeur « factice » de zéros.|
|`processorArchitecture`|Obligatoire. Spécifie le processeur. Les valeurs valides sont `msil` pour tous les processeurs, `x86` pour Windows 32 bits, `IA64` pour Windows 64 bits et `Itanium` pour les processeurs Itanium Intel 64 bits.|
|`type`|Obligatoire. Pour la compatibilité avec la technologie d’installation côte à côte de Windows. La seule valeur autorisée est `win32` .|

## <a name="remarks"></a>Notes

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre un `assemblyIdentity` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Cet exemple de code fait partie d’un exemple plus complet fourni pour la rubrique du [manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Voir aussi
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> appartient](../deployment/assemblyidentity-element-clickonce-application.md)