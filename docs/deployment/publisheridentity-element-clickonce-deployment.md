---
title: '&lt;publisherIdentity&gt; élément (déploiement ClickOnce) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 9d759072c2de61840ff0aa0eab9a3fdf77fb4d07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity&gt; élément (déploiement ClickOnce)
Contient des informations sur l'éditeur qui a signé ce manifeste de déploiement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le `publisherIdentity` élément est requis pour les manifestes signés. Le tableau suivant montre les attributs que la `publisherIdentity` élément prend en charge.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Obligatoire. Décrit l’identité du tiers qui a publié cette application.|  
|`issuerKeyHash`|Obligatoire. Contient le hachage SHA-1 de la clé publique de l’émetteur du certificat.|  
  
#### <a name="parameters"></a>Paramètres  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="subhead"></a>Sous-titre