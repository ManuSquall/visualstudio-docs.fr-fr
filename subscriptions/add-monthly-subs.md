---
title: Ajouter de nouveaux abonnements mensuels au portail d’administration des abonnements | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 09/03/2020
ms.topic: how-to
description: Découvrez comment vous venez d’acheter des abonnements Visual Studio mensuels au portail d’administration des abonnements.
ms.openlocfilehash: f6b835969fff3a8316a2b46c6e15217ebe3e33b1
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467594"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Ajouter de nouveaux abonnements Visual Studio mensuels au portail d’administration des abonnements
Lorsque vous achetez de nouveaux abonnements Visual Studio mensuels à l’aide d’un abonnement Azure, vous devrez peut-être les ajouter au portail d’administration des abonnements pour pouvoir les affecter aux utilisateurs.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Comment faire savoir si j’ai besoin d’ajouter mes abonnements ?
Les étapes à suivre pour ajouter des abonnements mensuels dépendent des types d’abonnements que votre organisation possède déjà, et si vous êtes un nouvel administrateur.
- Si vous êtes un nouvel administrateur, nous allons vérifier les abonnements Azure pour lesquels vous disposez de droits d’administrateur d’accès utilisateur lorsque vous vous connectez au portail d’administration des abonnements la première fois.  Si nous trouvons des abonnements mensuels pour vous, nous les ajouterons automatiquement. 
- Si vous avez déjà ajouté ou administré des abonnements mensuels, nous vérifions les nouveaux abonnements mensuels à chaque fois que vous vous connectez. 
- Si vous êtes déjà un administrateur des abonnements acquis via le programme de licence en volume, mais que vous n’avez pas encore ajouté ou géré des abonnements mensuels, vous devez les ajouter à l’aide de la procédure indiquée ci-dessous.

## <a name="how-to-add-monthly-subscriptions"></a>Comment ajouter des abonnements mensuels
1. Connectez-vous au portail d’administration des abonnements à l’adresse <https://manage.visualstudio.com>
1. Dans l’onglet **gérer les abonnés** , choisissez la liste déroulante Ajouter un **accord** . 
1. Choisir les **nouveaux abonnements mensuels** dans la liste déroulante
   > [!div class="mx-imgBorder"]
   > ![Liste déroulante Ajouter de nouveaux abonnements mensuels](_img/add-monthly-subs/add-subs-drop-down.png "Choisissez « Ajouter un contrat », puis « nouveaux abonnements mensuels ».")
1. Le système recherche tous les abonnements Azure pour lesquels vous disposez de droits d’administrateur d’accès utilisateur, et importe tous les abonnements Visual Studio achetés avec ces abonnements Azure.
1. Si aucun abonnement Azure sur lequel vous disposez des droits d’administrateur d’accès utilisateur n’est trouvé ou si des abonnements Azure éligibles sont détectés, mais qu’aucun abonnement Visual Studio n’est trouvé, vous recevrez le message suivant :
   > [!div class="mx-imgBorder"]
   > ![Aucun nouvel abonnement mensuel trouvé](_img/add-monthly-subs/no-subs-found.png "Message d’erreur indiquant qu’il n’y a pas d’abonnement Azure ou d’abonnements Visual Studio à votre disposition.")
1. Si de nouveaux abonnements mensuels sont trouvés, vous recevrez un message de confirmation
   > [!div class="mx-imgBorder"]
   > ![Message de confirmation de l’ajout d’abonnements](_img/add-monthly-subs/subs-added-confirmation.png "Un message de confirmation affiche les abonnements que vous avez ajoutés.")

## <a name="things-to-keep-in-mind"></a>Points à prendre en compte
- L’option permettant d’ajouter de nouveaux abonnements mensuels sera disponible la première fois que vous les achetez.  Une fois que vous avez ajouté des abonnements mensuels, nous vérifions les nouveaux abonnements à chaque fois que vous vous connectez au portail. 
- Lorsque de nouveaux abonnements sont trouvés, vous pouvez voir qu’ils sont déjà affectés aux abonnés.  Cela est dû au fait que d’autres administrateurs ont accès à l’abonnement Azure et qu’ils ont déjà attribué les nouveaux abonnements Visual Studio aux utilisateurs.  Maintenant que vous les avez également ajoutés à votre portail, vous pouvez administrer ces abonnements. 

## <a name="next-steps"></a>Étapes suivantes
Maintenant que vous avez ajouté des abonnements, vous êtes prêt à les affecter aux utilisateurs.  Vous pouvez le faire de plusieurs façons :
- [Affecter des abonnements individuellement](assign-license.md)
- [Attribuer des abonnements à plusieurs utilisateurs](assign-license-bulk.md)
- [Affecter des abonnements spécifiques à des utilisateurs spécifiques](assign-guid.md)

## <a name="see-also"></a>Voir aussi
- [Documentation de Visual Studio](/visualstudio/)
- [Documentation Azure DevOps](/azure/devops/)
- [Documentation Azure](/azure/)
- [Documentation Microsoft 365](/microsoft-365/)