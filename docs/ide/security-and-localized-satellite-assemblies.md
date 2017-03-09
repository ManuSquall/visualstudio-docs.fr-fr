---
title: "Sécurité et assemblys satellites localisés | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
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
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 587b403257a5fadefd32e57ecdd9914bd60a9e26
ms.lasthandoff: 02/22/2017

---
# <a name="security-and-localized-satellite-assemblies"></a>Sécurité et assemblys satellites localisés
Si votre assembly principal utilise des noms forts, les assemblys satellites doivent être signés avec la même clé privée que l’assembly principal. Si la paire de clés publique/privée ne correspond pas entre les assemblys principal et satellites, vos ressources ne sont pas chargées. Pour plus d’informations sur la signature des assemblys, consultez [Comment : signer un assembly avec un nom fort](http://msdn.microsoft.com/Library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 En règle générale, il peut s’avérer nécessaire que le groupe de signature de votre organisation ou une organisation de signature externe signe avec la clé privée. En effet, en raison de la nature sensible de la clé privée, l’accès est souvent limité à quelques personnes. Vous pouvez utiliser la signature différée pendant le développement. Pour plus d’informations, consultez [Temporisation de signature d’un assembly](http://msdn.microsoft.com/Library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Voir aussi  
 [Aspects de la sécurité des assemblys](http://msdn.microsoft.com/Library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Concepts fondamentaux sur la sécurité](http://msdn.microsoft.com/Library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Introduction aux applications internationales basées sur le .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localisation d’applications](../ide/localizing-applications.md)   
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)
