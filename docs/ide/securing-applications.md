---
title: Sécurité
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87e9cb7e9400253713caab17da04c44eb11f5ed1
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843908"
---
# <a name="secure-applications"></a>Sécuriser des applications

Vous devez prendre en compte la sécurité dans tous les aspects du développement de votre application, de la conception jusqu'au déploiement. Commencez par exécuter Visual Studio avec le niveau de sécurité le plus élevé possible. Consultez [Autorisations utilisateur](../ide/user-permissions-and-visual-studio.md).

Pour pouvoir développer effectivement des applications sécurisées, vous devez comprendre les concepts fondamentaux de la sécurité, de même que connaître les fonctionnalités de sécurité des plateformes pour lesquelles vous développez. Vous devez également connaître les techniques de codage sécurisé.

## <a name="code-for-security"></a>Coder avec des fonctionnalités de sécurité

La plupart des erreurs de codage conduisant à des failles de sécurité sont dues à des hypothèses erronées effectuées par les développeurs quand ils travaillent avec des entrées d’utilisateur. Elles peuvent également résulter d’une mauvaise connaissance de la plateforme pour laquelle le développement est réalisé.

- Les [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines) décrivent les différents procédés permettant de concevoir du code .NET qui fonctionne avec le système de sécurité.
- L’article sur les [Bonnes pratiques de sécurité pour C++](/cpp/top/security-best-practices-for-cpp) contient des informations sur les outils de sécurité et pratiques pour les développeurs C++.

## <a name="build-for-security"></a>Générer avec des fonctionnalités de sécurité

La sécurité est également un facteur important à prendre en compte dans le processus de génération. Quelques étapes supplémentaires peuvent améliorer la sécurité d’une application déployée et empêcher l’ingénierie à rebours non autorisée, l’usurpation d’identité ou d’autres attaques :

- [Dotfuscator](dotfuscator/index.md) est gratuit et vous aide à protéger les assemblys .NET contre l’ingénierie à rebours et l’utilisation non autorisée (par exemple le débogage non autorisé).
- La [signature avec nom fort](managing-assembly-and-manifest-signing.md) peut être utilisée pour identifier de façon univoque des composants logiciels et empêcher l’usurpation de noms.

## <a name="see-also"></a>Voir aussi

- [Sécurité dans le .NET Framework](/dotnet/standard/security/index)
- [Sécurité Azure](/azure/security/)
- [Guide de sécurité de Windows 10 Mobile](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Fonctionnalités de sécurité de la plateforme Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [Sécurité ASP.NET Core](/aspnet/core/security/?view=aspnetcore-2.1)
- [Sécurité de Windows Forms](/dotnet/framework/winforms/windows-forms-security)