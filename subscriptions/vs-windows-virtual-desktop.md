---
title: Avantage des bureaux virtuels Microsoft Windows dans les abonnements Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Découvrez comment vous pouvez tirer parti du bureau virtuel Microsoft Windows via votre abonnement Visual Studio
ms.openlocfilehash: b84527f7bdaf3e9218585bd52af0743ef23a5637
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183585"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Accéder au bureau virtuel Windows dans les abonnements 
Les abonnés Visual Studio peuvent désormais utiliser leur crédit Azure dev/test pour les services de bureau virtuel Microsoft Windows.  
Windows Virtual Desktop est un service de virtualisation d’applications et de postes de travail complet qui s’exécute dans le Cloud. Il s’agit de la seule infrastructure VDI (Virtual Desktop Infrastructure) qui offre une gestion simplifiée, plusieurs sessions Windows 10, des optimisations pour Office 365 ProPlus et la prise en charge des environnements Services Bureau à distance (RDS). Déployez et mettez à l’échelle vos applications et postes de travail Windows sur Azure en quelques minutes et bénéficiez de fonctionnalités de sécurité et de conformité intégrées.
Voici ce que vous pouvez faire quand vous exécutez Windows Virtual Desktop sur Azure :
- Configurer un déploiement Windows 10 multisession qui délivre une version complète de Windows 10 avec extensibilité
- Virtualiser Office 365 ProPlus et l’optimiser pour une exécution dans des scénarios virtuels multiutilisateurs
- Fournir des bureaux virtuels Windows 7 avec Mises à jour de sécurité étendues gratuites
- Tirer parti de vos applications et bureaux Windows Server et Services Bureau à distance existants sur n’importe quel ordinateur
- Virtualiser des bureaux et des applications
- Gérez les applications et les ordinateurs de bureau Windows 10, Windows Server et Windows 7 avec une expérience de gestion unifiée pour plus d’informations sur ce que vous pouvez faire avec le bureau virtuel Windows, regardez la [vidéo d’introduction](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Utiliser le bureau virtuel Windows avec Azure 
Les abonnés Visual Studio disposent désormais de plusieurs façons d’utiliser les abonnements Azure pour payer les services de bureau virtuel Windows :
- [Crédits individuels Azure DevTest](vs-azure.md).  Les abonnés qui reçoivent des crédits Azure DevTest individuels dans le cadre de leur abonnement peuvent utiliser ces crédits pour payer les services de bureau virtuel Windows.  Le montant du crédit mensuel dépend du niveau d’abonnement.
- [Abonnements Azure DevTest avec paiement à l’accès](vs-azure-payg.md).  Vous pouvez créer des abonnements Azure et associer un mode de paiement pour avoir un moyen transparent de payer l’utilisation de votre bureau virtuel Windows. 
- [Offre Azure accord entreprise DevTest](azure-ea-devtest.md).  Grâce à cette offre, les abonnés disposant d’un contrat entreprise peuvent payer pour le bureau virtuel Windows avec Azure à prix réduit. 

## <a name="requirements"></a>Configuration requise
Le bureau virtuel Windows requiert une Azure Active Directory (Azure AD) à laquelle les machines virtuelles seront jointes.  Les utilisateurs doivent être membres de ce Azure AD.  Il existe deux options pour implémenter l’Azure AD :
- Services d’annuaire Azure AD.  Pour la plupart des utilisateurs, il s’agit de l’option la plus simple à implémenter.
- Une machine virtuelle exécutant une promotion de contrôleur de domaine.  Cette option nécessite plus de travail pour la configuration, mais offre aux utilisateurs un coût d’exploitation inférieur.
Pour obtenir la liste complète des conditions préalables à l’utilisation du bureau virtuel Windows, consultez la [page vue d’ensemble](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)du bureau virtuel Windows. 

## <a name="get-started"></a>Prendre en main 
Une fois que toutes les conditions préalables sont en place, vous pouvez effectuer plusieurs actions pour mettre en place votre implémentation.  Consultez ces didacticiels pour commencer :
- [Créer un locataire Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- [Créer un pool hôte](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) à l’aide de l’portail Azure
- [Gérer les groupes d’applications](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) pour les bureaux virtuels Windows

## <a name="eligibility"></a>Éligibilité
| Niveau de l’abonnement                                                 |     Canaux                                            | Avantage                                                          | Renouvelable ?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | Licences en volume, Azure, Détail, | Disponible|  Oui          |
| Visual Studio Enterprise avec GitHub Enterprise  | LV | Disponible|  Oui          |
| Visual Studio Professional (Standard) | Licences en volume, Azure, Détail                                       | Disponible                                                             |  Oui             |
| Visual Studio Professional avec GitHub Enterprise | LV                                       | Disponible                                        |  Oui           |
| Visual Studio Test Professional (Standard)                         | Licences en volume, Détail                                              | Disponible|  Oui          |
| Plateformes MSDN (Standard)                                          | Licences en volume, Détail                                              | Disponible                                         |  Oui          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Non disponible  | N/A |
| Visual Studio Enterprise, Visual Studio Professional (cloud mensuel) | Azure | Non disponible | N/A |

<sup>1</sup>  *comprend : la revente interdite (NFR), FTE, MVP (Most Valuable Professional), les services Bureau à distance, les Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, imagine*

> [!NOTE]
> Microsoft ne propose plus d’abonnements annuels Visual Studio Professional et Visual Studio Enterprise dans les abonnements cloud. L’expérience des clients n’en sera pas altérée ; il leur sera par ailleurs toujours possible de renouveler, d’augmenter, de diminuer ou d’annuler leur abonnement. Les nouveaux clients sont encouragés à accéder à [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) pour explorer les différentes options d’achat de Visual Studio.

Vous n’êtes pas sûr de l’abonnement que vous utilisez ?  Connectez-vous à [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) pour afficher tous les abonnements attribués à votre adresse de messagerie. Si vous ne retrouvez pas tous vos abonnements, certains ont peut-être été attribués à une autre adresse e-mail.  Dans ce cas, vous devez vous connecter via l’adresse e-mail correspondante pour afficher ces abonnements.

## <a name="see-also"></a>Voir aussi
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Étapes suivantes
-   Si vous avez besoin d’acheter des abonnements Visual Studio, consultez :
     - [Tarification des achats au détail](https://visualstudio.microsoft.com/vs/pricing/) via le Microsoft Store
     - [Programmes de licence en volume](https://www.microsoft.com/licensing/default)
-   En savoir plus sur le [bureau virtuel Windows](https://docs.microsoft.com/azure/virtual-desktop/overview) 
