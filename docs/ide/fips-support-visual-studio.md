---
title: Support Visual Studio pour le mode de fonctionnement approuvé fiPS 140-2
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386448"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Support Visual Studio pour le mode de fonctionnement approuvé fiPS 140-2

À partir [de la version 16.4](/visualstudio/releases/2019/release-notes-v16.4/), Visual Studio 2019 prend en charge le mode de fonctionnement approuvé par la Norme fédérale de traitement de l’information (FIPS) 140-2 pour Windows, Azure et .NET. Et, avec [la version 16.5](/visualstudio/releases/2019/release-notes-v16.5/), Visual Studio prend désormais en charge le mode de fonctionnement approuvé FIPS 140-2 lorsque vous [développez des applications CMD qui ciblent un système Linux distant.](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)

Pour configurer le mode de fonctionnement approuvé FIPS 140-2 pour Visual Studio, [installez .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) et activez ensuite le paramètre de la politique de groupe, **la cryptographie du système : utilisez des algorithmes conformes au FIPS pour le cryptage, le hachage et la signature.**

Pour plus d’informations sur le mode de fonctionnement approuvé par fiPS 140-2 et sur la façon de l’activer, voir [FIPS 140-2 Validation](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Les outils que vous utilisez pour développer des applications pour des plates-formes non Microsoft comme iOS ou Android peuvent ne pas utiliser d’algorithmes conformes à la FIPS. Les logiciels tiers inclus avec Visual Studio ou les extensions que vous installez peuvent également ne pas utiliser d’algorithmes conformes au FIPS. De plus, le développement des solutions [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) ne prend pas en charge le mode de fonctionnement approuvé par fiPS 140-2.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le mode d’exploitation approuvé par fiPS 140-2 pour Visual Studio et pour d’autres produits et services Microsoft, consultez les liens suivants :

- [Visual Studio : Configurez le développement Linux sécurisé conforme à LA FIPS avec C](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows : cryptographie système et utilisation d’algorithmes conformes au FIPS pour le chiffrement, le hachage et la signature](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: FiPS compliance](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Voir aussi

[Sécuriser les applications](securing-applications.md)