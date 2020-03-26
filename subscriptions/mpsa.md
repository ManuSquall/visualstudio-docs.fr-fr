---
title: Abonnements Visual Studio dans un programme MPSA (Microsoft Products and Services Agreement) | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/03/2020
ms.topic: conceptual
description: Abonnements Visual Studio dans un programme MPSA (Microsoft Products and Services Agreement)
ms.openlocfilehash: e59929404febda5a07ba13f7dc230ab89e09addf
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232205"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Abonnements Visual Studio dans un programme MPSA (Microsoft Products and Services Agreement)
Si vous avez acheté des abonnements Visual Studio via le programme MPSA, il existe quelques éléments à connaître avant de devenir administrateur des abonnements Visual Studio et d’attribuer des abonnements à vos utilisateurs. Si vous avez déjà été configuré comme administrateur, vous pouvez accéder directement au [portail d’administration](https://manage.visualstudio.com/) des abonnements Visual Studio.

Les clients MPSA gèrent désormais les ressources achetées via MPSA dans un nouveau portail appelé [Business Center](https://businessaccount.microsoft.com/Customer), qui prend en charge des fonctionnalités similaires à celles du Centre de gestion des licences en volume (VLSC). Il s’agit notamment de consulter votre résumé de licence, commandes, téléchargements, clés, utilisateurs, etc. Cependant, les abonnements Visual Studio dans MPSA se comportent un peu comme Cloud Services. Business Center utilise également des comptes professionnels pour la connexion à la place des comptes Microsoft. Si votre organisation utilise des services cloud comme Office 365 ou Azure Active Directory, et que votre e-mail fait partie de l’un de ces deux services, il s’agit déjà d’un compte professionnel. Ceci vous permet de vous inscrire auprès de Business Center avec votre mot de passe existant. Si votre organisation n’utilise pas de services cloud et que votre e-mail n’est pas du tout un compte professionnel, vous pouvez l’utiliser pour vous inscrire auprès de Business Center.

En outre, le [portail d’administration](https://manage.visualstudio.com/) des abonnements Visual Studio est l’emplacement où les abonnements sont attribués aux abonnés une fois que vous devenez administrateur des abonnements Visual Studio. Dans MPSA, les abonnements Visual Studio doivent être provisionnés dans leur portail de gestion respectif, qui est le portail d’administration des abonnements Visual Studio. Pour ce faire, vous devez associer votre compte d’achats à un locataire (autrement dit, contoso.onmicrosoft.com).

Notez qu’il existe deux types de locataires : les locataires gérés et les locataires non gérés. Un locataire géré fait référence à un locataire qui est déjà géré par des administrateurs au sein de l’organisation.

Un locataire non géré est un locataire auquel aucun administrateur n’est affecté et qui ne peut pas être utilisé pour des services en ligne comme Office 365. Des locataires non gérés sont également créés lors de l’inscription auprès de Business Center avec un e-mail qui n’est pas un compte professionnel. Si vous avez été invité à créer un mot de passe lors de l’inscription auprès de Business Center, cela signifie que votre e-mail n’était pas un compte professionnel et qu’il a créé un locataire non géré.

Voici quelques exigences/étapes nécessaires pour devenir administrateur des abonnements Visual Studio avant d’effectuer l’association du locataire.

## <a name="pre-tenant-association-managed-tenant"></a>Association prélocataire (locataire managé)
- Vous devez être un utilisateur inscrit auprès du portail Business Center.
- Vous devez être administrateur d’utilisateurs (au minimum) ou administrateur général au sein du locataire dont vous faites partie. (Cela s’applique si votre entreprise utilise déjà des services cloud). Chaque rôle est nécessaire pour être administrateur des abonnements Visual Studio.
- Vous devez être administrateur général dans le locataire dont vous faites partie pour être en mesure d’associer votre compte d’achats à un locataire.
- Vous devez être administrateur de compte ou gestionnaire de comptes dans Business Center.
- Le champ « Pays ou région » au sein de votre profil utilisateur (et tout autre utilisateur) dans [Azure](https://portal.azure.com/) doit être rempli de façon appropriée selon votre région (autrement dit, États-Unis, CA, etc.). 

> [!NOTE]
> Les utilisateurs dont vous voulez faire des administrateurs des abonnements Visual Studio ne sont pas nécessairement des utilisateurs dans Business Center, car ils doivent seulement répondre aux critères 2 et 5.

Une fois que vous répondez aux critères ci-dessus, vous pouvez procéder à l’association de votre compte d’achats à votre locataire en suivant les étapes ci-dessous.
1. Connectez-vous à [Business Center](https://businessaccount.microsoft.com/Customer).
2. Cliquez sur l’onglet **Compte** et sélectionnez **Associate Domains** (Associer les domaines).
3. Sélectionnez votre **compte d’achats** (si vous en avez plusieurs).
4. Sélectionnez votre **locataire** (autrement dit, contoso.onmicrosoft.com).
5. Cliquez sur **Associate Domain** (Associer le domaine).

Après l’association, tous les utilisateurs répondant aux critères vont généralement être provisionnés en tant qu’administrateurs des abonnements Visual Studio en quelques minutes. Toutefois, dans certains cas, cela peut prendre jusqu’à 24 heures. Une fois que votre locataire est provisionné, vous êtes en mesure d’accéder au portail d’administration des abonnements Visual Studio. Si cela prend plus de 24 heures, veuillez communiquer avec MPSA Support à l’aide de ces étapes :
1. Connectez-vous àhttps://www.microsoft.com/licensing/mpsa/default
2. Cliquez sur le menu **Plus** en haut de la page. 
3. Choisissez **l’aide**
4. Choisissez **l’aide aux licences**
5. Sélectionnez l’option de support qui répond le mieux à vos besoins. 

> [!NOTE]
> Si de nouveaux utilisateurs répondent aux critères des étapes 2 et 5 (après l’association), vous devez contacter le support MPSA. Le support MPSA vous prêtera assistance pour provisionner les nouveaux administrateurs des abonnements Visual Studio.

## <a name="tenant-association-unmanaged"></a>Association de locataire (non managé)
Si vous vous êtes inscrit auprès de Business Center avec un e-mail qui n’était pas un compte professionnel (non inscrit auprès d’Azure Active Directory « Azure AD »), comme expliqué ci-dessus, l’association du locataire est légèrement différente. Vous devez effectuer une opération appelée « prise de contrôle de domaine ». Pendant ce processus, vous deviendrez administrateur général pour transformer votre locataire non managé en locataire managé.

Pour obtenir une explication plus détaillée de ce processus, vous pouvez utiliser les [guides de démarrage rapide](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx). Téléchargez le guide nommé *« Setup and Use Your Online Services »* (Configurer et utiliser vos services en ligne) qui va vous guider lors de la prise de contrôle d’un domaine. Quand vous avez terminé, votre compte d’achats est également associé à votre locataire.

> [!NOTE]
> Quand vous avez terminé le processus de prise de contrôle de domaine, vous devez respecter les critères des cinq étapes de la section Association prélocataire (locataire managé). Une fois que les critères sont satisfaits, vous devez uniquement contacter le support MPSA pour provisionner d’autres administrateurs des abonnements Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Documentation Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentation Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentation Azure](https://docs.microsoft.com/azure/)
- [Documentation Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur la gestion des abonnements Visual Studio.
- [Attribuer des abonnements individuels](assign-license.md)
- [Attribuer plusieurs abonnements](assign-license-bulk.md)
- [Modifier des abonnements](edit-license.md)
- [Supprimer les abonnements](delete-license.md)
- [Déterminer l’utilisation maximale](maximum-usage.md)
