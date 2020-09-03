---
title: '&lt;assembly &gt; , élément (déploiement ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b77cfacf3dca2c2cc20d674f79929e9958a16d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155735"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;assembly &gt; , élément (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Élément de niveau supérieur du manifeste de déploiement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <assembly    
   manifestVersion  
/>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L' `assembly` élément est l’élément racine et est obligatoire. Son premier élément contenu doit être un `assemblyIdentity` élément. Les éléments de manifeste doivent se trouver dans les espaces de noms suivants : `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` et `http://www.w3.org/2000/09/xmldsig#` . Les éléments enfants de l’assembly doivent également figurer dans ces espaces de noms, par héritage ou par balisage.  
  
 L’élément `assembly` comporte l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`manifestVersion`|Obligatoire. Cet attribut doit avoir la valeur `1.0` .|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un `assembly` élément dans un manifeste de déploiement pour une application déployée à l’aide de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Cet exemple de code fait partie d’un exemple plus complet fourni pour la rubrique du [manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md) .  
  
```  
<asmv1:assembly   
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [\<assembly> Appartient](../deployment/assembly-element-clickonce-application.md)
