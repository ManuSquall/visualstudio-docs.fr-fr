---
title: '&lt;Signature&gt; , élément (déploiement ClickOnce) | Microsoft Docs'
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
ms.openlocfilehash: 1c636a4178cf278c2bb0ad75f4e78b94758dda30
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605196"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature&gt; , élément (déploiement ClickOnce)
Contient les informations nécessaires pour signer numériquement ce manifeste de déploiement.

## <a name="syntax"></a>Syntaxe

```xml

      <Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>Remarques
 Signature d’un manifeste de déploiement à l’aide d’une signature d’enveloppe est facultative, mais recommandé. Pour plus d’informations sur la signature des fichiers XML, consultez la recommandation du World Wide Web Consortium, « XML-Signature Syntax and Processing », décrit dans [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).

 Si vous souhaitez signer votre manifeste, les hachages doivent être fournies pour tous les fichiers. Impossible de signer un manifeste avec des fichiers qui ne sont pas hachés, étant donné que les utilisateurs ne peuvent pas vérifier le contenu des fichiers non hachées.

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