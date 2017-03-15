---
title: "&lt;Signature&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Signature> element [ClickOnce deployment manifest]"
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;Signature&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contient les informations nécessaires à la signature numérique de ce manifeste de déploiement.  
  
## Syntaxe  
  
```  
  
      <Signature>   
   XML signature information   
</Signature>  
```  
  
## Notes  
 Signer un manifeste de déploiement à l'aide d'une signature d'enveloppe est facultatif, mais recommandé.  Pour plus d'informations sur la signature de fichiers XML, consultez la recommandation du W3C \(World Wide Web Consortium\) « XML\-Signature Syntax and Processing », à l'adresse [http:\/\/www.w3.org\/TR\/xmldsig\-core\/](http://www.w3.org/TR/xmldsig-core/).  
  
 Si vous souhaitez signer votre manifeste, les hachages doivent être fournis pour tous les fichiers.  Un manifeste contenant des fichiers qui ne sont pas hachés ne peut pas être signé, car les utilisateurs ne peuvent pas vérifier le contenu de fichiers non hachés.  
  
## Exemple  
 L'exemple de code suivant illustre un élément `Signature` dans un manifeste de déploiement utilisé dans un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
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
  
## Voir aussi  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)