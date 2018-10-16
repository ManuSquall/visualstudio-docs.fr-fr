---
title: '&lt;publisherIdentity&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 1d25b9ff6c4d8a3eb43d18d5c9849ba7199ffe79
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226939"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; , élément (déploiement ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Contient des informations sur l'éditeur qui a signé ce manifeste de déploiement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le `publisherIdentity` élément est requis pour les manifestes signés. Le tableau suivant montre les attributs que le `publisherIdentity` élément prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Obligatoire. Décrit l’identité du tiers qui a publié cette application.|  
|`issuerKeyHash`|Obligatoire. Contient le hachage SHA-1 de la clé publique de l’émetteur du certificat.|  
  
#### <a name="parameters"></a>Paramètres  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise  
  
## <a name="subhead"></a>Sous-titre



