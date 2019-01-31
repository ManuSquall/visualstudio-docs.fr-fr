---
title: Exemption de la Protection des informations Windows
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65a8da50cb14850762a1bd29c8a554f9f4556ca4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968713"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Configurer Visual Studio en tant qu’application exempte de la Protection des informations Windows

La [Protection des informations Windows](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP) vous aide à prévenir la fuite de données d’entreprise par le biais d’applications telles que la messagerie, les médias sociaux et le cloud public, qui sont en dehors du contrôle de l’entreprise. WIP contribue à protéger vos systèmes contre les fuites de données accidentelles sur les appareils d’entreprise et les appareils personnels, sans nécessiter de modifications de votre environnement ou d’autres applications.

Les applications *compatibles* avec WIP sont censées empêcher les données d’entreprise d’atteindre des emplacements réseau non protégés, et d’éviter le chiffrement des données personnelles. Visual Studio n’étant pas une application compatible, il ne fonctionne pas dans les environnements WIP, sauf si vous l’exemptez. Suivez les étapes décrites dans cet article pour permettre à Visual Studio de fonctionner sur un ordinateur prenant en charge WIP.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Configurer Visual Studio en tant qu’application exempte de la Protection des informations Windows

Vous pouvez exempter Visual Studio des restrictions WIP tout en l’autorisant à utiliser des données d’entreprise. Les applications exemptes de la Protection des informations Windows peuvent se connecter aux ressources cloud d’entreprise à l’aide d’une adresse IP ou d’un nom d’hôte. Aucun chiffrement n’est appliqué et l’application peut accéder aux fichiers locaux.

Pour exempter Visual Studio de la Protection des informations Windows, suivez les [étapes pour exempter une application de bureau](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Créer un fichier de stratégie AppLocker exempt de la Protection des informations Windows

Étant donné que Visual Studio inclut plusieurs fichiers binaires, vous devez [créer un fichier de stratégie AppLocker exempt de la Protection des informations Windows](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker vous permet de générer automatiquement des règles pour tous les fichiers d’un dossier.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Ajouter AppCompat à la stratégie de ressources cloud d’entreprise

Pour spécifier où Visual Studio peut accéder aux données d’entreprise sur votre réseau, suivez ces [étapes pour définir où vos applications protégées peuvent trouver et envoyer des données d’entreprise](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Pour que Windows cesse de bloquer les connexions aux ressources cloud par le biais d’une adresse IP, veillez à ajouter la chaîne /\*AppCompat\*/ au paramètre.

## <a name="see-also"></a>Voir aussi

- [Comportement des applications avec WIP](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)