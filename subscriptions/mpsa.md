---
title: Abonnements Visual Studio dans un programme MPSA (Microsoft Products and Services Agreement) | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: Get-Started-Article
description: Abonnements Visual Studio dans un programme MPSA (Microsoft Products and Services Agreement)
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: a18565a97c0cd85ce42109961592a57c490d92a1
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
ms.locfileid: "30864269"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Abonnements Visual Studio dans un programme MPSA (Microsoft Products and Services Agreement)

Si vous avez acheté des abonnements Visual Studio via le programme MPSA, il existe quelques éléments à connaître avant de devenir administrateur des abonnements Visual Studio et d’attribuer des abonnements à vos utilisateurs. Si vous avez déjà été configuré comme administrateur, vous pouvez accéder directement au [portail d’administration](https://manage.visualstudio.com/) des abonnements Visual Studio. 

En tant que client MPSA, un portail vous est présenté, où vous pouvez gérer vos ressources achetées via MPSA. Ce nouveau portail est appelé [Business Center](https://businessaccount.microsoft.com/) et il prend en charge certaines des fonctionnalités identiques et nouvelles tout comme le Centre de gestion des licences en volume (VLSC, Volume Licensing Service Center). Celles-ci incluent l’affichage de votre récapitulatif des licences ainsi que des commandes, téléchargements, clés et utilisateurs, entre autres. Toutefois, les abonnements Visual Studio dans MPSA se comportent presque de la même manière que les services cloud. Le portail Business Center utilise également des comptes professionnels pour la connexion à la place des comptes Microsoft. Si votre organisation utilise des services cloud comme Office 365 ou Azure Active Directory et que votre compte e-mail fait partie de l’un de ces deux services, il s’agit déjà d’un compte professionnel. Cela vous permet de vous inscrire auprès du portail Business Center avec le mot de passe que votre organisation vous a affecté. Si votre organisation n’utilise pas de services cloud et que votre compte e-mail n’est pas du tout un compte professionnel, ne vous inquiétez pas, car vous pouvez l’utiliser pour vous inscrire auprès du portail Business Center.

En outre, le [portail d’administration](https://manage.visualstudio.com/) des abonnements Visual Studio est l’emplacement où les abonnements sont affectés aux abonnés une fois que vous devenez administrateur Visual Studio. Dans MPSA, les abonnements Visual Studio doivent être provisionnés dans leur portail de gestion respectif, qui est le portail d’administration des abonnements Visual Studio. Pour ce faire, vous devez associer votre compte d’achats à un locataire (autrement dit, contoso.onmicrosoft.com). 

Notez qu’il existe deux types de locataires (un locataire managé et un locataire non managé). Un locataire managé fait référence à un locataire qui est déjà géré par l’organisation avec des administrateurs internes. 

Un locataire non managé est un locataire sans aucun administrateur interne qui ne peut pas être utilisé pour des services en ligne comme Office 365. Des locataires non managés sont également créés lors de l’inscription auprès du portail Business Center avec un compte e-mail qui n’est pas un compte professionnel. Si vous avez été invité à créer un mot de passe lors de l’inscription auprès du portail Business Center, cela signifie que votre compte e-mail n’était pas un compte professionnel et a créé un locataire non managé.

Avant de terminer l’association du locataire, voici quelques exigences/étapes nécessaires pour devenir administrateur des abonnements Visual Studio.

## <a name="pre-tenant-association-managed-tenant"></a>Association prélocataire (locataire managé)
-   Vous devez être un utilisateur inscrit auprès du portail Business Center.
-   Vous devez être administrateur d’utilisateurs (au minimum) ou administrateur général au sein du locataire dont vous faites partie. (Cela s’applique si votre entreprise utilise déjà des services cloud). Chaque rôle est nécessaire pour être administrateur des abonnements Visual Studio.
-   Vous devez être administrateur général dans le locataire dont vous faites partie pour être en mesure d’associer votre compte d’achats à un locataire.
-   Vous devez être administrateur de compte ou gestionnaire de comptes dans Business Center.
-   Le champ « Pays ou région » au sein de votre profil utilisateur (et tout autre utilisateur) dans [Azure](https://portal.azure.com/) doit être rempli de façon appropriée selon votre région (autrement dit, États-Unis, CA, etc.). 

> [!NOTE]
> Les utilisateurs qui vont devenir administrateurs des abonnements Visual Studio ne sont pas nécessairement des utilisateurs de Business Center, car ils doivent uniquement répondre aux critères des étapes 2 et 5.

Une fois que vous répondez aux critères de l’étape 5 ci-dessus, vous pouvez continuer à associer votre compte d’achats à un locataire en suivant les étapes ci-dessous.
1.  Connectez-vous à [Business Center](https://businessaccount.microsoft.com/).
2.  Cliquez sur l’onglet **Compte** et sélectionnez **Associate Domains** (Associer les domaines).
3.  Sélectionnez votre **compte d’achats** (si vous en avez plusieurs).
4.  Sélectionnez votre **locataire** (autrement dit, contoso.onmicrosoft.com).
5.  Cliquez sur **Associate Domain** (Associer le domaine).

Lors de l’association, tous les utilisateurs répondant aux critères requis sont généralement provisionnés en tant qu’administrateurs des abonnements Visual Studio en quelques minutes. Toutefois, dans certains cas, cela peut prendre jusqu’à 24 heures. Une fois provisionné, vous êtes en mesure d’accéder au portail d’administration des abonnements Visual Studio. Si cette opération dure plus de 24 heures, contactez le support MPSA.

> [!NOTE]
> Si de nouveaux utilisateurs répondent aux critères des étapes 2 et 5 (après l’association), vous devez contacter le support MPSA. Le support MPSA vous prêtera assistance pour provisionner les nouveaux administrateurs des abonnements Visual Studio.

## <a name="tenant-association-unmanaged"></a>Association de locataire (non managé)

Si vous vous êtes inscrit auprès du portail Business Center avec un compte e-mail qui n’était pas un compte professionnel (non inscrit auprès d’Azure Active Directory « Azure AD »), comme expliqué au paragraphe cinq ci-dessus, l’association du locataire est légèrement différente. Vous devez effectuer une opération appelée « prise de contrôle de domaine ». Pendant ce processus, vous deviendrez administrateur général pour transformer votre locataire non managé en locataire managé.

Pour obtenir une explication plus détaillée de ce processus, vous pouvez utiliser les [guides de démarrage rapide](https://www.microsoft.com/en-us/Licensing/existing-customer/business-center-training-and-resources.aspx). Téléchargez le guide nommé *« Setup and Use Your Online Services »* (Configurer et utiliser vos services en ligne) qui va vous guider lors de la prise de contrôle d’un domaine. Quand vous avez terminé, votre compte d’achats est également associé à votre locataire.

> [!NOTE]
> Quand vous avez terminé le processus de prise de contrôle de domaine, vous devez respecter les critères des cinq étapes de la section Association prélocataire (locataire managé). Une fois que les critères sont satisfaits, vous devez uniquement contacter le support MPSA pour provisionner d’autres administrateurs des abonnements Visual Studio.

Si vous avez des questions ou besoin d’aide, vous pouvez contacter le support par téléphone ou e-mail.

Support MPSA : **1-866-200-9611**, disponible du lundi au vendredi de 05:30 à 17:30 Pacifique

Adresse e-mail : ngvlsup@microsoft.com
