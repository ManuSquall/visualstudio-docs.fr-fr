---
title: '&lt;&gt;élément CompatibleFrameworks (déploiement ClickOnce) | Microsoft Docs'
description: L’élément compatibleFrameworks identifie les versions du .NET Framework sur lesquelles cette application peut être installée et exécutée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5da9819cd3df667be5e8fa04372684f82762c037
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383064"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;élément CompatibleFrameworks (déploiement ClickOnce)
Identifie les versions du .NET Framework pour lesquelles cette application peut s'installer et s'exécuter.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) ne prend pas en charge l' `compatibleFrameworks` élément lors de l’enregistrement d’un manifeste d’application qui a déjà été signé avec un certificat à l’aide de [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). À la place, vous devez utiliser [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Syntaxe

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L' `compatibleFrameworks` élément est requis pour les manifestes de déploiement qui ciblent le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime fourni par .NET Framework 4 ou version ultérieure. L' `compatibleFrameworks` élément contient un ou plusieurs `framework` éléments qui spécifient le .NET Framework versions sur lesquelles cette application peut s’exécuter. Le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Runtime exécute l’application sur la première disponible `framework` dans cette liste.

 Le tableau suivant répertorie l’attribut `compatibleFrameworks` pris en charge par l’élément.

|Attribut|Description|
|---------------|-----------------|
|`S` `upportUrl`|facultatif. Spécifie une URL dans laquelle la version de .NET Framework compatible préférée peut être téléchargée.|

## <a name="framework"></a>framework
 Obligatoire. Le tableau suivant répertorie les attributs `framework` pris en charge par l’élément.

|Attribut|Description|
|---------------|-----------------|
|`targetVersion`|Obligatoire. Spécifie le numéro de version du .NET Framework cible.|
|`profile`|Obligatoire. Spécifie le profil du .NET Framework cible.|
|`supportedRuntime`|Obligatoire. Spécifie le numéro de version du runtime associé au .NET Framework cible.|

## <a name="remarks"></a>Remarques

## <a name="example"></a>Exemple
 L’exemple de code suivant montre un `compatibleFrameworks` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Ce déploiement peut s’exécuter sur le [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Il peut également s’exécuter sur le .NET Framework 4, car il s’agit d’un sur-ensemble de [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Voir aussi
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)