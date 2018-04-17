---
title: '&lt;Signature&gt; élément (déploiement ClickOnce) | Documents Microsoft'
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
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: cae29bf7f1d5207258ddc90e7287f7fb3a3b2989
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature&gt; élément (déploiement ClickOnce)
Contient les informations nécessaires pour signer numériquement ce manifeste de déploiement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## <a name="remarks"></a>Notes  
 Signature d’un manifeste de déploiement à l’aide d’une signature d’enveloppe est facultative, mais recommandé. Pour plus d’informations sur la signature XML fichiers consultez la recommandation du World Wide Web Consortium, « XML Signature Syntax and Processing », décrit dans [ http://www.w3.org/TR/xmldsig-core/ ](http://www.w3.org/TR/xmldsig-core/).  
  
 Si vous souhaitez signer votre manifeste, les hachages doivent être fournis pour tous les fichiers. Impossible de signer un manifeste avec des fichiers qui ne sont pas hachées, car les utilisateurs ne peuvent pas vérifier le contenu des fichiers non hachées.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un `Signature` élément dans un manifeste de déploiement utilisé dans un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement.  
  
```  
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
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)