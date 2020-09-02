---
title: '&lt;&gt;élément publisherIdentity (déploiement ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927537"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;&gt;élément publisherIdentity (déploiement ClickOnce)
Contient des informations sur l'éditeur qui a signé ce manifeste de déploiement.

## <a name="syntax"></a>Syntaxe

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L' `publisherIdentity` élément est requis pour les manifestes signés. Le tableau suivant présente les attributs `publisherIdentity` pris en charge par l’élément.

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