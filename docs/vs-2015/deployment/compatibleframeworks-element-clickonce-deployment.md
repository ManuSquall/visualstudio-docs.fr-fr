---
title: '&lt;compatibleFrameworks&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
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
ms.openlocfilehash: fc6446f30f9429811c5382e0a49eca16b63cd9b5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422966"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; , élément (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifie les versions du .NET Framework pour lesquelles cette application peut s'installer et s'exécuter.  
  
> [!NOTE]
> [MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) ne prend pas en charge la `compatibleFrameworks` élément lors de l’enregistrement d’un manifeste d’application qui a déjà été signé avec un certificat à l’aide [MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). À la place, vous devez utiliser [Mage.exe](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
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
 Le `compatibleFrameworks` élément est requis pour les manifestes de déploiement qui ciblent le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] runtime fourni par [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ou version ultérieure. Le `compatibleFrameworks` élément contient un ou plusieurs `framework` éléments qui spécifient les versions du .NET Framework sur laquelle cette application peut s’exécuter. Le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] runtime exécutera l’application sur le premier disponible `framework` dans cette liste.  
  
 Le tableau suivant répertorie l’attribut qui le `compatibleFrameworks` élément prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`S` `upportUrl`|Optionnel. Spécifie l’URL où la version de .NET Framework compatible par défaut peut être téléchargée.|  
  
## <a name="framework"></a>framework  
 Obligatoire. Le tableau suivant répertorie les attributs qui la `framework` élément prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`targetVersion`|Obligatoire. Spécifie le numéro de version du .NET Framework cible.|  
|`profile`|Obligatoire. Spécifie le profil du .NET Framework cible.|  
|`supportedRuntime`|Obligatoire. Spécifie le numéro de version du runtime associé à la cible de .NET Framework.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 Le code suivant montre l’exemple un `compatibleFrameworks` élément dans un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifeste de déploiement. Ce déploiement peut s’exécuter sur le [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]. Il peut également s’exécuter le [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , car il est un sur-ensemble de la [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
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
