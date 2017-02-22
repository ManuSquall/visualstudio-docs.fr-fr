---
title: "CA5350&#160;: N’utilisez pas d’algorithmes de chiffrement faibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA5350&#160;: N’utilisez pas d’algorithmes de chiffrement faibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Catégorie|Microsoft.Cryptography|  
|Modification avec rupture|Sans rupture|  
  
> [!NOTE]
>  Cet avertissement a été mis à jour pour la dernière fois en novembre 2015.  
  
## Cause  
 Les algorithmes de chiffrement, tels que <xref:System.Security.Cryptography.TripleDES>, et les algorithmes de hachage, tels que <xref:System.Security.Cryptography.SHA1> et <xref:System.Security.Cryptography.RIPEMD160>, sont considérés comme faibles.  
  
 Ces algorithmes de chiffrement n’offrent pas autant de sécurité que leurs équivalents plus modernes. Les algorithmes de chiffrement et de hachage <xref:System.Security.Cryptography.SHA1> et <xref:System.Security.Cryptography.RIPEMD160> offrent moins de résistance aux collisions que les algorithmes de hachage plus modernes. L’algorithme de chiffrement <xref:System.Security.Cryptography.TripleDES> fournit moins de bits de sécurité que les algorithmes de chiffrement plus modernes.  
  
## Description de la règle  
 Des algorithmes de chiffrement et des fonctions de hachage faibles sont utilisés aujourd’hui pour plusieurs raisons, mais ils ne doivent pas servir à garantir la confidentialité des données qu’ils protègent.  
  
 La règle se déclenche et lève un avertissement quand elle trouve des algorithmes 3DES, SHA1 ou RIPEMD160 dans le code.  
  
## Comment corriger les violations  
 Utilisez des options de chiffrement plus fortes :  
  
-   Pour le chiffrement TripleDES, utilisez le chiffrement <xref:System.Security.Cryptography.Aes>.  
  
-   Pour les fonctions de hachage SHA1 et RIPEMD160, utilisez les fonctions de la famille [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) \(par exemple, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>\).  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle quand le niveau de protection nécessaire pour les données ne nécessite pas une garantie de sécurité.  
  
## Exemple de pseudo\-code  
 Au moment de l’écriture de cet article, l’exemple de pseudo\-code suivant illustre le schéma détecté par cette règle.  
  
### Violation de hachage SHA\-1  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### Solution  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Violation de hachage RIPEMD160  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### Solution  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Violation de chiffrement TripleDES  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### Solution  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```