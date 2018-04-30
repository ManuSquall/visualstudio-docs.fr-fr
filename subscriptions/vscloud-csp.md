---
title: Achat d’abonnements cloud Visual Studio pour les fournisseurs de solutions Cloud
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/15/2018
ms.topic: Get-Started-Article
description: Informations destinées aux fournisseurs de solutions cloud concernant l’achat et la gestion d’abonnements cloud Visual Studio pour vos clients.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 7cffe2f8e7351a243f581918e6d31a773d4808f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="buy-and-manage-visual-studio-cloud-subscriptions-for-your-customers"></a>Acheter et gérer des abonnements cloud Visual Studio pour vos clients

Les partenaires du programme [Fournisseur de solutions Cloud](https://partner.microsoft.com/en-US/cloud-solution-provider) peuvent acheter des abonnements cloud Visual Studio Enterprise et Visual Studio Professional pour leurs clients. 

[Comparer les options d’abonnement cloud](https://www.visualstudio.com/vs/pricing)

## <a name="prerequisites"></a>Prérequis
Vous devez tout d’abord configurer votre locataire de clients dans l’Espace partenaires et créer un abonnement Azure pour ce locataire. 
[En savoir plus](https://docs.microsoft.com/vsts/billing/csp/set-up-csp-customer)

## <a name="how-to-buy"></a>Comment acheter

<iframe src="//channel9.msdn.com/Shows/Visual-Studio-for-CSP-Partners/CSP-How-to-buy-Visual-Studio-Subscriptions/player" width="600" height="315" allowFullScreen="true" frameBorder="0"></iframe>

0. Connectez-vous à l’[Espace partenaires Microsoft](https://partnercenter.microsoft.com).
0. Choisissez **Clients** et sélectionnez un client pour lequel effectuer un achat.
0. Choisissez **Gestion des services**.
0. Choisissez **Visual Studio Marketplace**.
0. Vérifiez que le nom de votre client figure en haut à droite.
0. Choisissez **Abonnements**.
0. Choisissez Enterprise ou Professional, et choisissez mensuel ou annuel pour Visual Studio.
0. Choisissez **Acheter**.
0. Choisissez l’abonnement Azure à facturer pour cet achat.
0. Entrez le nombre d’utilisateurs dont votre client a besoin.
0. Vérifiez la commande et **confirmez-la**.

>[!NOTE]
> Vous devez suivre ces étapes chaque fois que vous achetez des abonnements Visual Studio en tant que fournisseur de solutions Cloud. À l’heure actuelle, il n’existe aucune API pour automatiser l’achat.

Après avoir confirmé l’achat, vous pouvez choisir **Gérer** pour affecter des abonnements aux utilisateurs finaux de votre client.  Vous pouvez également accéder au portail d’administration des abonnements à partir de l’Espace partenaires en choisissant **Gestion des services**.  À partir de là, consultez les étapes ou la vidéo ci-dessous.

## <a name="how-to-manage-visual-studio-cloud-subscriptions-for-your-customer"></a>Comment gérer les abonnements cloud Visual Studio pour votre client

<iframe src="//channel9.msdn.com/Shows/Visual-Studio-for-CSP-Partners/CSP-How-to-manage-Visual-Studio-Subscriptions/player" width="600" height="315" allowFullScreen="true" frameBorder="0"></iframe>

0. Connectez-vous à l’[Espace partenaires Microsoft](https://partnercenter.microsoft.com).
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
| Catégorie de compteur    |   Name                 |  Unités                                |           De quoi s’agit-il ?                          |
|-------------------|------------------------|---------------------------------------|-------------------------------------------------|
| Visual Studio     | Entreprise             |  Abonnement                         | Abonnement mensuel à Visual Studio Enterprise   |
| Visual Studio     | Enterprise (annuel)    |  Abonnements annuels                 | Abonnement annuel à Visual Studio Enterprise    |
| Visual Studio     | Professionnel           |  Abonnement                         | Abonnement mensuel à Visual Studio Professional |
| Visual Studio     | Professional (annuel)  |  Abonnements annuels                 | Abonnement annuel à Visual Studio Professional  |

Nous offrons une remise de 5 % sur la sixième unité que vous achetez (pour un client donné) chaque mois pour chaque abonnement Visual Studio. C’est pourquoi il y a deux lignes pour chaque option d’abonnement. Une ligne affiche une « Valeur minimale » de 0, ce que vous devez interpréter comme prix de base pour les unités de 1 à 5. L’autre ligne affiche une « Valeur minimale » de 5. Il s’agit de la remise de 5 % qui s’applique aux unités 6 et plus.


## <a name="frequently-asked-questions"></a>FAQ
### <a name="q-how-are-monthly-cloud-subscription-charges-processed"></a>Q : Comment les frais d’abonnement cloud **mensuels** sont-ils traités ?
R : Lors du premier achat, nous facturons une quantité au prorata pour couvrir les jours restants du mois en cours. Par exemple, si un achat de 10 abonnements cloud mensuels Visual Studio Professional a été effectué le 15 avril, nous facturons cinq unités, car il reste 15 jours sur les 30 du mois d’avril (soit 50 %), et nous facturons donc les unités au prorata de 50 %. Le premier mai et chaque mois suivant jusqu’à ce que vous annuliez, les dix unités seront facturées.

Quand vous augmentez la quantité payée ultérieurement, nous calculons également au prorata les unités accrues afin de couvrir les jours restants dans le mois en cours. Ainsi, si vous avez acheté un abonnement cloud Visual Studio Professional mensuel en plus le 10 mai, nous facturerons environ 0,677 unité (21 jours restants sur les 31 jours du mois de mai). 

### <a name="q-how-are-annual-cloud-subscription-charges-processed"></a>Q : Comment les frais d’abonnement cloud **annuels** sont-ils traités ?
R : Lors de chaque achat, nous facturons immédiatement la quantité totale achetée. Les frais ne sont pas répartis sur l’année, et il n’existe aucun prorata. Si vous achetez des abonnements cloud annuels à différents moments de l’année, vous devrez renouveler vos abonnements à des dates différentes. Nous ne faisons pas en sorte que tous les abonnements cloud annuels d’un client se terminent en même temps, comme cela est courant avec les achats Contrat de licence en volume Microsoft.

### <a name="q-how-do-cancelations-work"></a>Q : Que se passe-t-il en cas d’annulation ?
R : Quand vous annulez un abonnement cloud Visual Studio, vous annulez le renouvellement automatique. L’abonnement continue jusqu’à sa date de renouvellement normale, puis il arrive simplement à expiration. À l’expiration, l’abonné Visual Studio ne peut plus utiliser Visual Studio ni d’autres avantages de l’abonnement.

Avec les abonnements cloud mensuels, les annulations prennent effet le premier jour du mois suivant. Si vous annulez uniquement certains des abonnements cloud mensuels de vos clients, veillez à supprimer les utilisateurs le premier jour du mois suivant pour vous assurer que des abonnements actifs sont toujours affectés aux personnes appropriées.

Pour les abonnements cloud annuels, les annulations prennent effet le premier jour du mois suivant 12 mois à partir de l’achat initial, ou 12 mois à partir de la dernière facturation de renouvellement annuel. Par exemple, si vous avez acheté un abonnement cloud annuel Visual Studio Enterprise le 3 janvier 2018, il reste actif jusqu’au 1er février 2019, date de son renouvellement automatique pour une autre année. Si vous annulez à tout moment entre cette date et le 1er février 2020, l’abonnement expire le 1er février 2020. Aucune remise n’est accordée en cas d’annulation en cours d’année d’abonnement avec les abonnements cloud annuels.

### <a name="q-what-kind-of-volume-discounts-are-available-for-visual-studio-subscriptions"></a>Q : Quels sont les types de remise sur la quantité disponibles pour les abonnements Visual Studio ?

R : Vous bénéficiez d’une remise de 5 % à partir du sixième abonnement *pour chaque type* d’abonnement :

* Visual Studio Professional mensuel
* Visual Studio Professional annuel
* Visual Studio Enterprise mensuel
* Visual Studio Enterprise annuel

Par exemple, si vous achetez six abonnements mensuels Visual Studio Professional et cinq abonnements mensuels Visual Studio Enterprise, vous payez le prix normal pour cinq abonnements Professional, vous bénéficiez d’une remise de 5 % sur le sixième abonnement Professional, et vous payez le prix normal pour les cinq abonnements Enterprise.

En outre, la remise s’applique uniquement aux frais durant une période de facturation mensuelle donnée. Ainsi, si vous achetez cinq abonnements annuels Visual Studio Professional durant un mois, et que vous achetez ensuite cinq abonnements supplémentaires le mois suivant, vous payez le prix normal pour les dix abonnements.

Ces remises sont reflétées dans les données tarifaires mentionnées dans l’[Espace partenaires](https://partnercenter.microsoft.com). 

### <a name="q-are-there-renewal-discounts"></a>Q : Y a-t-il des remises pour le renouvellement ?

R : Non, les prix pour les abonnements Visual Studio sont fixes. Le même prix est proposé pour les nouveaux abonnements et pour les abonnements existants.

### <a name="q-are-there-azure-devtest-pricing-options-for-csps"></a>Q : Existe-t-il des tarifs de développement/test Azure pour les fournisseurs de solutions Cloud ?

R : Pas à l’heure actuelle. Vos clients peuvent profiter des [tarifs de développement/test Azure](http://aka.ms/azuredevtestpricing), mais nous ne proposons rien de spécifique pour les fournisseurs de solutions Cloud.