---
title: Sécurité et assemblys satellites localisés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c810c6c7e0c0c73557e6b38860c1e6d3953b225
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691290"
---
# <a name="security-and-localized-satellite-assemblies"></a>Sécurité et assemblys satellites localisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si votre assembly principal utilise des noms forts, les assemblys satellites doivent être signés avec la même clé privée que l’assembly principal. Si la paire de clés publique/privée ne correspond pas entre les assemblys principal et satellites, vos ressources ne sont pas chargées. Pour plus d’informations sur la signature des assemblys, consultez [Comment : signer un assembly avec un nom fort](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 En règle générale, il peut s’avérer nécessaire que le groupe de signature de votre organisation ou une organisation de signature externe signe avec la clé privée. En effet, en raison de la nature sensible de la clé privée, l’accès est souvent limité à quelques personnes. Vous pouvez utiliser la signature différée pendant le développement. Pour plus d’informations, consultez [Temporisation de signature d’un assembly](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Voir aussi  
 [Aspects de la sécurité des assemblys](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Concepts fondamentaux sur la sécurité](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Introduction aux applications internationales basées sur le .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localisation d’applications](../ide/localizing-applications.md)   
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)
