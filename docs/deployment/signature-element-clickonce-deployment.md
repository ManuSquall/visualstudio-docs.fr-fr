---
title: '&lt;&gt;Élément signature (déploiement ClickOnce) | Microsoft Docs'
description: L’élément signature contient les informations nécessaires pour signer numériquement ce manifeste de déploiement. La signature d’un manifeste de déploiement est facultative, mais recommandée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7a86236087bdbff8cf82ca4821573f9f799d019
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349280"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;&gt;Élément signature (déploiement ClickOnce)
Contient les informations nécessaires pour signer numériquement ce manifeste de déploiement.

## <a name="syntax"></a>Syntaxe

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Notes
 La signature d’un manifeste de déploiement à l’aide d’une signature d’enveloppe est facultative, mais recommandée. Pour plus d’informations sur la signature des fichiers XML, consultez la recommandation World Wide Web Consortium « XML-Signature Syntax and Processing », décrite dans [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 Si vous souhaitez signer votre manifeste, des hachages doivent être fournis pour tous les fichiers. Un manifeste avec des fichiers qui ne sont pas hachés ne peut pas être signé, car les utilisateurs ne peuvent pas vérifier le contenu des fichiers non hachés.

## <a name="example"></a> Exemple
 L’exemple de code suivant illustre un `Signature` élément dans un manifeste de déploiement utilisé dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement.

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>Voir aussi
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
