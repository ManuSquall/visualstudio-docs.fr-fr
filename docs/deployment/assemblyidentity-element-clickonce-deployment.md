---
title: '&lt;assemblyIdentity&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56525cc0c0c754a7fa3a1f4c2c5b6cf2e941e9b0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608342"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity&gt; , élément (déploiement ClickOnce)
Identifie l’assembly principal de le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.

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
 Le `assemblyIdentity` élément est requis. Il ne contient aucun élément enfant et a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`name`|Obligatoire. Identifie le nom explicite du déploiement à titre d’information.<br /><br /> Si `name` contient des caractères spéciaux, tels que des guillemets simples ou doubles, l’application peut échouer à activer.|
|`version`|Obligatoire. Spécifie le numéro de version de l’assembly, au format suivant : `major.minor.build.revision`.<br /><br /> Cette valeur doit être incrémentée dans un manifeste mis à jour pour déclencher une mise à jour de l’application.|
|`publicKeyToken`|Obligatoire. Spécifie une chaîne hexadécimale de 16 caractères qui représente les 8 derniers octets de la valeur de hachage SHA-1 de la clé publique sous laquelle le manifeste de déploiement est signé. La clé publique qui est utilisée pour signer doit être de 2 048 bits ou supérieur.<br /><br /> Bien que la signature d’un assembly est recommandé mais facultatif, cet attribut est requis. Si un assembly n’est pas signé, vous devez copier une valeur à partir d’un assembly auto-signé ou utiliser une valeur « factice » de tous les zéros non significatifs.|
|`processorArchitecture`|Obligatoire. Spécifie le processeur. Les valeurs valides sont `msil` pour tous les processeurs, `x86` pour Windows 32 bits, `IA64` pour Windows 64 bits, et `Itanium` pour les processeurs Itanium d’Intel 64 bits.|
|`type`|Obligatoire. Pour assurer la compatibilité avec la technologie d’installation de côte à côte de Windows. La seule valeur autorisée est `win32`.|

## <a name="remarks"></a>Remarques

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre un `assemblyIdentity` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Cet exemple de code fait partie d’un exemple plus complet fourni pour le [manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) rubrique.

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
- [\<assemblyIdentity>, élément](../deployment/assemblyidentity-element-clickonce-application.md)