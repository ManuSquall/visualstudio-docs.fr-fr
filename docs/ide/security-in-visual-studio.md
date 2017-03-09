---
title: "Sécurité dans Visual Studio| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8e34062596ab2f87ae97934b89b4c292e8f28f32
ms.lasthandoff: 02/22/2017

---
# <a name="security-in-visual-studio"></a>Sécurité dans Visual Studio
Vous devez prendre en compte la sécurité dans tous les aspects du développement de votre application, de la conception jusqu'au déploiement. Commencez par exécuter Visual Studio avec le niveau de sécurité le plus élevé possible. Consultez [Autorisations utilisateur](../ide/user-permissions-and-visual-studio.md).  
  
 Pour pouvoir développer effectivement des applications sécurisées, vous devez comprendre les concepts fondamentaux de la sécurité, de même que connaître les fonctionnalités de sécurité des plateformes pour lesquelles vous développez. Vous devez également connaître les techniques de codage sécurisé.  
  
## <a name="understanding-security"></a>Présentation de la sécurité  
 [Sécurité](http://msdn.microsoft.com/Library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 Décrit la sécurité d'accès du code, la sécurité basée sur les rôles, la stratégie de sécurité et les outils de sécurité du .NET Framework.  
  
 [Dix principaux conseils de sécurité à connaître pour défendre votre code](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Décrit les problèmes auxquels vous devez être attentif pour ne pas compromettre vos données ou votre système.  
  
## <a name="coding-for-security"></a>Codage de la sécurité  
 La plupart des erreurs de codage conduisant à des failles de sécurité sont dues à des hypothèses erronées effectuées par les développeurs lorsqu'ils travaillent avec des entrées d'utilisateur. Elles peuvent également résulter d'une mauvaise connaissance de la plateforme pour laquelle le développement est réalisé.  
  
 [Instructions de codage sécurisé](http://msdn.microsoft.com/Library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 Fournit des instructions sur le classement de vos composants afin de résoudre les problèmes de sécurité.  
  
 [Bonnes pratiques de sécurité](/visual-cpp/top/security-best-practices-for-cpp)  
 Explique les dépassements de mémoire tampon et présente en détails la fonctionnalité de vérification de la sécurité de Microsoft Visual C++ fournie par le repère de compilation /GS.
