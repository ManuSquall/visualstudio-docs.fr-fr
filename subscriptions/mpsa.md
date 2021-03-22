---
title: Abonnements Visual Studio dans MPSA | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/21/2021
ms.topic: conceptual
description: En savoir plus sur la gestion des abonnements Visual Studio dans un contrat Microsoft Products and services (MPSA)
ms.openlocfilehash: 63124e8853184fde04db7bc202e5acea3cfbe89f
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776530"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Abonnements Visual Studio dans un programme MPSA (Microsoft Products and Services Agreement)
Si vous avez acheté des abonnements Visual Studio via le programme MPSA, vous devez connaître quelques éléments avant de pouvoir devenir administrateur des abonnements Visual Studio et affecter des abonnements à vos utilisateurs. Si vous avez déjà été configuré en tant qu’administrateur, vous pouvez accéder directement au [portail d’administration](https://manage.visualstudio.com/)des abonnements Visual Studio.

Les clients MPSA gèrent les ressources achetées par le biais de MPSA dans un portail appelé [Business Center](https://businessaccount.microsoft.com/Customer), qui prend en charge des fonctionnalités similaires à celles du centre de gestion des licences en volume (VLSC). Cela inclut l’affichage du récapitulatif des licences, des commandes, des téléchargements, des clés, des utilisateurs, etc. Toutefois, les abonnements Visual Studio dans MPSA se comportent de la même façon que les services Cloud. Business Center utilise également des comptes professionnels pour la connexion à la place des comptes Microsoft. Si votre organisation utilise des services cloud comme Office 365 ou Azure Active Directory, et que votre e-mail fait partie de l’un de ces deux services, il s’agit déjà d’un compte professionnel. Ceci vous permet de vous inscrire auprès de Business Center avec votre mot de passe existant. Si votre organisation n’utilise pas de services cloud et que votre e-mail n’est pas du tout un compte professionnel, vous pouvez l’utiliser pour vous inscrire auprès de Business Center.

En outre, le [portail d’administration](https://manage.visualstudio.com/) des abonnements Visual Studio vous permet d’attribuer des abonnements une fois que vous devenez administrateur des abonnements Visual Studio. Dans MPSA, les abonnements Visual Studio doivent être approvisionnés dans leur portail de gestion respectif, qui est le portail d’administration des abonnements Visual Studio. Pour ce faire, vous devez associer votre compte d’achats à un locataire (autrement dit, contoso.onmicrosoft.com).

Notez qu’il existe deux types de locataires gérés par les locataires et les locataires non gérés. Un locataire géré fait référence à un locataire qui est déjà géré par des administrateurs au sein de l’organisation.

Un locataire non géré est un locataire sans aucun administrateur attribué et n’est pas utilisable pour des services en ligne tels qu’Office 365. Des locataires non gérés sont également créés lors de l’inscription auprès de Business Center avec un e-mail qui n’est pas un compte professionnel. Si vous avez été invité à créer un mot de passe lors de l’inscription auprès de Business Center, cela signifie que votre e-mail n’était pas un compte professionnel et qu’il a créé un locataire non géré.

Voici quelques-unes des exigences/étapes nécessaires pour devenir administrateur des abonnements Visual Studio avant de terminer l’Association du locataire.

## <a name="pre-tenant-association-managed-tenant"></a>Association prélocataire (locataire managé)
- Vous devez être un utilisateur inscrit auprès du portail Business Center.
- Vous devez être administrateur d’utilisateurs (au minimum) ou administrateur général au sein du locataire dont vous faites partie. (Cela s’applique si votre entreprise utilise déjà des services cloud). L’un ou l’autre rôle est nécessaire pour être un administrateur des abonnements Visual Studio.
- Vous devez être administrateur général dans le locataire dont vous faites partie pour être en mesure d’associer votre compte d’achats à un locataire.
- Vous devez être administrateur de compte ou gestionnaire de comptes dans Business Center.
- Le champ « Pays ou région » au sein de votre profil utilisateur (et tout autre utilisateur) dans [Azure](https://portal.azure.com/) doit être rempli de façon appropriée selon votre région (autrement dit, États-Unis, CA, etc.). 

> [!NOTE]
> Les utilisateurs auxquels vous souhaitez faire des administrateurs d’abonnements Visual Studio ne sont pas tenus d’être des utilisateurs dans le Business Center, car ils doivent uniquement répondre aux critères 2 et 5.

Une fois que vous avez rempli les critères ci-dessus, vous pouvez associer votre compte d’achat à votre locataire en suivant les étapes ci-dessous.
1. Connectez-vous à [Business Center](https://businessaccount.microsoft.com/Customer).
2. Cliquez sur l’onglet **Compte** et sélectionnez **Associate Domains** (Associer les domaines).
3. Sélectionnez votre **compte d’achats** (si vous en avez plusieurs).
4. Sélectionnez votre **locataire** (par exemple : contoso.onmicrosoft.com).
5. Cliquez sur **Associate Domain** (Associer le domaine).

En cas d’association, tous les utilisateurs répondant aux critères sont généralement configurés en tant qu’administrateurs des abonnements Visual Studio en quelques minutes. Toutefois, dans certains cas, cela peut prendre jusqu’à 24 heures. Une fois votre locataire approvisionné, vous serez en mesure d’accéder au portail d’administration des abonnements Visual Studio. Si cette opération prend plus de 24 heures, contactez le [support technique de Business Center](https://businessaccount.microsoft.com/Customer/ContactUs).

> [!NOTE]
> Si de nouveaux utilisateurs répondent aux critères des étapes 2 et 5 (après l’association), vous devez contacter le support MPSA. La prise en charge de MPSA fournit une assistance pour approvisionner les nouveaux administrateurs d’abonnements Visual Studio.

## <a name="tenant-association-unmanaged"></a>Association de locataire (non managé)
Si vous vous êtes inscrit auprès de Business Center avec un e-mail qui n’était pas un compte professionnel (non inscrit auprès d’Azure Active Directory « Azure AD »), comme expliqué ci-dessus, l’association du locataire est légèrement différente. Vous devez effectuer une opération appelée « prise de contrôle de domaine ». Pendant ce processus, vous deviendrez administrateur général pour transformer votre locataire non managé en locataire managé.

Pour obtenir une explication plus détaillée de ce processus, vous pouvez utiliser les [guides de démarrage rapide](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Téléchargez le guide nommé *« configuration et utilisation de vos services en ligne »* qui vous guidera tout au long du processus de prise de contrôle d’un domaine. Une fois cette opération terminée, votre compte d’achat est également associé à votre locataire.

> [!NOTE]
> Lorsque vous terminez le processus de prise de contrôle de domaine, vous devez respecter les critères des cinq étapes décrites dans la section relative à l’Association de pré-locataires (gérée). Une fois les critères remplis, il est nécessaire de contacter le support MPSA pour approvisionner d’autres administrateurs d’abonnements Visual Studio.

## <a name="support-resources"></a>Ressources de support
- Pour obtenir de l’aide sur l’administration des abonnements Visual Studio, contactez le [support des abonnements Visual Studio](https://aka.ms/vsadminhelp).

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Affecter des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Supprimer des abonnements](delete-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)