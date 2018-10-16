---
title: Avertissements de chiffrement | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4d795d9c6b6cefcf15c19867cc954ab898215a36
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201498"
---
# <a name="cryptography-warnings"></a>Avertissements de chiffrement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les avertissements de chiffrement prennent en charge la sécurité des bibliothèques et des applications grâce à une utilisation correcte du chiffrement. Ces avertissements contribuent à empêcher la présence de défauts de sécurité dans votre programme. Si vous désactivez chacun de ces avertissements, vous devez indiquer clairement le motif de l’opération dans le code et également en informer le responsable de la sécurité désigné pour votre projet de développement.  
  
|Règle|Description|  
|----------|-----------------|  
|[CA5350 : N’utilisez pas d’algorithmes de chiffrement faibles](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Des algorithmes de chiffrement et des fonctions de hachage faibles sont utilisés aujourd’hui pour plusieurs raisons, mais ils ne doivent pas servir à garantir la confidentialité ou l’intégrité des données qu’ils protègent.        Cette règle se déclenche lorsqu’elle détecte des algorithmes TripleDES, SHA1 ou RIPEMD160 dans le code.|  
|[CA5351 : N’utilisez pas d’algorithmes de chiffrement cassés](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Les algorithmes de chiffrement cassés ne sont pas considérés comme sécurisés, et leur utilisation doit être fortement déconseillée. Cette règle se déclenche lorsqu’elle détecte l’algorithme de hachage MD5 ou les algorithmes de chiffrement RC2 ou DES dans le code.|



