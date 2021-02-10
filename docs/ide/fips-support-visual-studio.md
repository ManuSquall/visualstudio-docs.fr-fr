---
title: Prise en charge de Visual Studio pour FIPS
titleSuffix: ''
description: Découvrez comment Visual Studio prend en charge le mode de fonctionnement approuvé de la publication de normes FIPS (Federal Information Processing Standard) 140-2 pour Windows, Azure et .NET.
ms.custom: SEO-VS-2020
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d6cb0d2bbcb1ec1d13f5916a7c2b1cd97824fb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945537"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Prise en charge de Visual Studio pour le mode d’opération approuvé de FIPS 140-2

Depuis la [version 16,4](/visualstudio/releases/2019/release-notes-v16.4/), Visual Studio 2019 prend en charge la publication normes FIPS (Federal Information Processing Standard) (FIPS) 140-2 mode d’opération approuvé pour Windows, Azure et .net. Et, avec la [version 16,5](/visualstudio/releases/2019/release-notes-archive-v16.5), Visual Studio prend désormais en charge le mode d’opération approuvé FIPS 140-2 quand vous développez des [applications C++ qui ciblent un système Linux distant](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Pour configurer le mode d’opération approuvé FIPS 140-2 pour Visual Studio, [installez .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) , puis activez le paramètre stratégie de groupe, **chiffrement système : utilisez des algorithmes compatibles FIPS pour le chiffrement, le hachage et la signature**.

Pour plus d’informations sur le mode d’opération approuvé FIPS 140-2 et sur la façon de l’activer, consultez [validation fips 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Les outils que vous utilisez pour développer des applications pour des plateformes non-Microsoft comme iOS ou Android peuvent ne pas utiliser des algorithmes conformes aux normes FIPS. Les logiciels tiers inclus dans Visual Studio ou les extensions que vous installez ne peuvent pas non plus utiliser des algorithmes conformes aux normes FIPS. De plus, le développement pour les solutions [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) ne prend pas en charge le mode de fonctionnement approuvé FIPS 140-2.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le mode de fonctionnement approuvé de FIPS 140-2 pour Visual Studio et pour d’autres produits et services Microsoft, consultez les liens suivants :

- [Visual Studio : configurer le développement Linux à distance sécurisé conforme aux normes FIPS avec C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows : chiffrement du système et utilisation d’algorithmes conformes aux normes FIPS pour le chiffrement, le hachage et la signature](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core : conformité FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Voir aussi

[Sécuriser les applications](securing-applications.md)