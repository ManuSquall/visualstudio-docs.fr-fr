---
title: "Sécurité dans Visual Studio| Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: "20"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 25b0f76c657f4d4df7375b4fc9e418e8806bd51f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="security-in-visual-studio"></a>Sécurité dans Visual Studio
Vous devez prendre en compte la sécurité dans tous les aspects du développement de votre application, de la conception jusqu'au déploiement. Commencez par exécuter Visual Studio avec le niveau de sécurité le plus élevé possible. Consultez [Autorisations utilisateur](../ide/user-permissions-and-visual-studio.md).  
  
 Pour pouvoir développer effectivement des applications sécurisées, vous devez comprendre les concepts fondamentaux de la sécurité, de même que connaître les fonctionnalités de sécurité des plateformes pour lesquelles vous développez. Vous devez également connaître les techniques de codage sécurisé.  
  
## <a name="understanding-security"></a>Présentation de la sécurité  
 [Sécurité](/dotnet/standard/security/index)  
 Décrit la sécurité d'accès du code, la sécurité basée sur les rôles, la stratégie de sécurité et les outils de sécurité du .NET Framework.  
  
 [Dix principaux conseils de sécurité à connaître pour défendre votre code](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Décrit les problèmes auxquels vous devez être attentif pour ne pas compromettre vos données ou votre système.  
  
## <a name="coding-for-security"></a>Codage de la sécurité  
 La plupart des erreurs de codage conduisant à des failles de sécurité sont dues à des hypothèses erronées effectuées par les développeurs lorsqu'ils travaillent avec des entrées d'utilisateur. Elles peuvent également résulter d'une mauvaise connaissance de la plateforme pour laquelle le développement est réalisé.  
  
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)  
 Fournit des instructions sur le classement de vos composants afin de résoudre les problèmes de sécurité.  
  
 [Bonnes pratiques de sécurité](/cpp/top/security-best-practices-for-cpp)  
 Explique les dépassements de mémoire tampon et présente en détails la fonctionnalité de vérification de la sécurité de Microsoft Visual C++ fournie par le repère de compilation /GS.

## <a name="building-for-security"></a>Générer avec des fonctionnalités de sécurité  
 La sécurité est également un facteur important à prendre en compte dans le processus de génération.  Quelques étapes supplémentaires peuvent améliorer la sécurité d’une application déployée et empêcher l’ingénierie à rebours non autorisée, l’usurpation d’identité ou d’autres attaques.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Explique comment installer et commencer à utiliser PreEmptive Protection - Dotfuscator Community Edition (gratuit) pour protéger les assemblys .NET de l’ingénierie à rebours et des utilisations non autorisées (comme un débogage non autorisé).
  
 [Gestion d’assembly et signature de manifeste](managing-assembly-and-manifest-signing.md)  
 Présente la signature avec nom fort, qui peut être utilisée pour identifier de façon univoque des composants logiciels, empêchant ainsi l’usurpation de noms.