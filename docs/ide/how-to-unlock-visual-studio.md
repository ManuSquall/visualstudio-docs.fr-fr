---
title: Prolonger une version d’évaluation ou mettre à jour une licence
description: Découvrez comment étendre une version d’évaluation gratuite de Visual Studio, utiliser un abonnement en ligne ou une clé de produit pour déverrouiller Visual Studio, et mettre à jour une licence périmée ou expirée.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 3dd2a688ef70064f44caccfd7c64150b7c649769
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869126"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Prolonger une version d’évaluation ou mettre à jour une licence

Vous pouvez évaluer une version d’évaluation gratuite de [Visual Studio Professional ou Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) pendant 30 jours. Et si vous vous connectez, vous pouvez étendre la période d’évaluation à 90 jours. (Visual Studio Community est gratuit sans période d’essai. Toutefois, vous devez vous [connecter](signing-in-to-visual-studio.md) régulièrement pour maintenir votre [licence à jour](#update-a-stale-license).)

Pour continuer à utiliser Visual Studio après la fin d’une période d’évaluation, déverrouillez-le avec un [abonnement en ligne](#use-an-online-subscription) ou une [clé de produit](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Utiliser un abonnement en ligne

1. Choisissez le bouton **se connecter** dans l’angle supérieur droit de l’IDE (ou accédez à   >  **paramètres du compte** de fichier pour ouvrir la boîte de dialogue **paramètres du compte** , puis choisissez le bouton **se connecter** ).

1. Entrez les informations d'identification d'un compte Microsoft ou d'un compte professionnel ou scolaire. Visual Studio recherche un abonnement Visual Studio ou une organisation Azure DevOps associé à votre compte.

> [!IMPORTANT]
> Visual Studio recherche automatiquement les abonnements en ligne associés quand vous vous connectez à une organisation Azure DevOps dans la fenêtre Outil **Team Explorer**. Vous pouvez alors utiliser un compte Microsoft ou un compte professionnel ou scolaire. Si un abonnement en ligne existe pour ce compte d'utilisateur, Visual Studio déverrouille automatiquement l'IDE.

Pour plus d’informations sur les abonnements Visual Studio et leur fonctionnement, consultez la page [Forum aux questions sur la prise en charge des abonnements](https://visualstudio.microsoft.com/subscriptions/support/) .

## <a name="enter-a-product-key"></a>Entrer une clé de produit

1. Sélectionnez **fichier**  >  **paramètres du compte** pour ouvrir la boîte de dialogue **paramètres du compte** , puis choisissez le lien **licence avec une clé de produit** .

1. Entrez la clé de produit dans la zone fournie.

> [!TIP]
> Les préversions de Visual Studio n’ont pas de clés de produit. Vous devez vous connecter à l’IDE pour utiliser les préversions.

Pour plus d’informations sur les clés de produit Visual Studio pour Visual Studio et sur la façon de les obtenir, consultez la page [utilisation des clés de produit dans les abonnements Visual Studio](/visualstudio/subscriptions/product-keys) .

## <a name="update-a-stale-license"></a>Mettre à jour une licence obsolète

Dans Visual Studio, vous pouvez voir un message indiquant que la licence est obsolète et doit être mise à jour.

![Message d’expiration de licence Visual Studio](../ide/media/vs2017_stale-license.png)

Ce message indique que si votre abonnement est toujours valide, le jeton de licence que Visual Studio utilise pour maintenir votre abonnement à jour n’a pas été actualisé. Visual Studio signale que la licence est périmée pour l’une des raisons suivantes :

* Vous n’avez pas utilisé Visual Studio ou vous n’êtes pas connecté à Internet pendant une période prolongée.
* Vous vous êtes déconnecté de Visual Studio.

Avant que le jeton de licence ne soit périmé, Visual Studio affiche un message d’avertissement qui vous demande d’entrer une nouvelle fois vos informations d’identification.

Si vous n’entrez pas à nouveau vos informations d’identification, le jeton commence à devenir obsolète et la boîte de dialogue **paramètres du compte** vous indique le nombre de jours restants avant l’expiration du jeton. Une fois votre jeton expiré, vous devez réentrer les informations d’identification de votre compte avant de pouvoir continuer à utiliser Visual Studio.

> [!Important]
> Si vous utilisez Visual Studio pendant de longues périodes dans des environnements ayant un accès limité ou nul à Internet, vous devez utiliser une clé de produit pour déverrouiller Visual Studio afin d’éviter toute interruption.

## <a name="update-an-expired-license"></a>Mettre à jour une licence expirée

Si votre abonnement a expiré et que vous n’avez plus de droits d’accès à Visual Studio, vous devez renouveler votre abonnement ou ajouter un autre compte disposant d’un abonnement. Pour plus d’informations sur la licence que vous utilisez, accédez à   >  **paramètres du compte** de fichier et consultez les informations de licence sur le côté droit de la boîte de dialogue. Si vous avez un autre abonnement associé à un autre compte, ajoutez ce compte à la liste **tous les comptes** sur le côté gauche de la boîte de dialogue en sélectionnant le lien **Ajouter un compte** .

## <a name="get-support"></a>Obtenir un support

Parfois, des problèmes surgissent. Si vous rencontrez un problème, voici quelques options de support :

* Signalez les problèmes liés au produit à l’aide de l’outil [signaler un problème](how-to-report-a-problem-with-visual-studio.md) .
* Trouvez des réponses aux questions sur les abonnements, les comptes et la facturation dans le [Forum aux questions sur la prise en charge des abonnements](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Voir aussi

* [Se connecter à Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Comparer les éditions de Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [En savoir plus sur les abonnements Visual Studio](/visualstudio/subscriptions/)
