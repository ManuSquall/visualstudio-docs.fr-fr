---
title: "Sécurité et assemblys satellites localisés | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5f2834e267e2494f62f5cfed9121a0a94a22afb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="security-and-localized-satellite-assemblies"></a>Sécurité et assemblys satellites localisés

Si votre assembly principal utilise des noms forts, les assemblys satellites doivent être signés avec la même clé privée que l’assembly principal. Si la paire de clés publique/privée ne correspond pas entre les assemblys principal et satellites, vos ressources ne sont pas chargées. Pour plus d’informations sur la signature des assemblys, consultez [Comment : signer un assembly avec un nom fort](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 En règle générale, il peut s’avérer nécessaire que le groupe de signature de votre organisation ou une organisation de signature externe signe avec la clé privée. En effet, en raison de la nature sensible de la clé privée, l’accès est souvent limité à quelques personnes. Vous pouvez utiliser la signature différée pendant le développement. Pour plus d'informations, consultez [Temporisation de signature d'un assembly](/dotnet/framework/app-domains/delay-sign-assembly).  
  
## <a name="see-also"></a>Voir aussi

- [Considérations de la sécurité d’assembly](/dotnet/framework/app-domains/assembly-security-considerations)  - [Concept des clés de sécurité](/dotnet/standard/security/key-security-concepts)   
- [Introduction aux applications internationales basées sur le .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
- [Localisation d’applications](../ide/localizing-applications.md)   
- [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)