---
title: "D&#233;pannage des exceptions&#160;: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.IdentityModel.Selectors.UnsupportedPolicyOptionsException (exception)"
  - "UnsupportedPolicyOptionsException (exception)"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
Une exception <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException> indique qu'une stratégie a été fournie au système, qui comprend des options qui ne sont pas prises en charge. Les restrictions qui peuvent provoquer ces dysfonctionnements sont les suivantes :  
  
 Un destinataire a demandé un jeton du service d'émission de jeton de sécurité local en spécifiant http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self comme émetteur du jeton. Or, l'une des spécifications indiquées dans la stratégie n'est pas prise en charge par le service d'émission de jeton de sécurité local de CardSpace. Pour plus d’informations, consultez [A Technical Reference for the Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkId=102401). Voici quelques exemples d'options non prises en charge :  
  
-   Une revendication demandée par le destinataire n’est pas dans la liste des revendications prises en charge spécifiée dans la section [Supported Claim Types](http://go.microsoft.com/fwlink/?LinkId=102402) de l’article « A Technical Reference for the Information Card Profile V1.0 ».  
  
-   Le type de jeton est autre que SAML 1.0 ou 1.1.  
  
-   Pour les sites non\-SSL, une clé n'est pas symétrique.  
  
-   KeyWrapAlgorithm diffère de l'algorithme par défaut.  
  
-   Un élément non pris en charge est spécifié dans la stratégie. Les éléments pris en charge sont les suivants :  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   KeySize  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   wst:RequestType n'est pas du type Problème.  
  
-   Pour les types de clé asymétrique, la taille d'une clé n'est pas 2048.  
  
## Voir aussi  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)