---
title: Achat d’abonnements cloud Visual Studio pour les fournisseurs de solutions Cloud
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: d2ab13ed-ef79-4ef0-8736-eccd04bc6020
ms.date: 03/18/2021
ms.topic: conceptual
description: Informations destinées aux fournisseurs de solutions cloud concernant l’achat et la gestion d’abonnements cloud Visual Studio pour vos clients.
ms.openlocfilehash: 09c905d113920a0bb55aed8851d3fb62c92a39bf
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042849"
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Acheter et gérer des abonnements cloud Visual Studio pour vos clients
Les partenaires du programme [Fournisseur de solutions Cloud](https://partner.microsoft.com/cloud-solution-provider) peuvent acheter des abonnements cloud Visual Studio Enterprise et Visual Studio Professional pour leurs clients.

[Comparer les options d’abonnement cloud](https://visualstudio.microsoft.com/vs/pricing)

> [!NOTE]
> Microsoft ne propose plus d’abonnements annuels Visual Studio Professional et Visual Studio Enterprise dans les abonnements cloud. L’expérience des clients n’en sera pas altérée ; il leur sera par ailleurs toujours possible de renouveler, d’augmenter, de diminuer ou d’annuler leur abonnement. Les nouveaux clients sont encouragés à accéder à [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) pour explorer les différentes options d’achat de Visual Studio.

## <a name="prerequisites"></a>Prérequis
Vous devez tout d’abord configurer votre locataire de clients dans l’Espace partenaires et créer un abonnement Azure pour ce locataire.

[En savoir plus](/azure/devops/organizations/billing/csp/set-up-csp-customer)

## <a name="who-can-buy-visual-studio-subscriptions"></a>Qui peut acheter des abonnements Visual Studio ?
Toute personne ayant un [accès Propriétaire ou Contributeur](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fvsts%2Forganizations%2Fbilling%2Fadd-backup-billing-managers%3Fview%3Dvsts%2520%2520sa&data=02%7C01%7C%7Cb9e717e8abff47b0cd7e08d618edd860%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636723807145220358&sdata=aIaamEXHhx94KCYVY%2FFibqFzNBEqKPntpql867xAMgU%3D&reserved=0) à l’abonnement Azure peut acheter des abonnements Visual Studio.

## <a name="how-to-buy"></a>Comment acheter

1. Connectez-vous à l’[Espace partenaires Microsoft](https://partnercenter.microsoft.com).
0. Choisissez **Clients** et sélectionnez un client pour lequel effectuer un achat.
0. Choisissez **Gestion des services**.
0. Choisissez **Visual Studio Marketplace**.
0. Vérifiez que le nom de votre client figure en haut à droite.
0. Choisissez **abonnements**.
0. Choisissez Enterprise ou Professional pour Visual Studio.
0. Choisissez **Acheter**.
0. Choisissez l’abonnement Azure à facturer pour cet achat.
0. Entrez le nombre d’utilisateurs dont votre client a besoin.
0. Vérifiez la commande et **confirmez-la**.

>[!NOTE]
> Vous devez suivre ces étapes chaque fois que vous achetez des abonnements Visual Studio en tant que fournisseur de solutions Cloud. À l’heure actuelle, il n’existe aucune API pour automatiser l’achat.

Après avoir confirmé l’achat, vous pouvez choisir **Gérer** pour affecter des abonnements aux utilisateurs finaux de votre client.  Vous pouvez également accéder au portail d’administration des abonnements à partir de l’espace partenaires en choisissant **gestion des services**.  À partir de là, consultez les étapes ou la vidéo ci-dessous.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Comment gérer les abonnements cloud Visual Studio pour votre client

1. Connectez-vous à l’[Espace partenaires Microsoft](https://partnercenter.microsoft.com).
0. Choisissez **Clients** et le nom du client.
0. Choisissez **Gestion des services**.
0. Choisissez **Gérer les abonnements Visual Studio**.

Si vous avez plusieurs abonnements Azure pour ce client, utilisez le menu déroulant pour choisir celui par le biais duquel vous avez effectué les achats.  Le **Récapitulatif des licences** indique combien d’abonnements ont été affectés et combien sont disponibles pour chaque option d’abonnement cloud Visual Studio.  Le récapitulatif vous permet également d’acheter des abonnements supplémentaires ou de réduire le nombre d’abonnements.

Choisissez **Ajouter** pour affecter un abonnement à un nouvel utilisateur.  La quantité affichée est mise à jour, et l’utilisateur final reçoit une notification par e-mail. Il peut ensuite se connecter avec l’adresse e-mail que vous avez fournie pour activer son abonnement Visual Studio dans le [portail des abonnés Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

Pour réaffecter un abonnement Visual Studio à un autre utilisateur, vous pouvez supprimer l’abonné actuel et ajouter un nouvel abonné.

Si un abonné n’a pas activé son abonnement Visual Studio, c’est peut-être parce qu’il n’a pas vu l’e-mail d’invitation.  Vous pouvez nous demander de renvoyer l’invitation d’activation à l’utilisateur à partir du portail d’administration de Visual Studio.

## <a name="view-visual-studio-pricing-for-csp-partners"></a>Voir les tarifs de Visual Studio pour les partenaires CSP
Pour voir les tarifs de Visual Studio pour les partenaires CSP, connectez-vous à l’[Espace partenaires](https://partnercenter.microsoft.com).  Choisissez **Tarification et offres** dans la navigation de gauche.  Choisissez le fichier de tarifs du mois en cours sous **Services basés sur l’utilisation** en haut à droite. Une fois la feuille de calcul Excel téléchargée, accédez à la feuille **Azure Price List** et filtrez la colonne **Meter Category** sur **Visual Studio**.

Voici comment interpréter les différents éléments de cette feuille de calcul :

| Catégorie du compteur    |   Nom                 |  Unités                                |           De quoi s’agit-il ?                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Entreprise             |  Abonnement                         | Abonnement mensuel à Visual Studio Enterprise   |
| Visual Studio     | Professional           |  Abonnement                         | Abonnement mensuel à Visual Studio Professional |

Nous offrons une remise de 5 % sur la sixième unité que vous achetez (pour un client donné) chaque mois pour chaque abonnement Visual Studio. C’est pourquoi il y a deux lignes pour chaque option d’abonnement. Une ligne affiche une « Valeur minimale » de 0, ce que vous devez interpréter comme prix de base pour les unités de 1 à 5. L’autre ligne affiche une « Valeur minimale » de 5. Il s’agit de la remise de 5 % qui s’applique aux unités 6 et plus.

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Q : Comment les frais d’abonnement cloud **mensuels** sont-ils traités ?
R : Lors du premier achat, nous facturons une quantité au prorata pour couvrir les jours restants du mois en cours. Par exemple, si un achat de 10 abonnements cloud mensuels Visual Studio Professional a été effectué le 15 avril, nous facturons cinq unités, car il reste 15 jours sur les 30 du mois d’avril (soit 50 %), et nous facturons donc les unités au prorata de 50 %. Le premier mai et chaque mois suivant jusqu’à ce que vous annuliez, les dix unités seront facturées.

Quand vous augmentez la quantité payée ultérieurement, nous calculons également au prorata les unités accrues afin de couvrir les jours restants dans le mois en cours. Ainsi, si vous avez acheté un abonnement cloud Visual Studio Professional mensuel en plus le 10 mai, nous facturerons environ 0,677 unité (21 jours restants sur les 31 jours du mois de mai).

### <a name="q-how-do-cancellations-work"></a>Q : Que se passe-t-il en cas d’annulation ?
R : Quand vous annulez un abonnement cloud Visual Studio, vous annulez le renouvellement automatique. L’abonnement continue jusqu’à sa date de renouvellement normale, puis il arrive simplement à expiration. À l’expiration, l’abonné Visual Studio ne peut plus utiliser Visual Studio ni d’autres avantages de l’abonnement.

Avec les abonnements cloud mensuels, les annulations prennent effet le premier jour du mois suivant. Si vous annulez uniquement certains des abonnements cloud mensuels de vos clients, veillez à supprimer les utilisateurs le premier jour du mois suivant pour vous assurer que des abonnements actifs sont toujours affectés aux personnes appropriées.

Pour les abonnements cloud annuels, les annulations prennent effet le premier jour du mois qui suit les 12 mois suivant l’achat initial, ou les 12 mois suivant la dernière facturation de renouvellement annuel. Par exemple, si vous avez acheté un abonnement cloud annuel Visual Studio Enterprise le 3 janvier 2018, il reste actif jusqu’au 1er février 2019, date de son renouvellement automatique pour une autre année. Si vous annulez à tout moment entre cette date et le 1er février 2020, l’abonnement expire le 1er février 2020. Aucune remise n’est accordée en cas d’annulation en cours d’année d’abonnement avec les abonnements cloud annuels.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Q : Quels sont les types de remise sur la quantité disponibles pour les abonnements Visual Studio ?
R : Vous bénéficiez d’une remise de 5 % à partir du sixième abonnement *pour chaque type* d’abonnement :
- Visual Studio Professional mensuel
- Visual Studio Enterprise mensuel

Par exemple, si vous achetez 6 abonnements mensuels Visual Studio Professional et 5 abonnements mensuels Visual Studio Enterprise, vous allez payer le prix normal pour cinq abonnements Professional, vous allez bénéficier d’une remise de 5 % sur le 6e abonnement Professional, et vous allez payer le prix normal sur les cinq abonnements Enterprise.

En outre, la remise s’applique uniquement aux frais durant une période de facturation mensuelle donnée. Ainsi, si vous achetez 5 abonnements annuels Visual Studio Professional en un mois, puis 5 de plus le mois suivant, vous allez payer le prix normal pour les dix abonnements.

Ces remises sont reflétées dans les données tarifaires mentionnées dans l’[Espace partenaires](https://partnercenter.microsoft.com).

### <a name="q-are-there-renewal-discounts"></a>Q : Y a-t-il des remises pour le renouvellement ?
R : Non, les prix pour les abonnements Visual Studio sont fixes. Le même prix est proposé pour les nouveaux abonnements et pour les abonnements existants.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>Q : Existe-t-il des tarifs de développement/test Azure pour les fournisseurs de solutions Cloud ?
A : Pas pour l'instant. Vos clients peuvent profiter des [tarifs de développement/test Azure](https://azure.microsoft.com/pricing/dev-test/), mais nous ne proposons rien de spécifique pour les fournisseurs de solutions Cloud.

## <a name="resources"></a>Ressources
- Pour obtenir de l’aide sur les ventes, les abonnements, les comptes et la facturation des abonnements Visual Studio, consultez [prise en charge des abonnements](https://aka.ms/vssubscriberhelp)Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
Consultez le [Forum aux](vscloud-billing-faq.yml) questions sur la facturation dans le Cloud pour obtenir des réponses aux questions de facturation courantes.