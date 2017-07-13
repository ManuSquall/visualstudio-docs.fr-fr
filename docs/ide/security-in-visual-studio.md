---
title: "Sécurité dans Visual Studio| Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 7314921a9416184c4bd63312bd5a82cef4102ddd
ms.contentlocale: fr-fr
ms.lasthandoff: 05/30/2017

---
# Sécurité dans Visual Studio
<a id="security-in-visual-studio" class="xliff"></a>
Vous devez prendre en compte la sécurité dans tous les aspects du développement de votre application, de la conception jusqu'au déploiement. Commencez par exécuter Visual Studio avec le niveau de sécurité le plus élevé possible. Consultez [Autorisations utilisateur](../ide/user-permissions-and-visual-studio.md).  
  
 Pour pouvoir développer effectivement des applications sécurisées, vous devez comprendre les concepts fondamentaux de la sécurité, de même que connaître les fonctionnalités de sécurité des plateformes pour lesquelles vous développez. Vous devez également connaître les techniques de codage sécurisé.  
  
## Présentation de la sécurité
<a id="understanding-security" class="xliff"></a>  
 [Sécurité](/dotnet/standard/security/index)  
 Décrit la sécurité d'accès du code, la sécurité basée sur les rôles, la stratégie de sécurité et les outils de sécurité du .NET Framework.  
  
 [Dix principaux conseils de sécurité à connaître pour défendre votre code](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Décrit les problèmes auxquels vous devez être attentif pour ne pas compromettre vos données ou votre système.  
  
## Codage de la sécurité
<a id="coding-for-security" class="xliff"></a>  
 La plupart des erreurs de codage conduisant à des failles de sécurité sont dues à des hypothèses erronées effectuées par les développeurs lorsqu'ils travaillent avec des entrées d'utilisateur. Elles peuvent également résulter d'une mauvaise connaissance de la plateforme pour laquelle le développement est réalisé.  
  
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)  
 Fournit des instructions sur le classement de vos composants afin de résoudre les problèmes de sécurité.  
  
 [Bonnes pratiques de sécurité](/cpp/top/security-best-practices-for-cpp)  
 Explique les dépassements de mémoire tampon et présente en détails la fonctionnalité de vérification de la sécurité de Microsoft Visual C++ fournie par le repère de compilation /GS.

## Générer avec des fonctionnalités de sécurité
<a id="building-for-security" class="xliff"></a>  
 La sécurité est également un facteur important à prendre en compte dans le processus de génération.  Quelques étapes supplémentaires peuvent améliorer la sécurité d’une application déployée et empêcher l’ingénierie à rebours non autorisée, l’usurpation d’identité ou d’autres attaques.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Explique comment installer et commencer à utiliser PreEmptive Protection - Dotfuscator Community Edition (gratuit) pour protéger les assemblys .NET de l’ingénierie à rebours et des utilisations non autorisées (comme un débogage non autorisé).
  
 [Gestion d’assembly et signature de manifeste](managing-assembly-and-manifest-signing.md)  
 Présente la signature avec nom fort, qui peut être utilisée pour identifier de façon univoque des composants logiciels, empêchant ainsi l’usurpation de noms.
