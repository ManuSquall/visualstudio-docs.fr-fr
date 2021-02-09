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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d95398285d9106719f3c2444d54202b81cfee4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877497"
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

## <a name="example"></a>Exemple
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
