---
title: Sécurité
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f89e9a58d1ea501b9d92a44eead5e343cc7c014b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "57866935"
---
# <a name="security-in-visual-studio"></a>Sécurité dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous devez prendre en compte la sécurité dans tous les aspects du développement de votre application, de la conception jusqu'au déploiement. Commencez par exécuter Visual Studio avec le niveau de sécurité le plus élevé possible. Consultez [Autorisations utilisateur](../ide/user-permissions-and-visual-studio.md).

 Pour pouvoir développer effectivement des applications sécurisées, vous devez comprendre les concepts fondamentaux de la sécurité, de même que connaître les fonctionnalités de sécurité des plateformes pour lesquelles vous développez. Vous devez également connaître les techniques de codage sécurisé.

## <a name="understanding-security"></a>Présentation de la sécurité
 [Sécurité](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) Décrit la sécurité d’accès du code, la sécurité basée sur les rôles, la stratégie de sécurité et les outils de sécurité du .NET Framework.

## <a name="coding-for-security"></a>Codage de la sécurité
 La plupart des erreurs de codage conduisant à des failles de sécurité sont dues à des hypothèses erronées effectuées par les développeurs lorsqu'ils travaillent avec des entrées d'utilisateur. Elles peuvent également résulter d'une mauvaise connaissance de la plateforme pour laquelle le développement est réalisé.

 [Instructions de codage sécurisé](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) Fournit des instructions sur le classement de vos composants pour résoudre les problèmes de sécurité.

 [Bonnes pratiques de sécurité](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) Explique les dépassements de mémoire tampon et présente en détail la fonctionnalité de vérification de la sécurité de Microsoft Visual C++ fournie par le repère de compilation /GS.
