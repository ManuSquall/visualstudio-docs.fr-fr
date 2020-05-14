---
title: Prolonger une version d’évaluation ou mettre à jour une licence
description: Découvrez comment prolonger un essai gratuit de Visual Studio, utilisez un abonnement en ligne ou une clé de produit pour débloquer Visual Studio, et mettez à jour une licence périmée ou expirée.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027580"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Prolonger une version d’évaluation ou mettre à jour une licence

Vous pouvez évaluer un essai gratuit de [Visual Studio Professional ou Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) pendant 30 jours. Et si vous vous connectez, vous pouvez prolonger la période d’essai à 90 jours. (Visual Studio Community est gratuit sans période d’essai. Cependant, vous devez [vous connecter](signing-in-to-visual-studio.md) périodiquement pour maintenir votre licence [à jour](#update-a-stale-license).)

Pour continuer à utiliser Visual Studio après la fin d’une période d’essai, déverrouiller avec un [abonnement en ligne](#use-an-online-subscription) ou une clé de [produit](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Utiliser un abonnement en ligne

1. Choisissez le bouton **Signe dans** le coin supérieur droit de l’IDE (ou accédez aux paramètres **de** > **compte** de fichier pour ouvrir le dialogue **paramètres de compte,** puis choisissez le bouton **Signe).**

1. Entrez les informations d'identification d'un compte Microsoft ou d'un compte professionnel ou scolaire. Visual Studio recherche un abonnement Visual Studio ou une organisation Azure DevOps associé à votre compte.

> [!IMPORTANT]
> Visual Studio recherche automatiquement les abonnements en ligne associés quand vous vous connectez à une organisation Azure DevOps dans la fenêtre Outil **Team Explorer**. Vous pouvez alors utiliser un compte Microsoft ou un compte professionnel ou scolaire. Si un abonnement en ligne existe pour ce compte d'utilisateur, Visual Studio déverrouille automatiquement l'IDE.

Pour plus d’informations sur les abonnements Visual Studio et leur fonctionnement, consultez la page [FaQ de Support Abonnements.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="enter-a-product-key"></a>Entrer une clé de produit

1. Sélectionnez **paramètres de** > **compte** de fichier pour ouvrir le dialogue **paramètres de compte,** puis choisissez la licence avec un lien **de clé de produit.**

1. Entrez la clé de produit dans la zone fournie.

> [!TIP]
> Les préversions de Visual Studio n’ont pas de clés de produit. Vous devez vous connecter à l’IDE pour utiliser les préversions.

Pour plus d’informations sur les clés de produits Visual Studio pour Visual Studio et comment les obtenir, consultez la page [d’abonnements Using product dans Visual Studio.](/visualstudio/subscriptions/product-keys)

## <a name="update-a-stale-license"></a>Mettre à jour une licence périmée

Vous pouvez voir un message dans Visual Studio qui dit: «Votre licence est devenue obsolète et doit être mis à jour."

![Message d’expiration de licence Visual Studio](../ide/media/vs2017_stale-license.png)

Ce message indique que même si votre abonnement peut encore être valide, le jeton de licence que Visual Studio utilise pour maintenir votre abonnement à jour n’a pas été actualisé. Visual Studio rapporte que la licence est périmée en raison de l’une des raisons suivantes:

* Vous n’avez pas utilisé Visual Studio ou vous n’avez pas connecté à Internet pendant une longue période de temps.
* Vous vous êtes déconnecté de Visual Studio.

Avant que le jeton de licence ne soit périmé, Visual Studio affiche un message d’avertissement qui vous demande d’entrer une nouvelle fois vos informations d’identification.

Si vous n’entrez pas vos informations d’identification, le jeton commence à périmé et le dialogue sur les **paramètres de compte** vous indique combien de jours vous avez laissés avant l’expiration de votre jeton. Une fois votre jeton expiré, vous devez réentrer les informations d’identification de votre compte avant de pouvoir continuer à utiliser Visual Studio.

> [!Important]
> Si vous utilisez Visual Studio pendant de longues périodes dans des environnements ayant un accès limité ou nul à Internet, vous devez utiliser une clé de produit pour déverrouiller Visual Studio afin d’éviter toute interruption.

## <a name="update-an-expired-license"></a>Mettre à jour une licence expirée

Si votre abonnement a expiré et que vous n’avez plus de droits d’accès à Visual Studio, vous devez renouveler votre abonnement ou ajouter un autre compte qui a un abonnement. Pour voir plus d’informations sur la licence que vous utilisez, rendez-vous sur Paramètres**de compte** **de fichier** > et regardez les informations de licence sur le côté droit du dialogue. Si vous avez un autre abonnement associé à un compte différent, ajoutez ce compte à la liste **Tous les comptes** sur le côté gauche de la boîte de dialogue en sélectionnant le lien Ajouter **un** compte.

## <a name="get-support"></a>Obtenir de l’aide

Parfois, des problèmes surgissent. Si vous rencontrez un problème, voici quelques options de soutien :

* Signalez les problèmes de produits en utilisant l’outil [Rapport un problème.](how-to-report-a-problem-with-visual-studio.md)
* Trouvez des réponses aux questions sur les abonnements, les comptes et la facturation dans la [FAQ de support d’abonnements.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="see-also"></a>Voir aussi

* [Connexion à Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Comparez les éditions Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [En savoir plus sur les abonnements Visual Studio](/visualstudio/subscriptions/)
