---
title: '&lt;&gt;élément CompatibleFrameworks (déploiement ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675414"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;élément CompatibleFrameworks (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifie les versions du .NET Framework pour lesquelles cette application peut s'installer et s'exécuter.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) ne prend pas en charge l' `compatibleFrameworks` élément lors de l’enregistrement d’un manifeste d’application qui a déjà été signé avec un certificat à l’aide de [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). À la place, vous devez utiliser [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 L' `compatibleFrameworks` élément est requis pour les manifestes de déploiement qui ciblent le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Runtime fourni par [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ou version ultérieure. L' `compatibleFrameworks` élément contient un ou plusieurs `framework` éléments qui spécifient le .NET Framework versions sur lesquelles cette application peut s’exécuter. Le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Runtime exécute l’application sur la première disponible `framework` dans cette liste.  
  
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
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre un `compatibleFrameworks` élément dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste de déploiement. Ce déploiement peut s’exécuter sur le [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Elle peut également s’exécuter sur le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , car il s’agit d’un sur-ensemble de [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
