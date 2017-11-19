---
title: "CA5351 N’utilisez pas les algorithmes de chiffrement cassés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32cd265451609e99c062270aeda0b278b98240d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 N’utilisez pas les algorithmes de chiffrement cassés
|||  
|-|-|  
|TypeName|DoNotUseBrokenCryptographicAlgorithms|  
|CheckId|CA5351|  
|Catégorie|Microsoft.Cryptography|  
|Modification avec rupture|Sans rupture|  
  
> [!NOTE]
>  Cet avertissement a été mis à jour pour la dernière fois en novembre 2015.  
  
## <a name="cause"></a>Cause  
 Les fonctions de hachage telles que <xref:System.Security.Cryptography.MD5> et les algorithmes de chiffrement tels que <xref:System.Security.Cryptography.DES> et <xref:System.Security.Cryptography.RC2> peuvent présenter un risque substantiel et provoquer l’exposition d’informations sensibles au moyen de techniques d’attaque triviales telles que les collisions de hachage et les attaques par force brute.  
  
 Les algorithmes de chiffrement répertoriés ci-dessous sont soumise aux attaques cryptographiques. L’algorithme de hachage de chiffrement <xref:System.Security.Cryptography.MD5> est soumis aux attaques par collision de hachage.  En fonction de l’utilisation, une collision de hachage peut entraîner un emprunt d’identité, une falsification ou d’autres types d’attaques sur les systèmes qui reposent sur la sortie de chiffrement unique d’une fonction de hachage. Les algorithmes de chiffrement <xref:System.Security.Cryptography.DES> et <xref:System.Security.Cryptography.RC2> sont soumis aux attaques de chiffrement qui peuvent entraîner une divulgation involontaire de données chiffrées.  
  
## <a name="rule-description"></a>Description de la règle  
 Les algorithmes de chiffrement cassés ne sont pas considérés comme sécurisés, et leur utilisation doit être déconseillée. L’algorithme de hachage MD5 est vulnérable à des attaques par collision connues, bien que la vulnérabilité varie en fonction du contexte d’utilisation.  Les algorithmes de hachage utilisés pour garantir l’intégrité des données (par exemple une signature de fichier ou un certificat numérique) sont particulièrement vulnérables.  Dans ce contexte, des personnes malveillantes peuvent générer deux éléments distincts de données (et donc remplacer des données ordinaires par des données malveillantes) sans modifier la valeur de hachage ou invalider une signature numérique associée.  
  
 Pour les algorithmes de chiffrement :  
  
-   Le chiffrement<xref:System.Security.Cryptography.DES> contient une clé de petite taille qui peut être cassée par la force brute en moins d’une journée.  
  
-   Le chiffrement<xref:System.Security.Cryptography.RC2> est vulnérable à une attaque par clé associée, où le pirate recherche les relations mathématiques entre toutes les valeurs de clés.  
  
 Cette règle se déclenche quand elle détecte l’une des fonctions de chiffrement ci-dessus dans le code source et elle affiche un avertissement à l’utilisateur.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Utilisez des options de chiffrement plus fortes :  
  
-   Pour MD5, utilisez des hachages de la famille [SHA-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) (par exemple <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).  
  
-   Pour DES et RC2, utilisez le chiffrement <xref:System.Security.Cryptography.Aes> .  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle, sauf s’il a été examiné par un expert en chiffrement.  
  
## <a name="pseudo-code-example"></a>Exemple de pseudo-code  
 L’exemple de pseudo-code suivant illustre le modèle détecté par cette règle et les alternatives possibles.  
  
### <a name="md5-hashing-violation"></a>Violation de hachage MD5  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = MD5.Create();  
  
```  
  
### <a name="solution"></a>Solution  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="rc2-encryption-violation"></a>Violation de chiffrement RC2  
  
```  
using System.Security.Cryptography;   
...    
RC2 encAlg = RC2.Create();  
  
```  
  
### <a name="solution"></a>Solution  
  
```  
using System.Security.Cryptography;   
...   
using (AesManaged encAlg = new AesManaged())   
{   
  ...   
}  
```  
  
### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Violation de chiffrement  
  
```  
using System.Security.Cryptography;   
...   
DES encAlg = DES.Create();  
  
```  
  
### <a name="solution"></a>Solution  
  
```  
using System.Security.Cryptography;   
...   
using (AesManaged encAlg = new AesManaged())   
{   
  ...   
}  
```