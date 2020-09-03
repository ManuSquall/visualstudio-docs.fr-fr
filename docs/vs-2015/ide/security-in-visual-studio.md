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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d967bd1f7a425ccd9dda5a938535788d961352f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672882"
---
# <a name="security-in-visual-studio"></a>Sécurité dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous devez prendre en compte la sécurité dans tous les aspects du développement de votre application, de la conception jusqu'au déploiement. Commencez par exécuter Visual Studio avec le niveau de sécurité le plus élevé possible. Consultez [autorisations utilisateur](../ide/user-permissions-and-visual-studio.md).

 Pour pouvoir développer effectivement des applications sécurisées, vous devez comprendre les concepts fondamentaux de la sécurité, de même que connaître les fonctionnalités de sécurité des plateformes pour lesquelles vous développez. Vous devez également connaître les techniques de codage sécurisé.

## <a name="understanding-security"></a>Présentation de la sécurité
 [Sécurité](https://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) Décrit la sécurité d’accès du code, la sécurité basée sur les rôles, la stratégie de sécurité et les outils de sécurité du .NET Framework.

## <a name="coding-for-security"></a>Codage de la sécurité
 La plupart des erreurs de codage conduisant à des failles de sécurité sont dues à des hypothèses erronées effectuées par les développeurs lorsqu'ils travaillent avec des entrées d'utilisateur. Elles peuvent également résulter d'une mauvaise connaissance de la plateforme pour laquelle le développement est réalisé.

 [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) Fournit des instructions sur le classement de vos composants pour résoudre les problèmes de sécurité.

 [Bonnes pratiques de sécurité](https://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) Explique les dépassements de mémoire tampon et présente en détail la fonctionnalité de vérification de la sécurité de Microsoft Visual C++ fournie par le repère de compilation /GS.
