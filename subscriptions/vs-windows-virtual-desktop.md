---
title: Microsoft Windows Virtual Desktop avantage dans les abonnements Visual Studio (fr) Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Découvrez comment vous pouvez profiter de Microsoft Windows Virtual Desktop via votre abonnement Visual Studio
ms.openlocfilehash: 87911b1b7b6eb63eb85b64515d5d24755e4656e6
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649731"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Accédez à Windows Virtual Desktop dans les abonnements 
Les abonnés visual Studio sont désormais en mesure d’utiliser leurs crédits individuels Azure dev/test pour les services Microsoft Windows Virtual Desktop.  
Windows Virtual Desktop est un service complet de virtualisation de bureau et d’applications qui s’exécute dans le cloud. C’est la seule infrastructure de bureau virtuelle (VDI) qui offre une gestion simplifiée, Windows 10 multi-session, des optimisations pour Office 365 ProPlus et un support pour les environnements de services de bureau à distance (RDS). Déployez et dimensionssez vos ordinateurs de bureau et applications Windows sur Azure en quelques minutes et obtenez des fonctionnalités de sécurité et de conformité intégrées.
Voici ce que vous pouvez faire quand vous exécutez Windows Virtual Desktop sur Azure :
- Configurer un déploiement Windows 10 multisession qui délivre une version complète de Windows 10 avec extensibilité
- Virtualiser Office 365 ProPlus et l’optimiser pour une exécution dans des scénarios virtuels multiutilisateurs
- Fournir des bureaux virtuels Windows 7 avec Mises à jour de sécurité étendues gratuites
- Tirer parti de vos applications et bureaux Windows Server et Services Bureau à distance existants sur n’importe quel ordinateur
- Virtualiser des bureaux et des applications
- Gérez Windows 10, Windows Server, et Windows 7 ordinateurs de bureau et applications avec une expérience de gestion unifiée Pour plus d’informations sur ce que vous pouvez faire avec Windows Virtual Desktop, regarder la [vidéo d’introduction](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Utilisez Windows Virtual Desktop avec Azure 
Les abonnés visual Studio ont maintenant plusieurs façons d’utiliser les abonnements Azure pour payer les services Windows Virtual Desktop :
- [Azure DevTest crédits individuels](vs-azure.md).  Les abonnés qui reçoivent des crédits individuels Azure DevTest dans le cadre de leurs abonnements peuvent utiliser ces crédits pour payer les services Windows Virtual Desktop.  Le montant du crédit mensuel dépend du niveau d’abonnement.
- [Azure DevTest Abonnements Pay-as-you-Go](vs-azure-payg.md).  Vous pouvez créer des abonnements Azure et joindre un instrument de paiement pour avoir un moyen homogène de payer votre utilisation de Bureau Virtuel Windows. 
- [Azure Enterprise Agreement DevTest offre](azure-ea-devtest.md).  Avec cette offre, les abonnés avec des accords d’entreprise peuvent payer pour Windows Virtual Desktop avec Azure à des prix réduits. 

## <a name="requirements"></a>Spécifications
Windows Virtual Desktop nécessite un répertoire Azure Active (Azure AD) auquel les machines virtuelles seront jointes.  Les utilisateurs doivent être membres de cette AD Azure.  Il existe deux options pour mettre en œuvre l’Azure AD :
- Azure AD Directory Services.  Pour la plupart des utilisateurs, c’est l’option la plus facile à mettre en œuvre.
- Une machine virtuelle exécutant une promo de contrôleur de domaine.  Cette option nécessite plus de travail à mettre en place, mais offre à la plupart des utilisateurs un coût d’exploitation inférieur.
Pour voir une liste complète des conditions préalables à l’utilisation de Windows Virtual Desktop, veuillez visiter la [page d’aperçu](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)de Windows Virtual Desktop . 

## <a name="get-started"></a>Bien démarrer 
Lorsque toutes vos conditions préalables sont en place, vous voudrez effectuer plusieurs actions pour mettre en place votre mise en œuvre.  Consultez ces tutoriels pour commencer:
- [Créer un locataire Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- [Créer une piscine d’accueil](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) à l’aide du portail Azure
- [Gérer les groupes d’applications](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) pour Windows Virtual Desktop

## <a name="eligibility"></a>Éligibilité
| Niveau de l’abonnement                                                 |     Canaux                                            | Avantage                                                          | Renouvelable ?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | Licences en volume, Azure, Détail, | Disponible|  Oui          |
| Visual Studio Enterprise avec GitHub Enterprise  | Vl | Disponible|  Oui          |
| Visual Studio Professional (Standard) | Licences en volume, Azure, Détail                                       | Disponible                                                             |  Oui             |
| Visual Studio Professional avec GitHub Enterprise | Vl                                       | Disponible                                        |  Oui           |
| Visual Studio Test Professional (Standard)                         | Licences en volume, Détail                                              | Disponible|  Oui          |
| Plateformes MSDN (Standard)                                          | Licences en volume, Détail                                              | Disponible                                         |  Oui          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Non disponible  | N/A |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensuel) | Azure | Non disponible | N/A |

<sup>1</sup>  *Comprend: Pas pour la revente (NFR), FTE, Most Valuable Professional (MVP), Directeur régional (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> Microsoft ne propose plus d’abonnements annuels Visual Studio Professional et Visual Studio Enterprise dans les abonnements cloud. L’expérience des clients n’en sera pas altérée ; il leur sera par ailleurs toujours possible de renouveler, d’augmenter, de diminuer ou d’annuler leur abonnement. Les nouveaux clients sont [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) encouragés à aller explorer différentes options pour acheter Visual Studio.

Vous n’êtes pas sûr de l’abonnement que vous utilisez ?  Connectez-vous [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) pour voir tous les abonnements attribués à votre adresse e-mail. Si vous ne retrouvez pas tous vos abonnements, certains ont peut-être été attribués à une autre adresse e-mail.  Dans ce cas, vous devez vous connecter via l’adresse e-mail correspondante pour afficher ces abonnements.

## <a name="see-also"></a>Voir aussi
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation De bureau virtuel Windows](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Étapes suivantes
-   Si vous avez besoin d’acheter des abonnements Visual Studio, consultez :
     - [Prix des achats au détail](https://visualstudio.microsoft.com/vs/pricing/) via le Microsoft Store
     - [Programmes de licences en volume](https://www.microsoft.com/licensing/default)
-   En savoir plus sur [Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview) 
