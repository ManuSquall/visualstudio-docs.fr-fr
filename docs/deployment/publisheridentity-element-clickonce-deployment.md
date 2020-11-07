---
title: '&lt;&gt;élément publisherIdentity (déploiement ClickOnce) | Microsoft Docs'
description: L’élément publisherIdentity contient des informations sur le serveur de publication qui a signé un manifeste de déploiement. L’élément est requis pour les manifestes signés.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1eb4b67bfdca13c63480f3dde82004d87cd4a12a
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350684"
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