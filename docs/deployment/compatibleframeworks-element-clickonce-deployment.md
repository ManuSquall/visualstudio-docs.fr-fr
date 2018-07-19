---
title: '&lt;compatibleFrameworks&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44329fc4c2ec5e9f2f8352d69ea487f23cbe3c5a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077683"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; , élément (déploiement ClickOnce)
Identifie les versions du .NET Framework pour lesquelles cette application peut s'installer et s'exécuter.  
  
> [!NOTE]
>  [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) ne prend pas en charge la `compatibleFrameworks` élément lors de l’enregistrement d’un manifeste d’application qui a déjà été signé avec un certificat à l’aide [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Au lieu de cela, vous devez utiliser [ *Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
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
 Le `compatibleFrameworks` élément est requis pour les manifestes de déploiement qui ciblent le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] runtime fourni par [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ou version ultérieure. Le `compatibleFrameworks` élément contient un ou plusieurs `framework` éléments qui spécifient les versions du .NET Framework sur laquelle cette application peut s’exécuter. Le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] runtime exécutera l’application sur le premier disponible `framework` dans cette liste.  
  
 Le tableau suivant répertorie l’attribut qui le `compatibleFrameworks` élément prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`S` `upportUrl`|Facultatif. Spécifie l’URL où la version de .NET Framework compatible par défaut peut être téléchargée.|  
  
## <a name="framework"></a>infrastructure  
 Obligatoire. Le tableau suivant répertorie les attributs qui la `framework` élément prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`targetVersion`|Obligatoire. Spécifie le numéro de version du .NET Framework cible.|  
|`profile`|Obligatoire. Spécifie le profil du .NET Framework cible.|  
|`supportedRuntime`|Obligatoire. Spécifie le numéro de version du runtime associé à la cible de .NET Framework.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 Le code suivant montre l’exemple un `compatibleFrameworks` élément dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste de déploiement. Ce déploiement peut s’exécuter sur le [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Il peut également s’exécuter le [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , car il est un sur-ensemble de la [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```xml  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)