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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891291"
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

## <a name="remarks"></a>Remarques

## <a name="requirements"></a>Spécifications

## <a name="subhead"></a>Sous-titre